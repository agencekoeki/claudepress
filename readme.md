# 🏗️ Claude SSG

> **Ton site web statique, généré par l'IA, sans dépendances, hébergeable partout.**

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)]()
[![License](https://img.shields.io/badge/license-MIT-green.svg)]()
[![Claude](https://img.shields.io/badge/powered%20by-Claude-orange.svg)]()

---

## 📋 Table des matières

1. [C'est quoi Claude SSG ?](#-cest-quoi-claude-ssg-)
2. [Pourquoi Claude SSG ?](#-pourquoi-claude-ssg-)
3. [Pour qui ?](#-pour-qui-)
4. [Concepts clés](#-concepts-clés)
5. [Installation](#-installation)
6. [Démarrage rapide](#-démarrage-rapide)
7. [Structure du projet](#-structure-du-projet)
8. [Guide d'utilisation](#-guide-dutilisation)
9. [Créer son premier site](#-créer-son-premier-site)
10. [Personnalisation](#-personnalisation)
11. [Commandes](#-commandes)
12. [FAQ](#-faq)
13. [Dépannage](#-dépannage)
14. [Contribuer](#-contribuer)
15. [Licence](#-licence)

---

## 🤔 C'est quoi Claude SSG ?

**Claude SSG** est un générateur de site statique (SSG) piloté par Claude Code.

### En termes simples :
```
Toi : "Crée-moi une page À propos avec mon parcours"
         ↓
    Claude SSG
         ↓
   about/index.html (fichier HTML prêt à publier)
```

### Qu'est-ce qu'un site statique ?

Un **site statique** = des fichiers HTML/CSS/JS simples, sans base de données, sans serveur complexe.
```
Site dynamique (WordPress) :
Visiteur → Serveur → PHP → Base de données → HTML généré → Visiteur
(Complexe, lent, vulnérable)

Site statique (Claude SSG) :
Visiteur → Serveur → HTML déjà prêt → Visiteur
(Simple, rapide, sécurisé)
```

### Qu'est-ce qui le rend spécial ?

| SSG classique (Jekyll, Hugo...) | Claude SSG |
|---------------------------------|------------|
| Tu écris des templates | Tu décris ce que tu veux |
| Tu apprends une syntaxe | Tu parles naturellement |
| Tu configures des fichiers | Tu demandes à Claude |
| Tu codes | Tu dialogues |

---

## 💡 Pourquoi Claude SSG ?

### Les problèmes qu'il résout

#### 1. "Je veux un site simple, mais les outils sont compliqués"

- WordPress ? Trop lourd, vulnérable, lent
- Jekyll/Hugo ? Il faut apprendre Ruby/Go
- Next.js ? C'est pour des apps, pas des sites
- Wix/Squarespace ? Enfermé chez eux, pas de contrôle

**Claude SSG** : Du HTML pur, que tu contrôles, sans dépendances.

#### 2. "Je suis sur un hébergement mutualisé"

Tu as un hébergement à 3€/mois chez OVH, o2switch, ou autre ?

Pas de Node.js ? Pas de Ruby ? Pas de problème.

**Claude SSG** génère du HTML statique. Tu copies les fichiers par FTP. Terminé.

#### 3. "Je veux que mon site soit rapide"

| Type de site | Temps de chargement typique |
|--------------|------------------------------|
| WordPress | 2-5 secondes |
| React SPA | 1-3 secondes |
| Site statique | 0.2-0.5 secondes |

Pas de base de données = pas d'attente.

#### 4. "Je veux garder le contrôle"

- ✅ Tes fichiers sont sur ton ordinateur
- ✅ Pas de compte obligatoire
- ✅ Pas de vendor lock-in
- ✅ Tu peux tout modifier
- ✅ Tu peux migrer quand tu veux

---

## 👤 Pour qui ?

### ✅ Claude SSG est fait pour toi si :

- Tu veux un site vitrine, un portfolio, un blog
- Tu es à l'aise avec Claude Code (ou tu veux apprendre)
- Tu préfères parler que coder
- Tu veux des fichiers HTML propres et simples
- Tu es sur un hébergement basique (mutualisé)
- Tu veux un site rapide et sécurisé

### ❌ Claude SSG n'est PAS fait pour toi si :

- Tu veux un site e-commerce complexe → utilise Shopify
- Tu veux des utilisateurs avec login → utilise un framework
- Tu veux du contenu généré en temps réel → utilise une app
- Tu ne veux pas utiliser Claude → utilise Hugo/Jekyll

---

## 🧠 Concepts clés

Avant de commencer, comprends ces 4 concepts :

### 1. Les 4 couches
```
┌─────────────────────────────────────────────┐
│  🌐 TON SITE                                │
│  Le contenu que tu crées (textes, images)   │
├─────────────────────────────────────────────┤
│  📐 SITE-TYPE                               │
│  Les règles UX (où mettre quoi, comment)    │
├─────────────────────────────────────────────┤
│  🎨 THÈME                                   │
│  L'apparence (couleurs, typo, espacements)  │
├─────────────────────────────────────────────┤
│  ⚙️ MOTEUR (Core)                           │
│  Les règles du système (ne touche pas)      │
└─────────────────────────────────────────────┘
```

**Analogie cuisine :**
- Moteur = Les règles de la cuisine (hygiène, températures)
- Thème = Le style de présentation (rustique, moderne, japonais)
- Site-type = Le type de plat (entrée, plat, dessert)
- Ton site = Les ingrédients que TU choisis

### 2. Le Design System

C'est le **dictionnaire visuel** de ton site.

Il définit EXACTEMENT :
- Quelles couleurs utiliser
- Quelles polices
- Quels espacements
- À quoi ressemble chaque élément

**Pourquoi ?** Pour que ton site soit cohérent. Partout. Toujours.

### 3. L'UX System

C'est le **livre de règles** de l'expérience utilisateur.

Il définit :
- Où placer les éléments
- Combien d'éléments max
- Ce qui est interdit (popup agressive, etc.)
- Ce qui est obligatoire (CTA visible, etc.)

**Pourquoi ?** Pour que ton site soit efficace, pas juste joli.

### 4. Le Build

C'est la **transformation** de tes fichiers texte en pages HTML.
```
Avant (ce que tu écris) :
content/about.md (texte Markdown)

Après (ce que Claude génère) :
public/about/index.html (page web)
```

---

## 📦 Installation

### Prérequis

1. **Claude Code** installé et fonctionnel
   - [Guide d'installation officiel](https://docs.anthropic.com/claude-code)

2. **Un terminal** (inclus sur Mac/Linux, ou Windows Terminal)

3. **Un éditeur de texte** (VS Code recommandé)

### Étapes d'installation

#### Étape 1 : Créer un dossier pour ton projet
```bash
mkdir mon-projet-web
cd mon-projet-web
```

#### Étape 2 : Lancer Claude Code
```bash
claude
```

#### Étape 3 : Initialiser Claude SSG

Dans Claude Code, tape :
```
/project:init-project
```

Claude va créer toute la structure nécessaire.

#### Étape 4 : Vérifier l'installation
```
/project:status
```

Tu devrais voir :
```
✅ Claude SSG initialisé

Version : 1.0.0
Sites : 0
Thèmes : 1 (template)
Site-types : 1 (template)
```

---

## 🚀 Démarrage rapide

### En 5 minutes, crée ton premier site :
```
# 1. Crée un site
/project:init-site mon-premier-site

# 2. Réponds aux questions :
#    - Quel thème ? → minimal
#    - Quel type ? → landing-saas (ou blog, portfolio...)

# 3. Crée une page
/project:new-page about --title="À propos"

# 4. Génère le site
/project:build

# 5. Regarde le résultat
/project:preview
```

Ouvre http://localhost:8000 dans ton navigateur. 🎉

---

## 📁 Structure du projet

Après installation, voici ce que tu as :
```
mon-projet-web/
│
├── claude-ssg/                    ← LE FRAMEWORK
│   │
│   ├── core/                      ← ⚙️ Moteur (NE PAS TOUCHER)
│   │   ├── CLAUDE.md              ← Instructions pour Claude
│   │   ├── rules/                 ← Règles automatiques
│   │   ├── engine/                ← Spécifications techniques
│   │   └── commands/              ← Les commandes disponibles
│   │
│   ├── themes/                    ← 🎨 Les thèmes visuels
│   │   ├── _template/             ← Modèle vide
│   │   └── minimal/               ← Exemple de thème
│   │
│   ├── site-types/                ← 📐 Les types de sites
│   │   ├── _template/             ← Modèle vide
│   │   └── landing-saas/          ← Exemple de type
│   │
│   └── sites/                     ← 🌐 TES SITES
│       ├── _template/             ← Modèle vide
│       └── mon-premier-site/      ← Ton site !
│           ├── site.json          ← Configuration
│           ├── content/           ← Tes pages (Markdown)
│           │   └── index.md       ← Page d'accueil
│           ├── overrides/         ← Tes personnalisations
│           ├── public/            ← HTML généré (pour FTP)
│           └── _state/            ← État du build
│
└── README.md                      ← Ce fichier !
```

### Où mettre quoi ?

| Tu veux... | Tu modifies... |
|------------|----------------|
| Changer le contenu d'une page | `sites/[site]/content/[page].md` |
| Changer la config du site | `sites/[site]/site.json` |
| Personnaliser un composant | `sites/[site]/overrides/components/` |
| Créer un nouveau thème | `themes/[nom]/` |
| Créer un nouveau type de site | `site-types/[nom]/` |
| Modifier le moteur | **NE PAS FAIRE** (sauf si tu sais ce que tu fais) |

---

## 📖 Guide d'utilisation

### Écrire du contenu

Tes pages sont en **Markdown** avec un **front-matter** YAML.

#### Exemple de page (`content/about.md`)
```markdown
---
title: "À propos de moi"
description: "Découvrez mon parcours et mes compétences"
layout: page
---

# À propos

Bonjour ! Je suis **Jean Dupont**, développeur web passionné.

## Mon parcours

J'ai commencé le développement en 2015...

## Mes compétences

- HTML / CSS / JavaScript
- PHP / WordPress
- SEO technique

## Me contacter

Envoyez-moi un email à [contact@example.com](mailto:contact@example.com).
```

#### Le front-matter (entre les `---`)

C'est la **configuration** de ta page.

| Champ | Obligatoire | Description |
|-------|-------------|-------------|
| `title` | ✅ Oui | Titre de la page |
| `description` | 🟡 Recommandé | Description pour SEO |
| `layout` | Non | Template à utiliser (défaut: "default") |
| `date` | Non | Date de publication |
| `draft` | Non | `true` pour ne pas publier |

#### Le Markdown (après le front-matter)

C'est ton **contenu**.

| Tu écris... | Tu obtiens... |
|-------------|---------------|
| `# Titre` | `<h1>Titre</h1>` |
| `## Sous-titre` | `<h2>Sous-titre</h2>` |
| `**gras**` | `<strong>gras</strong>` |
| `*italique*` | `<em>italique</em>` |
| `[lien](url)` | `<a href="url">lien</a>` |
| `![alt](image.jpg)` | `<img src="image.jpg" alt="alt">` |
| `- item` | Liste à puces |
| `1. item` | Liste numérotée |
| `> citation` | Bloc de citation |
| `` `code` `` | Code inline |

### Configurer ton site

Édite `sites/[ton-site]/site.json` :
```json
{
  "name": "Mon Super Site",
  "url": "https://monsupersite.com",
  "description": "Un site génial créé avec Claude SSG",
  "lang": "fr",
  "author": "Jean Dupont",

  "theme": "minimal",
  "siteType": "landing-saas",

  "navigation": [
    {"label": "Accueil", "url": "/"},
    {"label": "À propos", "url": "/about/"},
    {"label": "Blog", "url": "/blog/"},
    {"label": "Contact", "url": "/contact/"}
  ],

  "social": {
    "twitter": "https://twitter.com/moncompte",
    "linkedin": "https://linkedin.com/in/monprofil",
    "github": "https://github.com/moncompte"
  }
}
```

### Builder ton site
```
/project:build
```

Claude va :
1. Lire tous tes fichiers `content/*.md`
2. Appliquer le thème et les règles UX
3. Générer les fichiers HTML dans `public/`

### Publier ton site

Copie le contenu de `public/` sur ton serveur :
```bash
# Par FTP (avec ton client FTP préféré)
public/* → /var/www/html/

# Ou avec rsync
rsync -avz public/ user@serveur:/var/www/html/

# Ou avec la commande export
/project:export --ftp
```

---

## 🎨 Créer son premier site

### Scénario : Tu veux un site vitrine pour ton activité

#### Étape 1 : Initialise le site
```
/project:init-site agence-martin
```

Claude te demande :
- Quel thème ? → `minimal`
- Quel type ? → `landing-saas`

#### Étape 2 : Configure le site

Édite `sites/agence-martin/site.json` :
```json
{
  "name": "Agence Martin",
  "url": "https://agence-martin.fr",
  "description": "Agence de communication à Lyon",
  "lang": "fr",
  "author": "Sophie Martin",
  "theme": "minimal",
  "siteType": "landing-saas",
  "navigation": [
    {"label": "Accueil", "url": "/"},
    {"label": "Services", "url": "/services/"},
    {"label": "Réalisations", "url": "/portfolio/"},
    {"label": "Contact", "url": "/contact/"}
  ]
}
```

#### Étape 3 : Crée les pages
```
/project:new-page services --title="Nos services"
/project:new-page portfolio --title="Nos réalisations"
/project:new-page contact --title="Contactez-nous"
```

#### Étape 4 : Rédige le contenu

Édite `content/index.md` :
```markdown
---
title: "Agence Martin - Communication à Lyon"
description: "Agence de communication digitale et print à Lyon"
layout: homepage
---

# Donnez vie à vos idées

Nous transformons vos projets en succès depuis 2010.

[Découvrir nos services](/services/)
```

Édite `content/services.md` :
```markdown
---
title: "Nos services"
description: "Services de communication, design et web"
layout: page
---

# Nos services

## Communication digitale

Stratégie social media, publicité en ligne, content marketing...

## Design graphique

Logo, charte graphique, supports print...

## Création web

Sites vitrines, e-commerce, applications...
```

#### Étape 5 : Build et preview
```
/project:build
/project:preview
```

Ouvre http://localhost:8000 🎉

#### Étape 6 : Publie
```
/project:export --zip
```

Tu obtiens un fichier `agence-martin.zip` à uploader sur ton serveur.

---

## 🔧 Personnalisation

### Changer les couleurs

Tu veux un bleu différent ? Modifie le thème.

#### Option 1 : Modifier le thème existant

Édite `themes/minimal/theme.json` :
```json
{
  "tokens": {
    "colors": {
      "primary": "#1e3a5f",      ← Ta nouvelle couleur
      "accent": "#e63946"         ← Ta couleur d'accent
    }
  }
}
```

#### Option 2 : Créer ton propre thème
```
/project:new-theme mon-theme-perso
```

Puis personnalise `themes/mon-theme-perso/`.

### Modifier un composant

Tu veux un header différent ?
```
/project:override-component header
```

Cela crée `sites/[site]/overrides/components/header.html`.

Modifie-le à ta guise !

### Ajouter des règles UX

Tu veux interdire certaines pratiques ?
```
/project:override-ux
```

Cela crée `sites/[site]/overrides/ux-tweaks.md`.

Exemple :
```markdown
# Mes règles UX

## Navigation
- Maximum 4 items dans la nav (pas 5 comme le défaut)

## Images
- Toujours en format WebP
- Lazy loading obligatoire
```

---

## 🎮 Commandes

### Commandes principales

| Commande | Ce qu'elle fait |
|----------|-----------------|
| `/project:init-site [nom]` | Crée un nouveau site |
| `/project:build` | Génère le HTML |
| `/project:build [page]` | Génère une seule page |
| `/project:preview` | Lance un serveur local |
| `/project:validate` | Vérifie que tout est OK |

### Commandes de création

| Commande | Ce qu'elle fait |
|----------|-----------------|
| `/project:new-page [chemin]` | Crée une nouvelle page |
| `/project:new-theme [nom]` | Crée un nouveau thème |
| `/project:new-site-type [nom]` | Crée un nouveau type de site |
| `/project:new-component [nom]` | Crée un nouveau composant |

### Commandes d'information

| Commande | Ce qu'elle fait |
|----------|-----------------|
| `/project:status` | Affiche l'état du projet |
| `/project:list-themes` | Liste les thèmes disponibles |
| `/project:list-site-types` | Liste les types de sites |
| `/project:diff` | Montre les changements depuis le dernier build |

### Commandes de publication

| Commande | Ce qu'elle fait |
|----------|-----------------|
| `/project:export --zip` | Crée une archive ZIP |
| `/project:export --ftp` | Envoie par FTP (config requise) |
| `/project:audit` | Audit complet (perf, SEO, accessibilité) |

---

## ❓ FAQ

### Questions générales

<details>
<summary><strong>C'est gratuit ?</strong></summary>

Claude SSG lui-même est gratuit et open-source.

Tu as besoin d'un accès à Claude Code (inclus dans l'abonnement Claude Pro ou via API).

</details>

<details>
<summary><strong>Ça marche sur Windows ?</strong></summary>

Oui ! Claude Code fonctionne sur Windows, Mac et Linux.

</details>

<details>
<summary><strong>Je peux faire un blog ?</strong></summary>

Oui ! Utilise le site-type `blog` et crée tes articles dans `content/blog/`.

</details>

<details>
<summary><strong>Je peux faire un e-commerce ?</strong></summary>

Pour un e-commerce simple (quelques produits, paiement Stripe), oui.

Pour un vrai e-commerce avec panier, stock, etc. → utilise Shopify ou WooCommerce.

</details>

<details>
<summary><strong>C'est compatible SEO ?</strong></summary>

Oui, et même très bon pour le SEO :
- HTML sémantique
- Chargement ultra-rapide
- Méta tags générés automatiquement
- Sitemap.xml automatique
- Pas de JavaScript bloquant

</details>

### Questions techniques

<details>
<summary><strong>Je peux utiliser Tailwind CSS ?</strong></summary>

Oui, tu peux créer un thème basé sur Tailwind.

Mais attention : le CSS final doit être compilé. Claude SSG ne fait pas de build CSS.

</details>

<details>
<summary><strong>Je peux ajouter du JavaScript ?</strong></summary>

Oui, dans `themes/[theme]/assets/js/` ou `sites/[site]/assets/js/`.

Mais reste minimaliste : le but est d'avoir un site statique léger.

</details>

<details>
<summary><strong>Je peux utiliser des composants React/Vue ?</strong></summary>

Non. Claude SSG génère du HTML statique.

Si tu veux du React, utilise Next.js ou Astro.

</details>

<details>
<summary><strong>Comment gérer les images ?</strong></summary>

Place-les dans `sites/[site]/assets/images/` et référence-les avec :
```markdown
![Description](/assets/images/mon-image.jpg)
```

</details>

<details>
<summary><strong>Comment ajouter Google Analytics ?</strong></summary>

Ajoute dans `sites/[site]/site.json` :
```json
{
  "scripts": {
    "head": ["<!-- GA code ici -->"]
  }
}
```

</details>

---

## 🔧 Dépannage

### "Commande non reconnue"
```
Erreur : /project:build n'est pas reconnu
```

**Solution :**
1. Vérifie que tu es dans le bon dossier
2. Vérifie que `claude-ssg/` existe
3. Relance Claude Code

### "Composant non trouvé"
```
🔴 ERREUR: Composant "hero" non trouvé
```

**Solution :**
1. Vérifie le nom du composant (faute de frappe ?)
2. Vérifie qu'il existe dans le thème
3. Crée-le avec `/project:new-component hero`

### "Variable non résolue"
```
🔴 ERREUR: Variable {{site.phone}} non résolue
```

**Solution :**
1. Ajoute la variable dans `site.json` :
```json
   { "phone": "01 23 45 67 89" }
```

### "Le build ne change rien"

**Causes possibles :**
1. Tu édites le mauvais fichier
2. Le cache est actif
3. Tu regardes le mauvais dossier

**Solution :**
```
/project:rebuild-all --no-cache
```

### "Le preview ne s'affiche pas"

**Solutions :**
1. Vérifie que le port 8000 est libre
2. Essaie un autre port : `/project:preview --port=3000`
3. Vérifie ton firewall

---

## 🤝 Contribuer

### Signaler un bug

1. Vérifie que le bug n'est pas déjà signalé
2. Crée une issue avec :
   - Description du problème
   - Étapes pour reproduire
   - Ce que tu attendais
   - Ce qui s'est passé

### Proposer une amélioration

1. Ouvre une issue pour en discuter d'abord
2. Fork le projet
3. Crée une branche : `git checkout -b feature/ma-feature`
4. Commit : `git commit -m "Add ma feature"`
5. Push : `git push origin feature/ma-feature`
6. Ouvre une Pull Request

### Code de conduite

- Sois respectueux
- Sois constructif
- Documente tes changements
- Teste avant de soumettre

---

## 📄 Licence

MIT License

Copyright (c) 2024

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

## 🙏 Remerciements

- [Anthropic](https://anthropic.com) pour Claude
- La communauté des SSG pour l'inspiration
- Toi, pour utiliser cet outil !

---

<p align="center">
  <strong>Fait avec ❤️ et Claude</strong>
</p>

<p align="center">
  <a href="#-claude-ssg">⬆️ Retour en haut</a>
</p>
