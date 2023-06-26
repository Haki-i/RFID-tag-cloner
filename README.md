# RFID-tag-cloner

# **Objectif du projet**

L’objectif est d’élaborer un boitier dans lequel est caché un module RFID pour enregistrer automatiquement des cartes qui seraient posées dessus.

# I- **Conception electronique**

Pour concevoir le projet, j’ai opté pour l’utilisation d’une carte Nodemcu car je disposais d’un câble micro USB C plus petit et plus souple que celui d’une carte Arduino Nano.

## a) Alimentation de la carte

Pour pouvoir alimenter la carte via le port micro USB C de la Nodemcu j’utiliserai un support de pile 6V dont les fils électriques sont déjà soudés, ainsi qu’un mini module PCB USB femelle afin de pouvoir envoyer le courant des piles vers le câble USB de la Nodemcu.

Il faut ensuite pouvoir contrôler lorsqu’on le souhaite l’allumage de la carte grâce à un bouton levier.

- On soude le pôle positif des piles au bouton
- On soude l’autre broche du bouton vers le Vbus du module femelle USB. Le courant ne passe que si le levier est actionné.
- On soude le pôle négatif des piles vers le GND du module USB femelle

## b) Module RFID et Led indicatrices

Pour brancher le module RFID à la carte :


![Node](https://user-images.githubusercontent.com/92324336/146691266-ae3609b8-8e0a-4d49-b65d-4e3708bf275e.png)

[https://github.com/bernardo-amaral/nodemcu-rfid](https://github.com/bernardo-amaral/nodemcu-rfid)

On branche également une led RGB sur 3 différents pins pour obtenir trois couleurs indiquant l’avancée de la copie depuis l’extérieur.

# II- **Conception informatique**

Pour mettre au point un copieur de carte RFID automatique, nous utilisons le code d’exemple fourni avec la bibliothèque RFID.

Après modification de ce code pour nos besoins, le programme enchaine infiniment et successivement ces évènements :

- Allumage de la Led en rouge et attente d’une carte à copier sur le lecteur
- Détection d’une carte puis copie de celle-ci.
- Allumage de la led en bleu et attente d’une carte programmable
- Détection de la 2nd carte puis copie des éléments dans celle-ci
- Allumage de la led en vert 3 secondes puis en rouge

Si un traitement n’est pas correctement réalisé, l’étape en cours recommence.

L’objectif est à la fois d’inscrire dans le nouveau badge l’UID de celui copié (bloc 0) mais également de copier l’intégralités des autres informations des autres autres blocs pour avoir une copie quasi identique.

# III- **Conception 3D**

La boite dans laquelle se trouvera notre copieur de badge est séparée en deux parties :

- Une zone de rangement de tous les modules avec les trous pour la led et le bouton
- Une zone sans composant qui permettra de tromper la cible
- Chaque bloc est fermable avec un couvercle

![IMRPIMANTE](https://user-images.githubusercontent.com/92324336/146691290-49cc0106-2397-4397-b905-647404c3f901.png)

# **Rendu final**


![image](https://user-images.githubusercontent.com/92324336/232253774-a1dc0e81-347e-4c3f-b945-107a781e6ace.png)

