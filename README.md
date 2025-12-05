# Test Helm

Ce dépôt est un dépôt de test pour expérimenter avec la CI/CD et les workflows réutilisables.

## Description

Ce projet contient les charts Helm pour le déploiement de l'application [`test-app`](https://github.com/dnum-mi/test-app) à l'aide du [dépôt de workflows](https://github.com/dnum-mi/fabnum-cicd). Il permet principalement de tester les workflows réutilisables et les pipelines CI/CD.

## Structure

- `charts/test-app/` - Chart Helm principal avec les templates pour le déploiement
  - `client/` - Composants client
  - `server/` - Composants serveur
  - `secrets/` - Gestion des secrets avec Vault
- `ci/` - Configuration pour l'intégration continue

## Utilisation

Ce dépôt est destiné uniquement à des fins de test et d'expérimentation.
