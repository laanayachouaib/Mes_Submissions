# Gestion des branches Git

## Historique des branches

### Branche main
Branche principale contenant la base du projet.

### Branche feature/about
Créée pour le challenge C09.

**Commande de création** :
\`\`\`bash
git checkout -b feature/about
\`\`\`

**Modifications apportées** :
1. Création de \`about.md\`
2. Mise à jour de \`README.md\`

**Commit** :
\`\`\`bash
feat: ajouter page about.md et documentation des branches
\`\`\`

## Visualisation des branches
\`\`\`bash
git log --graph --oneline --all
\`\`\`

## Commandes clés

| Commande | Description |
|----------|-------------|
| \`git branch\` | Lister les branches |
| \`git branch <nom>\` | Créer une branche |
| \`git checkout <branche>\` | Basculer sur une branche |
| \`git checkout -b <branche>\` | Créer et basculer |
| \`git switch <branche>\` | Basculer (alternative moderne) |
| \`git switch -c <branche>\` | Créer et basculer |
| \`git merge <branche>\` | Fusionner une branche |
| \`git branch -d <branche>\` | Supprimer une branche |

## Bonnes pratiques des branches

1. **Noms explicites** : \`feature/nom-fonctionnalité\`, \`bugfix/description\`, \`hotfix/critique\`
2. **Isolation** : Une branche = une fonctionnalité ou un correctif
3. **Commits fréquents** : Des petits commits sur la branche
4. **Nettoyage** : Supprimer les branches après fusion

---
*Document créé dans le cadre du challenge C09*
*Date: $(date)*