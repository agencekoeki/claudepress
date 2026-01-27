---
name: init-project
description: Initialise la structure complète du framework Claude SSG. À exécuter UNE SEULE FOIS pour créer le système de base.
arguments: none
---

# Commande : init-project

## But
Créer l'architecture complète du framework Claude SSG dans le répertoire courant.
Cette commande pose les fondations. Elle crée TOUS les dossiers et fichiers de base nécessaires au fonctionnement du système.

## Pré-requis
- Le répertoire courant doit être VIDE ou ne pas contenir de dossier `claude-ssg/`
- Si un dossier `claude-ssg/` existe déjà, STOPPER et demander confirmation avant d'écraser

## Étapes d'exécution

### ÉTAPE 1 : Vérification
1. Vérifier si `./claude-ssg/` existe
2. Si OUI :
   - Afficher : "⚠️ Un projet Claude SSG existe déjà dans ce répertoire."
   - Demander : "Voulez-vous l'écraser ? (oui/non)"
   - Si "non" : STOPPER
3. Si NON : continuer

### ÉTAPE 2 : Création de l'arborescence
Créer la structure complète avec tous les dossiers et fichiers templates.

### ÉTAPE 3 : Confirmation
Afficher un résumé de ce qui a été créé.

## Utilisation
```
/init-project
```

## Résultat
Structure complète du framework créée et prête à l'emploi.
