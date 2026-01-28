# Spécification : Règles de validation

## Objectif
Garantir que l'output HTML est conforme au design system et aux règles UX.

## Niveaux de validation

### Niveau 1 : Syntaxe (BLOQUANT)
- HTML valide (balises fermées, imbrication correcte)
- Pas de `{{variables}}` non résolues
- Encodage UTF-8 correct

### Niveau 2 : Structure (BLOQUANT)
- DOCTYPE présent
- `<html lang="">` présent
- `<head>` contient les meta obligatoires
- Un seul `<h1>` par page
- Hiérarchie des headings respectée (pas de h3 après h1 sans h2)

### Niveau 3 : Design System (BLOQUANT)
- Toutes les classes CSS utilisées sont documentées
- Préfixes respectés (th-, st-, c-)
- Pas de styles inline (sauf exception documentée)

### Niveau 4 : UX (AVERTISSEMENT)
- Règles du ux-system.md respectées
- Checklist UX validée

### Niveau 5 : Accessibilité (AVERTISSEMENT)
- Images ont un attribut `alt`
- Liens ont un texte descriptif
- Contraste suffisant (si vérifiable)
- Structure sémantique correcte

## Checklist automatique

### HTML Structure
```
[ ] DOCTYPE html présent
[ ] <html lang="xx"> présent
[ ] <meta charset="UTF-8"> en premier dans <head>
[ ] <meta name="viewport" ...> présent
[ ] <title> présent et non vide
[ ] Un seul <h1> par page
[ ] Hiérarchie h1 > h2 > h3 > h4 > h5 > h6 respectée
[ ] Toutes les balises sont fermées
[ ] Imbrication correcte
```

### Classes CSS
```
[ ] Aucune classe sans préfixe (th-, st-, c-)
[ ] Toutes les classes th-* existent dans design-system.md
[ ] Toutes les classes st-* existent dans ux-system.md
[ ] Pas de classes Tailwind non autorisées (si applicable)
```

### Images
```
[ ] Attribut alt présent sur toutes les <img>
[ ] Attribut alt non vide (sauf images décoratives avec alt="")
[ ] Attribut src valide (fichier existe ou URL valide)
[ ] Attribut loading="lazy" sur images below-the-fold
```

### Liens
```
[ ] Attribut href présent
[ ] Pas de href="#" sans JavaScript associé
[ ] Liens externes ont target="_blank" + rel="noopener"
[ ] Texte de lien descriptif (pas de "cliquez ici")
```

### Formulaires
```
[ ] Tous les <input> ont un <label> associé
[ ] Attribut type présent sur <input>
[ ] Attribut name présent sur <input>
[ ] <button> a un type explicite (submit, button, reset)
```

### Performance
```
[ ] Pas de scripts bloquants dans <head> (sauf critique)
[ ] CSS critique inline ou préchargé
[ ] Images optimisées (format webp si possible)
[ ] Pas de ressources externes non nécessaires
```

## Rapport de validation

Format du rapport :
```json
{
  "file": "public/about/index.html",
  "timestamp": "2024-01-27T14:30:00Z",
  "status": "PASS | WARN | FAIL",
  "summary": {
    "errors": 0,
    "warnings": 2,
    "passed": 45
  },
  "details": [
    {
      "level": "error | warning | info",
      "rule": "html-single-h1",
      "message": "Multiple <h1> tags found",
      "line": 42,
      "suggestion": "Keep only one <h1> per page"
    }
  ]
}
```

## Commandes de validation

### Valider un fichier
```
/project:validate public/about/index.html
```

### Valider tout le site
```
/project:validate --all
```

### Valider avec niveau spécifique
```
/project:validate --level=3  # Jusqu'au Design System
```

### Mode strict (warnings = errors)
```
/project:validate --strict
```

## Actions correctives

Pour chaque erreur, proposer :
1. Description du problème
2. Localisation exacte (fichier, ligne)
3. Règle violée (référence au document)
4. Suggestion de correction
5. Correction automatique si possible

Exemple :
```
❌ ERREUR: Classe CSS non documentée
   Fichier: public/about/index.html
   Ligne: 23
   Classe: "custom-header"
   Règle: design-system.md > Classes CSS > Préfixes

   Suggestion: Utiliser "c-custom-header" (préfixe custom)
   ou "th-header" (si c'est le composant thème)

   Corriger automatiquement ? (oui/non)
```
