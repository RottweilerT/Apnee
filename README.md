# Apnée RottweilerT

Appli d'entraînement à l'apnée statique à sec : comptes, séances guidées (progressive, tables CO₂/O₂, essai record) avec signaux sonores, et historique avec courbe du record.

Site : https://rottweilert.github.io/Apnee/

- `index.html` : toute l'appli.
- Comptes et données : Firebase (projet `apnee-rottweilert`). Connexion par email/mot de passe ou Google ; chaque personne a ses données sous `users/{uid}` dans Firestore.
- `firestore.rules` : règles de sécurité à coller dans Firestore (onglet Règles). Chacun ne lit et n'écrit que ses propres données ; seul l'auteur d'un ticket peut le modifier ou le supprimer.
- Hors ligne : `sw.js` garde le site sur l'appareil ; Firestore garde les séances en attente et les envoie au retour du réseau.
- Les séances enregistrées dans le navigateur par l'ancienne version peuvent être importées depuis l'onglet Compte.
- Onglet Notes : tickets (idées, tâches, problèmes) partagés entre tous les inscrits, enregistrés dans la collection Firestore `tickets` avec `kind: "note"`.
- `.github/workflows/export-tickets.yml` : copie les tickets dans `tickets/tickets.json` toutes les heures (et à la demande). Lancée avec l'entrée « resoudre » (identifiants séparés par des virgules), elle passe d'abord ces tickets en Résolu.
- Mes séances : séances réglées et enregistrées sous un nom, dans `users/{uid}/programmes` (nom, réglages, favori, ordre).
- Réglages (bips, volume, vibrations, thème, respiration libre) : dans la fiche `users/{uid}.settings`, et copiés sur l'appareil.
- Menus d'actions : bouton ⋯, clic droit ou appui long sur une séance enregistrée, une séance de l'historique ou un ticket. Composants réutilisables en tête du script (`AM`, `actionsOn`, `dlg`, `confirmDlg`, `promptDlg`, `guarded`).
