# Résolution de conflit Git - Challenge C11

## Objectif
Créer et résoudre volontairement un conflit de fusion entre deux branches.

## Date
$(date)

## Scénario créé

### Branches créées
1. **feature/conflit-1** : Modification de la ligne 1 de a.txt
2. **feature/conflit-2** : Modification de la MÊME ligne 1 de a.txt

### Processus
\`\`\`bash
# Création des branches
git checkout -b feature/conflit-1
# Modifier a.txt sur conflit-1
echo \"Version 1\" > a.txt
git add a.txt && git commit -m \"modif 1\"

git checkout main
git checkout -b feature/conflit-2
# Modifier la MÊME ligne sur conflit-2
echo \"Version 2\" > a.txt
git add a.txt && git commit -m \"modif 2\"

# Fusion
git checkout main
git merge feature/conflit-1  # OK
git merge feature/conflit-2  # CONFLIT !
\`\`\`

## Le conflit

### Fichier en conflit : a.txt

\`\`\`
<<<<<<< HEAD
LIGNE MODIFIEE PAR BRANCHE 1 - Cette ligne va créer un conflit
=======
LIGNE MODIFIEE PAR BRANCHE 2 - Version complètement différente
>>>>>>> feature/conflit-2
Deuxième ligne inchangée
Troisième ligne
\`\`\`

### Cause du conflit
Les deux branches ont modifié la même ligne du même fichier, et Git ne sait pas automatiquement quelle version conserver.

## Résolution

### Fichier résolu : a.txt
\`\`\`
LIGNE RESOLUE - Fusion des deux branches
Version 1: \"LIGNE MODIFIEE PAR BRANCHE 1\"
Version 2: \"LIGNE MODIFIEE PAR BRANCHE 2\"
Résolution: Les deux versions ont été combinées pour la démonstration
Deuxième ligne inchangée
Troisième ligne
\`\`\`

### Étapes de résolution
1. Identifier les fichiers en conflit avec \`git status\`
2. Ouvrir le fichier et analyser les marqueurs (\`<<<<<<<\`, \`=======\`, \`>>>>>>>\`)
3. Décider du contenu final (garder l'une des versions, combiner, ou créer une nouvelle version)
4. Supprimer les marqueurs de conflit
5. Ajouter le fichier résolu : \`git add <fichier>\`
6. Committer la résolution : \`git commit\`

## Commandes utiles pour les conflits

| Commande | Description |
|----------|-------------|
| \`git status\` | Voir les fichiers en conflit |
| \`git diff\` | Voir les différences conflictuelles |
| \`git diff --base\` | Voir la version commune |
| \`git mergetool\` | Utiliser un outil graphique de résolution |
| \`git checkout --ours <fichier>\` | Garder la version de la branche courante |
| \`git checkout --theirs <fichier>\` | Garder la version de la branche fusionnée |
| \`git merge --abort\` | Annuler la fusion en cours |

## Outils de résolution graphique

### VS Code
VS Code détecte automatiquement les conflits et propose :
- **Accept Current Change** (--ours)
- **Accept Incoming Change** (--theirs)
- **Accept Both Changes** (combiner)
- **Compare Changes** (comparer)

### Autres outils
- \`git mergetool\` (lance l'outil configuré)
- **Kdiff3**, **Meld**, **Beyond Compare**

## Bonnes pratiques

### Pour éviter les conflits
1. **Pull régulièrement** : \`git pull origin main\` avant de commencer
2. **Petits commits** : Des modifications atomiques et fréquentes
3. **Communication** : Informer l'équipe des modifications majeures
4. **Branches courtes** : Ne pas laisser les branches vivre trop longtemps

### Pour résoudre les conflits
1. **Prendre son temps** : Comprendre les deux versions
2. **Tester** : Vérifier que le code fonctionne après résolution
3. **Message clair** : Expliquer comment le conflit a été résolu
4. **Revue** : Faire relire la résolution si possible

## Vérification finale

\`\`\`bash
# Voir l'historique avec le commit de résolution
git log --graph --oneline -10

# Voir le contenu résolu
cat a.txt

# Voir les branches
git branch -a
\`\`\`

## Nettoyage (optionnel)

\`\`\`bash
# Supprimer les branches temporaires
git branch -d feature/conflit-1
git branch -d feature/conflit-2
\`\`\`

---
*Document créé dans le cadre du challenge C11 - Conflict Git*
*Date: $(date)*