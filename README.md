# Bus 2D — guide de mise en ligne et création de l'APK

Contenu du dossier :
- index.html : le jeu
- manifest.webmanifest : informations de l'appli (nom, icônes, plein écran paysage)
- sw.js : mode hors ligne
- icons/ : icônes de l'appli

## Étape 1 — Mettre le jeu en ligne avec GitHub Pages

1. Connecte-toi sur github.com avec le compte kikigaming70.
2. Clique sur « + » en haut à droite, puis « New repository ».
3. Nom du dépôt : kikigaming70.github.io (exactement, c'est un nom spécial qui met le jeu à la racine
   de ton site, ce qui simplifie l'APK plus tard). Laisse-le en « Public ». Clique sur « Create repository ».
4. Sur la page du dépôt vide, clique sur « uploading an existing file ».
5. Dézippe ce dossier, puis glisse dans la fenêtre : index.html, manifest.webmanifest, sw.js
   ET le dossier icons (glisse le dossier lui-même pour garder son nom).
6. Clique sur « Commit changes ».
7. Va dans Settings > Pages. Sous « Build and deployment », choisis
   Source : « Deploy from a branch », Branch : main, dossier « / (root) », puis Save.
8. Attends 1 à 2 minutes. Ton jeu sera à l'adresse :
   https://kikigaming70.github.io/
   Ouvre-la sur ton téléphone pour vérifier qu'il se lance.

## Étape 2 — Installer sans APK (le plus rapide)

Sur Android, ouvre l'adresse dans Chrome, puis menu ⋮ > « Installer l'application »
(ou « Ajouter à l'écran d'accueil »). Le jeu apparaît avec son icône et se lance en plein écran.

## Étape 3 — Créer l'APK avec PWABuilder

1. Va sur pwabuilder.com et colle l'adresse du jeu, puis « Start ».
2. Vérifie que le manifeste et le service worker sont bien détectés.
3. Clique sur « Package for stores », puis « Android ».
4. Laisse les options par défaut (tu peux changer le nom du paquet, par exemple com.kikigaming70.bus2d)
   et lance la génération. Télécharge le zip obtenu.
5. IMPORTANT : garde précieusement dans le zip le fichier de clé de signature (.keystore)
   et son mot de passe. Sans eux, tu ne pourras plus mettre l'appli à jour.
6. Dans le zip, installe l'APK sur ton téléphone (autorise l'installation depuis une source inconnue).
   Le fichier .aab sert uniquement à publier sur le Play Store.

Remarque : pour que l'appli s'affiche sans barre d'adresse, PWABuilder te donne un petit fichier
« assetlinks.json » à déposer dans ton dépôt, dans un dossier nommé .well-known. Suis ses instructions.
Comme ton dépôt s'appelle kikigaming70.github.io, ce fichier sera bien à la racine de ton site.
(GitHub Pages ignore parfois les dossiers commençant par un point : si le fichier n'est pas accessible,
ajoute aussi un fichier vide nommé .nojekyll à la racine du dépôt.)

## Mettre à jour le jeu plus tard

Remplace index.html dans le dépôt GitHub, puis change le numéro VERSION dans sw.js
(par exemple bus2d-v2) pour que les joueurs reçoivent la nouvelle version.
