# Spécification : Déploiement

## Principe

Le déploiement consiste à copier UNIQUEMENT le contenu de `public/` vers le serveur de destination.

```
AVANT BUILD:
sites/mon-site/
├── content/        ← Sources (pas déployées)
├── overrides/      ← Config (pas déployée)
└── public/         ← VIDE

APRÈS BUILD:
sites/mon-site/
├── content/
├── overrides/
└── public/         ← HTML généré
    ├── index.html
    ├── about/index.html
    └── ...

APRÈS DÉPLOIEMENT:
Serveur FTP:
/public_html/
├── index.html      ← Copié depuis public/
├── about/index.html
└── ...
```

---

## Ce qui doit être déployé

```
UNIQUEMENT le contenu de : sites/[ton-site]/public/

PAS le reste du framework !
```

### Structure sur le serveur FTP
```
/var/www/html/          (ou /public_html/, /www/, etc.)
├── index.html          ← depuis public/index.html
├── about/
│   └── index.html
├── blog/
│   ├── index.html
│   └── mon-article/
│       └── index.html
├── assets/
│   ├── css/
│   ├── js/
│   └── images/
├── robots.txt
└── sitemap.xml
```

---

## Configuration du déploiement

### Dans `site.json`
```json
{
  "deploy": {
    "method": "ftp",
    "ftp": {
      "host": "ftp.example.com",
      "port": 21,
      "user": "ENV:FTP_USER",
      "password": "ENV:FTP_PASSWORD",
      "remotePath": "/public_html/",
      "secure": true
    }
  }
}
```

### Lecture des variables d'environnement

`ENV:XXX` = lire depuis variable d'environnement (sécurité)

**Ne jamais stocker de mots de passe en clair dans site.json !**

### Options de configuration

| Champ | Type | Description | Défaut |
|-------|------|-------------|--------|
| `method` | string | `ftp`, `sftp`, `rsync`, `s3`, `netlify` | `ftp` |
| `ftp.host` | string | Serveur FTP | Obligatoire |
| `ftp.port` | int | Port FTP | `21` |
| `ftp.user` | string | Utilisateur (ou ENV:) | Obligatoire |
| `ftp.password` | string | Mot de passe (ou ENV:) | Obligatoire |
| `ftp.remotePath` | string | Chemin sur le serveur | `/` |
| `ftp.secure` | bool | FTPS (TLS) | `true` |
| `sftp.port` | int | Port SFTP | `22` |
| `sftp.privateKey` | string | Chemin clé privée | - |

---

## Commande locale

### `/project:export`

```
/project:export --zip
→ Crée mon-site.zip contenant le contenu de public/

/project:export --ftp
→ Déploie via FTP selon la config de site.json

/project:export --sftp
→ Déploie via SFTP

/project:export --folder /chemin/destination
→ Copie dans un dossier local
```

### Comportement

1. Vérifie que `public/` existe et n'est pas vide
2. Valide la configuration de déploiement
3. Exécute le déploiement selon la méthode choisie
4. Affiche le résultat (succès ou erreurs)

---

## GitHub Actions

### Secrets à configurer dans GitHub

```
Settings > Secrets and variables > Actions > New repository secret

FTP_HOST     = ftp.tonhebergeur.com
FTP_USER     = ton-user-ftp
FTP_PASSWORD = ton-mot-de-passe
FTP_PORT     = 21 (optionnel)
```

### Workflow FTP (recommandé)

Voir `.github/workflows/deploy.yml`

### Variantes supportées

#### SFTP
```yaml
- name: Deploy to SFTP
  uses: wlixcc/SFTP-Deploy-Action@v1.2.4
  with:
    server: ${{ secrets.SFTP_HOST }}
    username: ${{ secrets.SFTP_USER }}
    password: ${{ secrets.SFTP_PASSWORD }}
    port: ${{ secrets.SFTP_PORT || 22 }}
    local_path: ./claude-ssg/sites/${{ env.SITE_NAME }}/public/*
    remote_path: /public_html/
```

#### rsync over SSH
```yaml
- name: Deploy via rsync
  uses: burnett01/rsync-deployments@6.0.0
  with:
    switches: -avzr --delete
    path: ./claude-ssg/sites/${{ env.SITE_NAME }}/public/
    remote_path: /var/www/html/
    remote_host: ${{ secrets.SSH_HOST }}
    remote_user: ${{ secrets.SSH_USER }}
    remote_key: ${{ secrets.SSH_PRIVATE_KEY }}
```

