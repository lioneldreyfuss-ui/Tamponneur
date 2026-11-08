# Le Tamponneur

Un outil gratuit pour avocats : il appose le numéro de pièce sur la première page de chaque PDF d'un dossier, en quelques secondes. Le numéro est lu directement dans le nom du fichier.

Ce dépôt contient le logiciel à télécharger et **la recette** : un texte à coller dans un assistant d'IA (Claude, ChatGPT…), qui fabrique l'outil pour vous. Vous gardez ainsi la maîtrise complète de ce qui s'exécute sur votre ordinateur.

## Ce que fait l'outil

* Vous déposez vos pièces PDF, ou un dossier entier.
* Il lit le numéro dans le nom de chaque fichier (« Pièce 12 - Contrat », « P3 », « 5 bis »…), que vous pouvez corriger.
* Il affiche un aperçu de la première page avec le tampon.
* Il tamponne toutes les pièces en un clic : numéro, nom de l'avocat, mention « Avocat », barreau.
* Forme, position, taille et couleurs du tampon sont réglables.

## Confidentialité

L'outil est un simple fichier qui s'ouvre dans votre navigateur. Vos pièces ne quittent jamais votre ordinateur : aucune IA et aucun serveur ne voient vos documents. L'IA intervient seulement pour fabriquer l'outil, à partir du texte ci-dessous, qui ne contient aucune donnée.

## Comment l'obtenir

1. Ouvrez Claude ou ChatGPT dans une nouvelle conversation. La version gratuite peut suffire, mais le résultat varie selon l'assistant.
2. Copiez le prompt ci-dessous avec le bouton de copie en haut à droite du bloc, et collez-le.
3. Enregistrez le fichier HTML que l'IA vous rend, puis ouvrez-le d'un double-clic.
4. Testez avec trois ou quatre **fausses pièces** : vérifiez les numéros, l'aperçu, et le fichier obtenu.

