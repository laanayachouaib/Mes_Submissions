# FAQ - Foire Aux Questions

## Généralités

### Qu'est-ce que ce projet ?
Ce projet est un exercice d'apprentissage de Git simulant un workflow d'entreprise.

### Qui peut utiliser ce projet ?
Toute personne souhaitant apprendre Git et ses bonnes pratiques.

## Technique

### Quels sont les prérequis ?
- Git installé
- Un éditeur de code (VS Code recommandé)
- Connaissances de base en ligne de commande

### Comment contribuer ?
1. Fork le projet
2. Créer une branche feature
3. Faire vos modifications
4. Soumettre une Pull Request

## Support

### Où trouver de l'aide ?
- Consulter la documentation dans le dossier \`docs/\`
- Ouvrir une issue sur GitHub
- Contacter l'équipe via les canaux de communication

## Questions avancées

### Comment gérer les conflits Git ?
Utilisez \`git status\` pour identifier les conflits, puis résolvez-les manuellement dans les fichiers concernés.

### Quelle est la différence entre merge et rebase ?
- **merge** : Crée un commit de fusion, garde l'historique complet
- **rebase** : Réécrit l'historique, donne une ligne plus propre

### Comment revenir en arrière après un mauvais commit ?
- \`git reset --soft HEAD~1\` : Annule le commit mais garde les modifications
- \`git reset --hard HEAD~1\` : Annule complètement le commit
- \`git revert <hash>\` : Crée un nouveau commit qui annule les changements

## Bonnes pratiques

### Convention de commits
Utiliser le format : \`type(scope): description\`

Types courants :
- **feat** : Nouvelle fonctionnalité
- **fix** : Correction de bug
- **docs** : Documentation
- **style** : Formatage
- **refactor** : Refactorisation
- **test** : Tests
- **chore** : Maintenance