#### Netlify
```yaml
- name: Deploy to Netlify
  uses: nwtgck/actions-netlify@v2.1
  with:
    publish-dir: ./claude-ssg/sites/${{ env.SITE_NAME }}/public
    production-deploy: true
  env:
    NETLIFY_AUTH_TOKEN: ${{ secrets.NETLIFY_AUTH_TOKEN }}
    NETLIFY_SITE_ID: ${{ secrets.NETLIFY_SITE_ID }}
```

#### GitHub Pages
```yaml
- name: Deploy to GitHub Pages
  uses: peaceiris/actions-gh-pages@v3
  with:
    github_token: ${{ secrets.GITHUB_TOKEN }}
    publish_dir: ./claude-ssg/sites/${{ env.SITE_NAME }}/public
```

---

## Stratégies de déploiement

### Stratégie 1 : Build local, commit public/, deploy en CI

```
1. Tu travailles en local avec Claude Code
2. Tu fais /project:build
3. Tu commit TOUT (y compris public/)
4. GitHub Action déploie public/ via FTP
```

**Avantage :** Simple, pas besoin de Claude en CI
**Inconvénient :** Le repo contient les fichiers générés

### Stratégie 2 : Build en CI

```
1. Tu travailles en local avec Claude Code
2. Tu commit SEULEMENT content/ et config
3. GitHub Action rebuild + déploie
```

**Avantage :** Repo propre
**Inconvénient :** Nécessite Claude/Node en CI (complexe)

### Recommandation

**Stratégie 1** pour commencer. Plus simple, plus fiable.

---

## Fichiers de configuration

### .gitignore recommandé

```gitignore
# Ignorer les fichiers générés SI tu choisis la stratégie 2
# claude-ssg/sites/*/public/

# Toujours ignorer
claude-ssg/sites/*/_state/
.DS_Store
*.log
.env
.env.local
node_modules/
```

### Structure du repo Git recommandée

```
mon-repo/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── claude-ssg/
│   ├── core/
│   ├── themes/
│   ├── site-types/
│   └── sites/
│       └── mon-site/
│           ├── site.json
│           ├── content/
│           ├── overrides/
│           └── public/      ← Déployé
├── .gitignore
├── CLAUDE.md
└── README.md
```

---

## Vérifications pré-déploiement

Avant de déployer, Claude vérifie :

1. **Build valide** : `public/` contient des fichiers
2. **HTML valide** : Pas d'erreurs de syntaxe
3. **Liens fonctionnels** : Pas de liens cassés internes
4. **Assets présents** : CSS, JS, images référencés existent
5. **SEO minimum** : Title et description sur chaque page

### Commande de vérification

```
/project:validate --pre-deploy
```

---

## Rollback

En cas de problème après déploiement :

1. Revenir au commit précédent : `git checkout HEAD~1`
2. Rebuild : `/project:build`
3. Redéployer : `/project:export --ftp`

Ou via GitHub :
1. Revert le commit problématique
2. Le workflow se relance automatiquement

---

## Logs et debugging

### Logs locaux

Les logs de déploiement sont stockés dans :
```
sites/[site]/_state/deploy.log
```

### Format du log

```
[2024-01-27 14:30:00] INFO: Déploiement démarré
[2024-01-27 14:30:01] INFO: Connexion à ftp.example.com:21
[2024-01-27 14:30:02] INFO: Upload de 15 fichiers...
[2024-01-27 14:30:10] INFO: Fichier index.html uploadé
[2024-01-27 14:30:15] SUCCESS: Déploiement terminé (8 secondes)
```

### Erreurs courantes

| Erreur | Cause | Solution |
|--------|-------|----------|
| Connection refused | Port incorrect ou bloqué | Vérifier port et firewall |
| Authentication failed | Identifiants incorrects | Vérifier user/password |
| Permission denied | Droits insuffisants | Vérifier permissions FTP |
| No such file | Chemin distant incorrect | Vérifier remotePath |
| Timeout | Serveur lent ou inaccessible | Réessayer ou vérifier serveur |
