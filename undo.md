# Git Undo: git restore vs git reset

## Introduction
Git propose plusieurs façons d'annuler des changements. Ce document explique les différences entre \`git restore\` et \`git reset\`, deux commandes souvent utilisées pour annuler des modifications.

---

## 1. git restore

### Objectif
Annuler des modifications **non commitées** dans le working directory ou le staging area.

### Utilisations courantes

#### a) Annuler des modifications non stagées
\`\`\`bash
# Annuler les changements dans un fichier (working directory)
git restore <fichier>
\`\`\`

**Exemple** :
\`\`\`bash
echo \"changement\" >> a.txt
git restore a.txt  # Le fichier revient à son état précédent
\`\`\`

#### b) Retirer un fichier du staging (sans perdre les modifications)
\`\`\`bash
# Dés-stage un fichier mais garde les modifications
git restore --staged <fichier>
\`\`\`

#### c) Annuler complètement (staging + working directory)
\`\`\`bash
# Annule tout (staging et modifications locales)
git restore --source=HEAD --staged --worktree <fichier>
\`\`\`

### Avantages de git restore
- **Sûr** : N'affecte que les changements non commités
- **Précis** : Peut cibler des fichiers spécifiques
- **Intuitif** : Remet les fichiers à un état connu

---

## 2. git reset

### Objectif
Annuler des commits ou déplacer le HEAD.

### Utilisations courantes

#### a) Annuler le dernier commit (garder les modifications)
\`\`\`bash
# Supprime le commit mais garde les changements dans le working directory
git reset --soft HEAD~1
\`\`\`

#### b) Annuler le dernier commit (perdre les modifications)
\`\`\`bash
# Supprime le commit et les modifications
git reset --hard HEAD~1
\`\`\`

#### c) Retirer un fichier du staging
\`\`\`bash
# Ancienne méthode (avant git restore)
git reset HEAD <fichier>
\`\`\`

### Modes de git reset

| Mode | Effet sur HEAD | Staging Area | Working Directory |
|------|----------------|--------------|-------------------|
| \`--soft\` | Modifié | Inchangé | Inchangé |
| \`--mixed\` (défaut) | Modifié | Réinitialisé | Inchangé |
| \`--hard\` | Modifié | Réinitialisé | Réinitialisé |

---

## 3. Comparaison détaillée

| Aspect | git restore | git reset |
|--------|-------------|----------|
| **Annule les commits** | ❌ Non | ✅ Oui |
| **Annule les modifications non commitées** | ✅ Oui | ⚠️ Indirectement |
| **Modifie l'historique** | ❌ Non | ✅ Oui |
| **Risque de perte de données** | Faible | Élevé (avec --hard) |
| **Apparition dans Git** | Git 2.23 (2019) | Depuis les débuts |
| **Recommandé pour** | Annuler modifications locales | Réinitialiser l'historique |

---

## 4. Démonstration pratique

### Scénario 1: Modification non voulue dans un fichier
\`\`\`bash
# 1. Modifier un fichier
echo \"texte\" >> b.txt

# 2. Annuler la modification
git restore b.txt

# Résultat: Le fichier revient à son état original
\`\`\`

### Scénario 2: Fichier ajouté par erreur au staging
\`\`\`bash
# 1. Ajouter un fichier par erreur
git add fichier-erreur.txt

# 2. Le retirer du staging
git restore --staged fichier-erreur.txt

# Résultat: Le fichier est dés-stagé mais les modifications restent
\`\`\`

### Scénario 3: Dernier commit avec un mauvais message
\`\`\`bash
# 1. Annuler le dernier commit (garder les changements)
git reset --soft HEAD~1

# 2. Re-committer avec le bon message
git commit -m \"message correct\"

# Résultat: L'historique est corrigé sans perte de données
\`\`\`

---

## 5. Bonnes pratiques

### Utiliser git restore quand...
- Vous voulez annuler des changements non commités
- Vous voulez retirer un fichier du staging
- Vous voulez éviter de modifier l'historique

### Utiliser git reset quand...
- Vous voulez supprimer le dernier commit
- Vous voulez combiner plusieurs commits
- Vous êtes sûr de vouloir modifier l'historique

### Éviter git reset --hard
- Peut entraîner une perte définitive de données
- Privilégier \`git reset --soft\` ou \`git restore\`

---

## 6. Commandes équivalentes

| Ancienne méthode (avant Git 2.23) | Nouvelle méthode (recommandée) |
|-----------------------------------|--------------------------------|
| \`git checkout -- <fichier>\` | \`git restore <fichier>\` |
| \`git reset HEAD <fichier>\` | \`git restore --staged <fichier>\` |
| \`git checkout <commit> -- <fichier>\` | \`git restore --source=<commit> <fichier>\` |

---

## Conclusion

- **git restore** est plus intuitif pour annuler des modifications locales
- **git reset** est puissant mais peut être dangereux avec \`--hard\`
- Depuis Git 2.23, \`git restore\` est la méthode recommandée pour annuler des changements non commités
- Toujours vérifier l'état avec \`git status\` avant d'annuler

---

*Document créé dans le cadre du challenge C07 - Undo sans paniquer*
*Date: $(date)* 
