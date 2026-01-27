# Validation Rules - Règles de validation

## Validation pré-build

Avant chaque génération, ces validations sont effectuées :

### 1. Validation des fichiers JSON

Tous les fichiers `.json` doivent :
- [ ] Être du JSON valide (parseable)
- [ ] Contenir les champs requis selon leur type
- [ ] Ne pas contenir de champs inconnus (warning)

#### site.json (requis)
```json
{
    "name": "string (requis)",
    "theme": "string (requis)",
    "type": "string (requis)",
    "url": "string (optionnel)",
    "language": "string (optionnel, défaut: 'en')"
}
```

#### theme.json (requis)
```json
{
    "name": "string (requis)",
    "version": "string (requis)",
    "author": "string (optionnel)"
}
```

#### preset.json (requis)
```json
{
    "name": "string (requis)",
    "description": "string (optionnel)",
    "default_theme": "string (optionnel)"
}
```

### 2. Validation des composants

Pour chaque composant référencé :
- [ ] Le fichier existe dans la cascade (site > type > thème)
- [ ] Le fichier n'est pas vide
- [ ] La syntaxe HTML est valide

### 3. Validation des variables

Pour chaque variable utilisée :
- [ ] La variable est définie quelque part
- [ ] OU un fallback est fourni
- [ ] OU la config autorise les variables vides

### 4. Validation du contenu

Pour chaque fichier Markdown :
- [ ] Le frontmatter YAML est valide (si présent)
- [ ] Les liens internes pointent vers des pages existantes
- [ ] Les images référencées existent

### 5. Validation des assets

Pour chaque asset référencé :
- [ ] Le fichier existe
- [ ] L'extension est autorisée
- [ ] La taille est raisonnable (warning si > 5MB)

## Messages d'erreur

Format standard :
```
[ERREUR] {type}: {message}
  → Fichier: {chemin}
  → Ligne: {numéro} (si applicable)
  → Suggestion: {correction proposée}
```

## Niveaux de sévérité

| Niveau | Action |
|--------|--------|
| ERROR | Bloque le build |
| WARNING | Affiche un avertissement, continue |
| INFO | Information, continue |

## Commande de validation

Exécuter une validation sans build :
```
/validate [site]
```

Affiche un rapport complet des erreurs et warnings.
