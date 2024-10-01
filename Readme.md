1. Planification des fonctionnalités

L'application aura les fonctionnalités suivantes :

    Inscription et connexion : Chaque étudiant doit pouvoir créer un compte et s'identifier pour accéder à l'application.
    Gestion des défis : Une interface qui affiche les défis disponibles, avec des informations comme le titre, la description, les points à gagner et la date de fin.
    Soumission de preuves : Les étudiants doivent pouvoir soumettre des preuves sous forme de texte, images ou vidéos pour valider un défi.
    Modération et validation des preuves : Un administrateur (par exemple, un membre de l'organisation de l'intégration) pourra valider ou rejeter les preuves soumises.
    Classement des promotions : Chaque promotion aura un tableau de points en fonction des défis validés par ses membres.
    Notifications : Envoyer des notifications push pour informer des nouveaux défis ou des résultats de validation de preuves.
    Commentaires et interactions (optionnel) : Les étudiants peuvent interagir sur les défis (likes, commentaires).

2. Choix des technologies

    Frontend (React Native) : Pour une application mobile multiplateforme (Android et iOS).
    Backend (Django) : Utilisation de Django REST Framework (DRF) pour construire une API RESTful.
    Base de données : PostgreSQL est recommandé pour sa compatibilité avec Django et sa fiabilité pour gérer des données structurées.
    Stockage de fichiers : Utilise Amazon S3 ou Django File Storage pour stocker les preuves soumises (images/vidéos).
    Notifications Push : Utilise Firebase Cloud Messaging (FCM) pour envoyer des notifications push.

3. Architecture de l'application
Backend (Django)

    Modèles :
        User : Utiliser le modèle d'authentification natif de Django ou l'étendre si nécessaire.
        Promo : Chaque étudiant appartient à une promotion.
        Challenge : Modèle qui contient les défis avec titre, description, date de fin, points à gagner.
        Proof (Preuve) : Les preuves soumises par les étudiants pour chaque défi.
        Score : Le score total de chaque promotion, mis à jour à chaque validation de preuve.
    Endpoints (API REST) :
        Auth : Inscription/Connexion avec JWT ou token.
        Challenges :
            GET : Liste des défis.
            POST : Soumission de preuves.
        Admin : Validation des preuves.
        Scores : Classement des promotions.

Frontend (React Native)

    Écrans :
        Login/Signup : Pour que les étudiants puissent s'enregistrer et se connecter.
        Challenge List : Affiche tous les défis disponibles pour la promotion actuelle.
        Submit Proof : Un formulaire pour soumettre une preuve pour un défi.
        Leaderboard : Affiche le classement des promotions.
        Admin Panel : Si nécessaire, un écran pour modérer les preuves.
