# Documentation du Merge - Challenge C10

## Opération réalisée
Fusion de la branche \`feature/about\` vers \`main\`.

## Date du merge
$(date)

## Branches impliquées
- **Branche source** : feature/about
- **Branche cible** : main

## Commande utilisée
\`\`\`bash
git checkout main
git merge feature/about
\`\`\`

## Type de merge
$(git log --oneline -1 | grep -q "Merge branch" && echo "Merge commit créé" || echo "Fast-forward merge")

## Fichiers fusionnés
\`\`\`
$(git diff --name-status HEAD~1 HEAD 2>/dev/null || git diff --name-status ORIG_HEAD HEAD)
\`\`\`

## Vérifications post-merge

### Fichiers présents sur main
\`\`\`bash
git ls-files | grep -E "about.md|branches.md"
\`\`\`

### Historique des commits
\`\`\`
$(git log --graph --oneline -8)
\`\`\`

## Différence entre Fast-forward et Merge commit

| Type | Description | Avantages | Inconvénients |
|------|-------------|-----------|---------------|
| **Fast-forward** | Le pointeur main avance simplement | Historique linéaire, plus propre | Ne garde pas la trace de la branche |
| **Merge commit** | Crée un commit de fusion | Garde l'historique des branches | Historique plus complexe |

## Pour contrôler le type de merge

\`\`\`bash
# Forcer un merge commit (même si fast-forward possible)
git merge --no-ff feature/about

# Forcer un fast-forward (si possible)
git merge --ff-only feature/about
\`\`\`

## Nettoyage (optionnel)
Après fusion, on peut supprimer la branche :

\`\`\`bash
# Supprimer la branche locale
git branch -d feature/about

# Vérifier que la branche est supprimée
git branch
\`\`\`

---
*Document créé dans le cadre du challenge C10 - Merge simple vers main*
*Date: $(date)*