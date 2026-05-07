# CICD - Demo 01

## Mise en place
Créer des dossiers : `.github/workflows`
Créer un fichier `.yaml`/`.yml` pour créer un pipeline

## Structure de fichier
```yaml
# Nommage
name: Nom du pipeline

# Déclencheur (Trigger)
on: 
  # Lors du push d'une branche
  push:
    branches: [main]
  # Déclenchement manuel (Ajoute un bouton à l'interface)
  workflow_dispatch:

# Travail à réaliser
jobs:
  demo_job:
    runs-on: windows-latest # Machine "prêtée" par github
    steps: #Liste des étapes à réaliser
      - name: Nom de l'étape du CI/CD
        run: commande à executer (Liée à l'OS)
      - name: Nouvelle étape
        run: commande à executer
``` 