S'il reste un défaut, décrivez-le simplement à l'IA, dans la même conversation (« le tampon est à l'envers sur les pages en paysage »). Elle corrigera.

Pour plus de sécurité, vous pouvez ensuite demander à l'IA, dans une nouvelle conversation, de vérifier que le fichier n'envoie aucune donnée vers l'extérieur.

## Le prompt

```text
Je suis avocat. Fabrique-moi une petite application, « Le Tamponneur », sous la forme d'un seul fichier HTML que j'ouvre d'un double-clic dans mon navigateur, sur Windows ou sur Mac. Je ne veux rien installer.

L'application appose un tampon sur la première page de chacune de mes pièces PDF, pour les numéroter avant de les communiquer. Le numéro de chaque pièce se trouve dans le nom du fichier.

Mes pièces sont confidentielles : aucun fichier ne doit jamais quitter mon ordinateur. Tout le traitement se fait dans le navigateur, sans aucune intelligence artificielle ni aucun service en ligne.

Les choix techniques ci-dessous ont déjà été testés : applique-les tels quels, sans les discuter ni proposer d'alternative.

### Ce que l'application doit faire

- Ajouter les pièces en les glissant dans une zone prévue, ou avec deux boutons : « Choisir des fichiers » et « Choisir un dossier de pièces ». Un dossier entier doit être importé d'un coup, quel que soit le nombre de pièces. Les fichiers qui ne sont pas des PDF sont ignorés, avec un message.
- Lire le numéro dans le nom de chaque fichier. Exemples à reconnaître : « Pièce 12 - Contrat » donne 12, « P3 » donne 3, « 007\_attestation » donne 7, « Pièce 5 bis » donne 5 bis. Une date en début de nom (« 2024-03-12 courrier ») ou un nombre isolé (« rapport 2024 ») ne sont pas des numéros.
- Afficher la liste des pièces avec le numéro trouvé, que je peux corriger à la main. Une pièce sans numéro apparaît en rouge, un numéro en double en orange. Ma correction n'est jamais écrasée.
- Montrer un aperçu de la première page de la pièce sélectionnée, avec le tampon, qui se met à jour dès que je change un réglage.
- Régler le tampon : le libellé (par défaut « Pièce n° » suivi du numéro), mon prénom, mon nom (en majuscules par défaut), la mention « Avocat », et quelques lignes libres (barreau, toque). Je choisis aussi la forme (rectangle, rectangle arrondi, ovale), le coin de la page (en haut à droite par défaut), la taille, les marges, la taille du texte, l'épaisseur du trait et les couleurs (rouge par défaut). L'intérieur du tampon est transparent par défaut, avec une option pour un fond blanc. Mes réglages sont mémorisés d'une ouverture à l'autre.
- Tamponner toutes les pièces numérotées, en un clic, avec une barre de progression. Seule la première page de chaque pièce reçoit le tampon. Les pièces sans numéro sont ignorées, et je suis prévenu.
- Récupérer le résultat : si mon navigateur le permet (Chrome, Edge), je choisis un dossier de sortie et les pièces y sont enregistrées une par une, sous leur nom d'origine. Sinon, je reçois un fichier ZIP (ou le PDF directement s'il n'y a qu'une pièce). Chaque pièce reste aussi téléchargeable individuellement depuis la liste.
- Expliquer les problèmes en une phrase simple, sans message technique : fichier protégé par un mot de passe, fichier endommagé, fichier trop volumineux.

### À quoi elle doit ressembler

Une interface claire et sobre, digne d'un cabinet d'avocats, en français, sur fond gris très clair, avec des cartes blanches. Une seule couleur d'accent : le rouge d'un tampon encreur. Le nom « Le Tamponneur » est dessiné comme un tampon : lettres rouges en gras dans un double cadre rouge, légèrement penché.

En haut, un bandeau avec ce nom, une courte description, la mention « Traitement local, aucun fichier envoyé » avec un cadenas, et un témoin qui indique si le moteur est prêt.

En dessous, trois colonnes sur grand écran :

1. À gauche, les réglages du tampon, regroupés en quatre blocs : le contenu, la forme et la position (la position se choisit en cliquant sur un coin d'une petite page dessinée), le texte et les couleurs, et un bloc replié pour la détection du numéro. Cette colonne reste visible quand on fait défiler la page.
2. Au centre, les pièces : la zone de dépôt, puis la liste (numéro modifiable, nom du fichier, état, boutons pour télécharger ou retirer), puis le choix de la sortie, la barre de progression et le grand bouton rouge « Tamponner les pièces ».
3. À droite, l'aperçu de la page, en grand.

Sur un écran plus petit, l'aperçu passe sous les deux autres colonnes, puis tout s'empile.

Au démarrage, un écran d'attente indique que le moteur se prépare, avec une barre de progression et les étapes, puis disparaît. Les messages d'information et d'erreur apparaissent en petites fenêtres en haut à droite, qui disparaissent seules.

L'application doit rester utilisable au clavier et lisible par un lecteur d'écran.

### Choix techniques imposés

- Un seul fichier HTML, tout compris. Les seuls éléments chargés depuis Internet sont les outils suivants, dans ces versions exactes : Tailwind CSS 3.4.17, Pyodide 0.26.1 (depuis jsDelivr), la bibliothèque Python pypdf 6.21.2 (installée par micropip) et pdf.js 3.11.174 (depuis cdnjs, uniquement pour l'aperçu).
- Le traitement des PDF est écrit en Python et exécuté dans le navigateur par Pyodide. Utilise uniquement pypdf : pas de PyMuPDF, de reportlab ni de fpdf2.
- Le tampon est dessiné directement dans la page PDF, avec les polices standard Helvetica et Helvetica gras.
- Ajoute une politique de sécurité qui interdit au navigateur toute connexion, sauf le téléchargement de ces outils. Vérifie qu'elle ne bloque pas leur chargement.
- Les originaux ne sont jamais modifiés : le travail se fait sur des copies en mémoire.

### Pièges déjà rencontrés, à éviter

- Sur les pages tournées (scans en paysage, pages pivotées) et sur les pages dont la zone visible est décalée, le tampon doit apparaître droit et au bon coin, tel que je vois la page.
- Les accents et le symbole « ° » doivent s'afficher correctement dans le tampon.
- Le texte du tampon est centré et se réduit automatiquement s'il est trop long pour le cadre.
- Si je dépose un fichier à côté de la zone de dépôt, le navigateur ne doit pas l'ouvrir à la place de l'application.
- Quand je corrige un numéro, le champ ne doit pas perdre le curseur pendant la frappe.
- Un aperçu ancien ne doit jamais remplacer un aperçu plus récent.
- Certains PDF sont protégés sans mot de passe d'ouverture : ils doivent être traités normalement, en chargeant au besoin le module de déchiffrement de Pyodide. Ceux qui exigent un mot de passe sont signalés.
- L'aperçu doit fonctionner quand le fichier est ouvert depuis le disque (adresse en « file:// »), sans lancer de processus séparé pour pdf.js.
- Les noms de fichiers avec accents, espaces ou doublons ne doivent pas poser de problème : utilise des noms internes neutres, et ajoute « (2) » au nom de sortie en cas de doublon.
- Pour ménager la mémoire, ne charge une pièce qu'au moment de la traiter et libère-la aussitôt après.
- L'écran ne doit pas se figer pendant le traitement : la progression avance pièce par pièce.
- Aucun message technique brut ne doit s'afficher : les détails vont dans la console du navigateur.

### Ce que tu me rends

Le fichier le\_tamponneur.html complet, prêt à être ouvert d'un double-clic. Si tu peux exécuter du code, teste d'abord le traitement des PDF sur des pages normales et tournées.

Ajoute ensuite, en quelques lignes simples et sans jargon, ce que tu as vérifié et ce que tu n'as pas pu vérifier. 
```

## Précautions

* Faites vos essais avec de fausses pièces, jamais avec un dossier client.
* L'outil est fourni tel quel, sans aucune garantie. Vérifiez toujours vos pièces tamponnées avant de les communiquer : la responsabilité reste la vôtre.
* Un PDF signé électroniquement perd la validité de sa signature dès qu'il est tamponné.

## Vos retours

Un bug, une amélioration, un piège que l'IA n'a pas su éviter ? Ouvrez une [Issue](../../issues) sur ce dépôt. Chaque retour utile enrichira le prompt pour tout le monde.

## Licence

Ce texte est diffusé sous [licence MIT](LICENSE) : vous pouvez librement le réutiliser, le modifier et le partager, à condition de conserver la mention de l'auteur et de la licence.
