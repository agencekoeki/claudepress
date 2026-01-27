# Règles du Moteur SSG

## 1. Principe de fonctionnement

Le SSG Claude fonctionne en 3 phases :
1. **Parsing** : Lecture et analyse du contenu Markdown
2. **Résolution** : Application des variables et composants
3. **Assemblage** : Génération du HTML final

## 2. Ordre de résolution des composants

Lors de la génération, les composants sont résolus dans cet ordre (priorité décroissante) :

1. `sites/[site]/overrides/components/` - Surcharges du site
2. `site-types/[type]/components/` - Composants du type de site
3. `themes/[theme]/components/` - Composants du thème

Le premier fichier trouvé est utilisé.

## 3. Variables système

Variables toujours disponibles :

| Variable | Description |
|----------|-------------|
| `{{site.name}}` | Nom du site |
| `{{site.url}}` | URL de base |
| `{{page.title}}` | Titre de la page |
| `{{page.slug}}` | Slug de la page |
| `{{page.content}}` | Contenu parsé |
| `{{build.date}}` | Date de génération |
| `{{build.version}}` | Version du build |

## 4. Règles de validation

Avant chaque build, vérifier :

- [ ] Tous les composants référencés existent
- [ ] Toutes les variables sont définies
- [ ] Les fichiers de configuration sont valides (JSON)
- [ ] Les assets référencés existent

## 5. Gestion des erreurs

En cas d'erreur :
1. Afficher le message d'erreur clair
2. Indiquer le fichier et la ligne concernés
3. Ne PAS générer de fichier incomplet
4. Suggérer une correction si possible

## 6. Cache et état

Le fichier `_state/manifest.json` contient :
- Liste des fichiers générés
- Hashes des sources
- Date de dernière génération

Utiliser ce manifest pour les builds incrémentaux.
