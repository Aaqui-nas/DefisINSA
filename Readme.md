# Application de Défis pour Étudiants

## Description

Cette application permet aux étudiants de participer à des défis en soumettant des preuves (texte, images ou vidéos), de recevoir des notifications, et de suivre le classement de leur promotion. Un administrateur pourra valider ou rejeter les preuves soumises, et un système de points permet de déterminer la promotion gagnante.

## Fonctionnalités

L'application intègre les fonctionnalités suivantes :

1. **Inscription et connexion** :

   - Chaque étudiant peut créer un compte et s'identifier pour accéder à l'application.

2. **Gestion des défis** :

   - Interface affichant les défis disponibles, avec des informations telles que le titre, la description, les points à gagner et la date de fin.

3. **Soumission de preuves** :

   - Les étudiants peuvent soumettre des preuves sous forme de texte, images ou vidéos pour valider un défi.

4. **Modération et validation des preuves** :

   - Un administrateur peut valider ou rejeter les preuves soumises.

5. **Classement des promotions** :

   - Un tableau de points est mis à jour en fonction des défis validés par les membres d'une promotion.

6. **Notifications** :

   - Notifications push pour informer des nouveaux défis ou des résultats de validation de preuves.

7. **Commentaires et interactions (optionnel)** :
   - Les étudiants peuvent interagir sur les défis via des likes et des commentaires.

## Choix des Technologies

L'architecture technique repose sur les outils suivants :

- **Frontend** : [React Native](https://reactnative.dev/)

  - Application mobile multiplateforme (iOS et Android).

- **Backend** : [Django](https://www.djangoproject.com/)

  - API RESTful construite avec Django REST Framework (DRF).

- **Base de données** : [PostgreSQL](https://www.postgresql.org/)

  - Gestion des données structurées.

- **Stockage de fichiers** :

  - Utilisation de [Amazon S3](https://aws.amazon.com/s3/) ou Django File Storage pour stocker les fichiers (images/vidéos).

- **Notifications Push** :
  - Utilisation de [Firebase Cloud Messaging (FCM)](https://firebase.google.com/docs/cloud-messaging) pour les notifications push.

## Architecture de l'Application

### Backend (Django)

#### Modèles

- **User** : Modèle d'authentification natif de Django (extensible si nécessaire).
- **Promo** : Chaque étudiant appartient à une promotion.
- **Challenge** : Modèle contenant les défis avec titre, description, date de fin, points à gagner.
- **Proof (Preuve)** : Preuves soumises par les étudiants pour chaque défi.
- **Score** : Score total de chaque promotion, mis à jour à chaque validation de preuve.

#### Endpoints (API REST)

- **Auth** :

  - Inscription/Connexion avec JWT ou token.

- **Challenges** :

  - `GET /challenges` : Liste des défis.
  - `POST /challenges/:id/proofs` : Soumission de preuves.

- **Admin** :

  - Validation et rejet des preuves.

- **Scores** :
  - Classement des promotions.

### Frontend (React Native)

#### Écrans

- **Login/Signup** : Permet aux étudiants de s'enregistrer et de se connecter.
- **Challenge List** : Affiche tous les défis disponibles pour la promotion actuelle.
- **Submit Proof** : Formulaire pour soumettre une preuve pour un défi.
- **Leaderboard** : Affiche le classement des promotions.
- **Admin Panel** : Interface pour modérer les preuves (si nécessaire).

## Installation et Configuration

### Prérequis

- **Node.js** : Version 12 ou supérieure.
- **Python** : Version 3.8 ou supérieure.
- **PostgreSQL** : Version 12 ou supérieure.

### Étapes d'installation

1. **Cloner le projet** :

   ```bash
   git clone https://github.com/Aaqui-nas/DefisINSA.git
   cd DefisINSA
   ```

2. **Backeng (Django)** :
   - Créer un environnement virtuel et installer les dépendances :
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

   - Appliquer les migrations :
   ```bash
   python manage.py migrate
   ```

   - Lancer le serveur :
   ```bash
   python manage.py runserver
   ```

3. **Frontend (React Native)** :
   - Installer les dépendances :
   ```bash
   npm install
   ```

   -Lancer l'application sur un émulateur ou un appareil :
   ```bash
   npx react-native run-android # Pour Android
   npx react-native run-ios     # Pour iOS
   ```