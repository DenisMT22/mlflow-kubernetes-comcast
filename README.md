# MLflow on Kubernetes - Comcast Exercise

## Objectif

Déployer une infrastructure MLflow scalable sur Kubernetes pour permettre aux Data Scientists de Comcast de tracker et servir leurs modèles ML en production.

## Architecture du projet

mlflow-kubernetes/
├── mlflow-deployment.yaml        # Deployment et Service Kubernetes
├── mlflow-secrets-template.yaml  # Template pour secrets sécurisés
├── screenshots/                  # Captures d'écran de l'interface
└── README.md                     # Documentation complète

## Technologies utilisées

### Infrastructure et Orchestration

- Kubernetes : Orchestration de conteneurs et scalabilité
- Minikube : Cluster Kubernetes local pour développement
- Docker : Conteneurisation (PostgreSQL, MLflow)

### Cloud et Stockage

- AWS S3 : Stockage d'artefacts de modèles ML
- AWS IAM : Gestion des accès et credentials
- AWS CLI : Interface en ligne de commande AWS

### Base de données

- PostgreSQL : Stockage des métadonnées MLflow
- Docker Networks : Communication entre conteneurs

### MLOps et Machine Learning

- MLflow : Tracking d'expériences et gestion de modèles
- MLflow Tracking Server : Serveur centralisé pour équipes

### Sécurité

- Kubernetes Secrets : Stockage sécurisé des credentials
- Base64 Encoding : Encodage des données sensibles

### Outils de développement

- VS Code : Éditeur de code et fichiers YAML
- Terminal/CLI : Administration système et Kubernetes
- Git/GitHub : Versioning et collaboration

## Compétences acquises

### Data Engineering

- Architecture MLOps : Conception d'infrastructure pour ML en production
- Déploiement cloud : Intégration AWS (S3, IAM) avec Kubernetes
- Scalabilité : Solutions pour supporter de multiples utilisateurs
- Monitoring : Configuration de tracking pour modèles ML

### DevOps et Infrastructure

- Kubernetes Administration : Deployments, Services, Secrets
- Containerisation : Gestion de conteneurs Docker
- Orchestration : Coordination de services multiples
- Networking : Port-forwarding et services Kubernetes

### Sécurité et Bonnes pratiques

- Gestion des secrets : Kubernetes Secrets vs variables hardcodées
- Principe de moindre privilège : Permissions AWS minimales
- Chiffrement : Base64 et protection des credentials
- Configuration sécurisée : Séparation code/configuration

### Cloud Computing (AWS)

- Stockage objet S3 : Buckets, policies, accès programmatique
- IAM : Création d'utilisateurs, policies, access keys
- CLI AWS : Automatisation et gestion par ligne de commande

### Bases de données

- PostgreSQL : Configuration et connection strings
- Docker databases : Déploiement de BD en conteneurs
- Intégration applicative : Connection MLflow-PostgreSQL

## Instructions de déploiement

### Prérequis

- AWS Account avec bucket S3 configuré
- Cluster Kubernetes (minikube) fonctionnel
- Docker installé et PostgreSQL déployé

### 1. Configurer les secrets

#Copier le template et remplir avec vos credentials

cp mlflow-secrets-template.yaml mlflow-secrets.yaml

#Éditer mlflow-secrets.yaml avec vos valeurs encodées en base64

kubectl apply -f mlflow-secrets.yaml

### 2. Déployer MLflow

kubectl apply -f mlflow-deployment.yaml

### 3. Accéder à l'interface

kubectl port-forward service/mlflow-service 8080:80

Interface disponible sur : http://localhost:8080

## Résultats obtenus

### Infrastructure production-ready

- MLflow accessible via interface web
- Stockage sécurisé des modèles sur S3
- Métadonnées persistées en PostgreSQL
- Scalabilité assurée par Kubernetes

### Sécurité renforcée

- Credentials protégés par Kubernetes Secrets
- Séparation des environnements
- Accès contrôlé aux ressources AWS

### Impact business pour Comcast

- Data Scientists peuvent tracker leurs expériences
- Équipes ML collaborent efficacement
- Modèles déployés à grande échelle
- Gouvernance des modèles centralisée

## Compétences transférables

Ces compétences sont directement applicables pour :

- MLOps Engineer : Infrastructure ML en production
- Data Platform Engineer : Architecture de données scalable
- DevOps Engineer : Orchestration Kubernetes
- Cloud Engineer : Solutions AWS multi-services
- Site Reliability Engineer : Monitoring et scalabilité

## Screenshots

Voir le dossier screenshots/ pour les captures d'écran de l'interface MLflow fonctionnelle.


## Data Engineering Exercise - MLflow Kubernetes Deployment
