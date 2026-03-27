# Git Stash - Challenge C13

## Objectif
Utiliser git stash pour sauvegarder temporairement du travail non terminé.

## Date
$(date)

## Scénario réalisé

### 1. Situation initiale
- Branche : \`feature/stash-demo\`
- Modification non commitée sur \`journal.txt\`

### 2. Stash du travail
\`\`\`bash
git stash push -m "WIP: Travail en cours sur journal.txt - fonctionnalité à terminer"
\`\`\`

### 3. Changement de contexte
\`\`\`bash
git checkout main
git checkout -b feature/autre-travail
# Travail sur une autre branche
\`\`\`

### 4. Retour et réapplication
\`\`\`bash
git checkout feature/stash-demo
git stash pop  # Réapplique et supprime le stash
\`\`\`

### 5. Commit final
\`\`\`bash
git add journal.txt
git commit -m "feat: finaliser le travail récupéré du stash"
\`\`\`

## Commandes Git Stash

| Commande | Description |
|----------|-------------|
| \`git stash\` | Sauvegarde les modifications non commitées |
| \`git stash push -m \"message\"\` | Stash avec un message descriptif |
| \`git stash list\` | Liste tous les stashes |
| \`git stash show\` | Affiche le contenu du dernier stash |
| \`git stash show -p\` | Affiche les différences complètes |
| \`git stash apply\` | Réapplique le dernier stash (le garde) |
| \`git stash pop\` | Réapplique et supprime le dernier stash |
| \`git stash drop\` | Supprime le dernier stash |
| \`git stash clear\` | Supprime tous les stashes |
| \`git stash branch <nom>\` | Crée une branche à partir d'un stash |

## Utilisations courantes

### Stash avec des fichiers non suivis
\`\`\`bash
# Inclure les fichiers non suivis
git stash -u

# Inclure tout (y compris les fichiers ignorés)
git stash -a
\`\`\`

### Stash spécifique
\`\`\`bash
# Stasher seulement certains fichiers
git stash push -m \"message\" -- fichier1.txt fichier2.txt
\`\`\`

### Appliquer un stash spécifique
\`\`\`bash
# Appliquer un stash autre que le dernier
git stash apply stash@{2}
\`\`\`

## Cas d'usage

### 1. Changement de branche urgent
Quand vous devez changer de branche mais que vous n'avez pas fini votre travail.

### 2. Pull avant push
Pour récupérer les dernières modifications sans perdre votre travail en cours.

### 3. Tester une idée rapidement
Pour sauvegarder votre travail et expérimenter temporairement.

### 4. Nettoyer le working directory
Pour avoir un état propre sans perdre vos modifications.

## Bonnes pratiques

1. **Messages clairs** : Toujours utiliser \`-m\` avec un message descriptif
2. **Stashes temporaires** : Ne pas laisser traîner des stashes trop longtemps
3. **Nettoyer régulièrement** : Supprimer les stashes inutilisés
4. **Vérifier avant pop** : Utiliser \`git stash show\` avant \`pop\` pour éviter les surprises

## Vérification finale

\`\`\`bash
# Voir l'historique des stashes
git stash list

# Voir les commits
git log --oneline -5

# Voir l'état actuel
git status
\`\`\`

## Nettoyage (optionnel)

\`\`\`bash
# Supprimer les stashes restants
git stash clear

# Supprimer la branche de démonstration
git checkout main
git branch -d feature/stash-demo
git branch -d feature/autre-travail 2>/dev/null || echo "Branche déjà supprimée"
\`\`\`

---
*Document créé dans le cadre du challenge C13 - git stash*
*Date: $(date)*