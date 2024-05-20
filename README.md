# Welcome to Firebase

Nous allons ensemble apprendre à implémenter Firebase, le server side qui vous permettra de lancer vos mvp rapidement et de scaler vos outils.

## Qu'est ce que Firebase

Google décrit ça comme une plateforme de developpment ou vous pouvez rapidement créer des applications de haute qualité, engager les premiers utilisateurs et surtout être scalable. C'est ça la priorité lorsque l’on a un produit tech, c’est la scalabilité. Vous pouvez stocker vos données, les utilisés et faire des changements en temps réel, authentifier vos users, ajouter les push notifications (mobile & web), utiliser les outils d'analytics, pluguer des tonnes d'extension, facilité les paiements dans vos apps ... La liste est longue.

## Setup


Avant de commencer il faut initialiser un projet Firebase. Regardez cette [vidéo](https://firebasestorage.googleapis.com/v0/b/workshopfirebase-de30e.appspot.com/o/202405201205.mp4?alt=media&token=3b1769b7-c76b-4e93-b85d-a73c5568dc02).

Vous pouvez donner le nom que vous souhaitez. Il aura une importance pour la suite.


## Go pour la step 1 - Ajouter Firebase à votre page HTML



```HTML
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Test Firebase</title>
    <script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-app.js"></script>

    <script>
      const firebaseConfig = {
        apiKey: "your-api-key",
        authDomain: "your-project-id.firebaseapp.com",
        projectId: "your-project-id",
        storageBucket: "your-project-id.appspot.com",
        messagingSenderId: "your-sender-id",
        appId: "your-app-id"
      };

      const app = firebase.initializeApp(firebaseConfig);
      console.log("Firebase is connected successfully!");
    </script>
</head>
<body>
    <h1>Bienvenue sur votre page Firebase!</h1>
</body>
</html>

```

N'oubliez pas de remplacer les valeurs de firebaseConfig avec celles fournies par Firebase pour votre propre projet. Vous allez pouvoir retrouver toute les valeurs ci-dessous dont vous avez besoin dans la paramètre Firebase ([voir vidéo](https://firebasestorage.googleapis.com/v0/b/workshopfirebase-de30e.appspot.com/o/Screen%20Recording%202024-05-20%20at%2012.45.33.mov?alt=media&token=3522e063-33ab-4061-a76d-cb250e43b672))
```HTML
apiKey: "your-api-key"
authDomain: "your-project-id.firebaseapp.com",
projectId: "your-project-id",
storageBucket: "your-project-id.appspot.com",
messagingSenderId: "your-sender-id",
appId: "your-app-id"
```

Lancer votre page web et check la console.

## Step 2 - Un formulaire simple pour que les utilisateurs puissent saisir leur email et mot de passe pour s'inscrire


Cette partie se découpe en 2 parties : HTML et JAVASCRIPT. Un formulaire simple pour que les utilisateurs puissent saisir leur email et mot de passe pour s'inscrire. Je sais le html ça soule tout le monde donc je vous laisse le code: 

```HTML
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inscription Firebase</title>
    <script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-auth.js"></script>
</head>
<body>
    <h1>Inscription avec Firebase</h1>
    <form id="signup-form">
        <input type="email" id="email" placeholder="Entrez votre email" required><br>
        <input type="password" id="password" placeholder="Entrez votre mot de passe" required><br>
        <button type="submit">S'inscrire</button>
    </form>

    <script>
      
        // Rajouter la logique juste ici

    </script>
</body>
</html>
```

ps: n'oubliez pas de rajouter la balise -> <script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-auth.js"></script>


Voici les étapes du JavaScript:

1- Initialise Firebase avec vos configurations spécifiques.

2 - Ajoute un écouteur d'événements au formulaire d'inscription pour créer un utilisateur lorsque le formulaire est soumis.


3 - Utilise la méthode createUserWithEmailAndPassword pour créer un compte utilisateur avec les valeurs email et mot de passe fournies.

Besoin d'aide ? ([voir](https://www.youtube.com/watch?v=b1ULt_No3IY))


## Step 3 - Connexion et de déconnexion


Nous allons implémenter la fonctionnalité qui permet aux utilisateurs de se connecter avec leur email et mot de passe, et également de se déconnecter. Same, prenez le HTML me remerciez pas et ajoutez votre logique.


```HTML
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Connexion et Déconnexion Firebase</title>
    <script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-auth.js"></script>
</head>
<body>
    <h1>Connexion avec Firebase</h1>
    <form id="login-form">
        <input type="email" id="login-email" placeholder="Entrez votre email" required><br>
        <input type="password" id="login-password" placeholder="Entrez votre mot de passe" required><br>
        <button type="submit">Se connecter</button>
    </form>

    <button id="logout-button" style="display:none;">Se déconnecter</button>

    <script>

    //Ajouter votre logique ici

    <script\>
</body>
</html>
```

Ça devient un peu tricky. Voici le résumez du fonctionnement: 

#### HTML : 

Un formulaire de connexion pour que les utilisateurs puissent saisir leur email et mot de passe, et un bouton de déconnexion.

#### JavaScript :
Connexion : Un écouteur d'événements est ajouté au formulaire de connexion. Lorsque le formulaire est soumis, la méthode signInWithEmailAndPassword est utilisée pour connecter l'utilisateur.

Déconnexion : Un écouteur d'événements est ajouté au bouton de déconnexion. Lorsque ce bouton est cliqué, la méthode signOut est utilisée pour déconnecter l'utilisateur.
Le bouton de déconnexion est initialement caché et s'affiche uniquement lorsque l'utilisateur est connecté.

Doc Firebase est magique je vous laisse vous y refferrer.


## Step 4 - Enfin, le stockage avec Firestore

Pour intégrer les fonctionnalités de connexion et déconnexion et le stockage de données dans Firestore, on va 
 commencer par ajouter un formulaire de connexion à la page. Cela garantira que les utilisateurs doivent être connectés pour ajouter et visualiser des données.


```HTML
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Connexion et Gestion de Données Firestore</title>
    <script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-auth.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-firestore.js"></script>
</head>
<body>
    <h1>Connexion pour accéder à Firestore</h1>
    <form id="login-form">
        <input type="email" id="login-email" placeholder="Entrez votre email" required><br>
        <input type="password" id="login-password" placeholder="Entrez votre mot de passe" required><br>
        <button type="submit">Se connecter</button>
    </form>

    <button id="logout-button" style="display:none;">Se déconnecter</button>

    <div id="data-interface" style="display:none;">
        <h1>Stockage de données avec Firestore</h1>
        <form id="data-form">
            <input type="text" id="user-name" placeholder="Entrez votre nom" required><br>
            <button type="submit">Sauvegarder</button>
        </form>

        <h2>Utilisateurs enregistrés :</h2>
        <ul id="user-list"></ul>
    </div>


    <script>

       //Ajouter votre logique ici

    <script\>


</body>
</html>
```

#### Pour le process c'est assez simple: 


1. Formulaires de connexion et de déconnexion : Permettent aux utilisateurs de se connecter et se déconnecter.

2. Interface de données : Visible uniquement lorsque l'utilisateur est connecté, permettant d'ajouter et visualiser des données dans Firestore.

3. Gestion des utilisateurs : L'utilisateur doit être connecté pour interagir avec Firestore, assurant ainsi une couche de sécurité.

Encore une fois il y a des tonnes de doc en ligne ([voir 1](https://www.freecodecamp.org/news/the-firestore-tutorial-for-2020-learn-by-example/), [voir 2](https://stackoverflow.com/questions/70919326/adding-documents-to-firestore-using-javascript), [voir 3](https://www.youtube.com/watch?v=2yNyiW_41H8))


