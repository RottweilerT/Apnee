# Apnée RottweilerT

Appli d'entraînement à l'apnée statique à sec : comptes, séances guidées (progressive, tables CO₂/O₂, essai record) avec signaux sonores, et historique avec courbe du record.

Site : https://rottweilert.github.io/Apnee/

- `index.html` : toute l'appli.
- Comptes et données : Firebase (projet `apnee-rottweilert`). Connexion par email/mot de passe ou Google ; chaque personne a ses données sous `users/{uid}` dans Firestore.
- `firestore.rules` : règles de sécurité à coller dans Firestore (onglet Règles). Chacun ne lit et n'écrit que ses propres données.
- Hors ligne : `sw.js` garde le site sur l'appareil ; Firestore garde les séances en attente et les envoie au retour du réseau.
- Les séances enregistrées dans le navigateur par l'ancienne version peuvent être importées depuis l'onglet Compte.
