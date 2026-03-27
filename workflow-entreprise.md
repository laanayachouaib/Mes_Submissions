# Workflow Entreprise - Challenge C12

## Objectif
Simuler un workflow réaliste d'entreprise avec deux fonctionnalités développées en parallèle.

## Date
$(date)

## Branches créées

### feature/a
Créée depuis \`main\` pour ajouter la fonctionnalité de contact.
- **Commits** : 2 commits
  - \`feat(contact): ajouter page de contact avec coordonnées\`
  - \`feat(contact): ajouter formulaire de contact structure\`
- **Fichiers** : \`contact.md\`

### feature/b
Créée depuis \`main\` pour ajouter la FAQ.
- **Commits** : 2 commits
  - \`feat(faq): ajouter page FAQ avec questions générales\`
  - \`docs(faq): ajouter questions avancées et bonnes pratiques\`
- **Fichiers** : \`faq.md\`

## Ordre de fusion
1. **feature/a** → main (premier merge)
2. **feature/b** → main (deuxième merge)

## Historique des commits

\`\`\`
$(git log --graph --oneline -15)
\`\`\`

## Fichiers présents sur main après fusion

\`\`\`
$(git ls-files | grep -E "contact.md|faq.md")
\`\`\`

## Diagramme du workflow

\`\`\`
main:     A---B---C---D---E (main avant features)
              \\
feature/a:     F---G (2 commits)
                  \\
main après 1er merge:  ---M1 (merge feature/a)
                        \\
feature/b:               H---I (2 commits)
                            \\
main final:               ---M2 (merge feature/b)
\`\`\`

## Bonnes pratiques du workflow entreprise

### 1. Branches feature
- Une branche = une fonctionnalité
- Noms descriptifs : \`feature/nom-fonctionnalite\`
- Commits fréquents et atomiques

### 2. Ordre de fusion
- Fusionner les features par ordre de priorité
- Vérifier l'absence de conflits après chaque merge

### 3. Main stable
- La branche \`main\` doit toujours être fonctionnelle
- Tester après chaque fusion

### 4. Revue de code
- Idéalement, utiliser des Pull Requests
- Faire relire avant fusion

## Commandes utilisées

\`\`\`bash
# Création des branches
git checkout -b feature/a
git checkout -b feature/b

# Fusions
git checkout main
git merge feature/a
git merge feature/b

# Vérifications
git log --graph --oneline --all
git diff main feature/a
\`\`\`

## Nettoyage (optionnel)
Après fusion, on peut supprimer les branches :

\`\`\`bash
git branch -d feature/a
git branch -d feature/b
\`\`\`

---
*Document créé dans le cadre du challenge C12 - Workflow entreprise*
*Date: $(date)*