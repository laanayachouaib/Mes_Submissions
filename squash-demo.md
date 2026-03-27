# Git Squash - Challenge C14

## Objectif
Nettoyer l'historique en combinant plusieurs commits en un seul avant fusion.

## Date
$(date)

## Scénario réalisé

### 1. Création d'une branche avec 3 commits
\`\`\`bash
git checkout -b feature/squash-demo
# Commit 1: ajouter structure de documentation technique
# Commit 2: ajouter spécifications fonctionnelles
# Commit 3: ajouter conventions et bonnes pratiques
\`\`\`

### 2. Vérification des commits
\`\`\`bash
git log main..feature/squash-demo --oneline
# Affiche 3 commits
\`\`\`

### 3. Squash merge
\`\`\`bash
git checkout main
git merge --squash feature/squash-demo
\`\`\`

### 4. Commit final
\`\`\`bash
git commit -m \"feat: ajouter documentation technique complète\"
\`\`\`

## Commandes Squash

| Commande | Description |
|----------|-------------|
| \`git merge --squash <branche>\` | Fusionne en un seul commit (sans commit) |
| \`git rebase -i HEAD~n\` | Squash interactif de n commits |
| \`git commit --amend\` | Ajouter des changements au dernier commit |

## Types de Squash

### 1. Squash via merge (recommandé pour les branches)
\`\`\`bash
git checkout main
git merge --squash feature/branche
git commit -m \"feat: description unifiée\"
\`\`\`

### 2. Squash via rebase interactif
\`\`\`bash
git checkout feature/branche
git rebase -i HEAD~3
# Remplacer 'pick' par 'squash' pour les commits à combiner
\`\`\`

### 3. Squash après plusieurs commits
\`\`\`bash
# Réinitialiser soft (garder les modifs)
git reset --soft HEAD~3
git commit -m \"feat: nouveau commit combiné\"
\`\`\`

## Comparaison des méthodes

| Méthode | Avantages | Inconvénients |
|---------|-----------|---------------|
| \`merge --squash\` | Simple, garde l'historique propre | Perd l'historique détaillé de la branche |
| \`rebase -i\` | Contrôle précis | Plus complexe, réécrit l'historique |
| \`reset --soft\` | Rapide pour les derniers commits | Risque de confusion |

## Visualisation

### Avant squash
\`\`\`
main:     A---B---C
              \\
feature:      D---E---F (3 commits)
\`\`\`

### Après merge --squash
\`\`\`
main:     A---B---C---S (1 commit combiné)
\`\`\`

### Historique de la branche
\`\`\`
$(git log feature/squash-demo --oneline -3 2>/dev/null || echo "Branche supprimée")
\`\`\`

### Historique de main
\`\`\`
$(git log main --oneline -5)
\`\`\`

## Quand utiliser squash

### ✅ À faire
- Pour une fonctionnalité qui aurait dû être un seul commit
- Pour nettoyer des commits de type "WIP" ou "fix"
- Avant de fusionner dans main pour garder l'historique lisible
- Pour les corrections mineures post-review

### ❌ À éviter
- Si l'historique détaillé est important pour le débogage
- Si les commits sont logiquement indépendants
- Sur des branches déjà partagées
- Sans avoir testé après squash

## Bonnes pratiques

1. **Message clair** : Le commit squashé doit avoir une description complète
2. **Tester après squash** : Vérifier que tout fonctionne avant de pousser
3. **Documenter** : Mentionner dans le message que c'est un squash
4. **Nettoyer** : Supprimer la branche après merge

## Nettoyage

\`\`\`bash
# Supprimer la branche de démonstration
git branch -d feature/squash-demo
\`\`\`

---
*Document créé dans le cadre du challenge C14 - Squash*
*Date: $(date)*