# CICD - Demo 01

## Principe du CI/CD
- Intégration continue (CI)
  - Récuperation du code
  - Validation de la qualité du code
  - Validation des tests
- Déployment continue (CD)
  - Mise en ligne du projet

## Mise en place
Créer des dossiers : `.github/workflows`
Créer un fichier `.yaml`/`.yml` pour créer un pipeline

## Structure de fichier
```yaml
# Nommage
name: Nom du pipeline

# Déclencheur (Trigger)
# https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows
on: 
  # Lors du push d'une branche
  push:
    branches: [main]
  # Déclenchement manuel (Ajoute un bouton à l'interface)
  workflow_dispatch:

# Travail à réaliser
jobs:
  demo_job:
    # Machine "prêtée" par github
    # https://docs.github.com/en/actions/reference/runners/github-hosted-runners
    runs-on: windows-latest 
    #Liste des étapes à réaliser
    steps:
      - name: Nom de l'étape du CI/CD
        run: commande à executer (Liée à l'OS)
      - name: Nouvelle étape
        run: commande à executer
``` 

## Utilisation des variables configuré dans le Repo

### Categories
- Variables 
  - Stocker en claire dans le github
  - Syntaxe d'utilisation : `${{ vars.NAME }}`

- Secrets
  - Stocker sur github et caché
  - Syntaxe d'utilisation : `${{ secrets.NAME }}`

- Github
  - Variable d'event du déclenchement
  - Syntaxe d'utilisation : `${{ github.ref }}` 

### Types de variables
- Repository 
  - Toujours accessible
- Environnement
  - Necessite de créer l'environnement dans github
  - Accessible uniquement pour les jobs avec `environment: ...`


## Utilisation des variables d'env

### Local
Définition de variable de le fichier `yaml`
```yaml
name: Exemple de variable d'env

env:
  EXEMPLE: "Ceci est un super variable local :o"

on: [workflow_dispatch]

jobs: 
# ...
```

Utilisation dans le workflow (Attention, ça dépend du terminal) : 
- Linux : `$EXEMPLE`
- Powershell: `$env:EXEMPLE`

### Github
Liste dispo sur :  
https://docs.github.com/en/actions/reference/workflows-and-actions/variables#default-environment-variables