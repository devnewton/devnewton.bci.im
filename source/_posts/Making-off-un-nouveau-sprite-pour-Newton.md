---
title: 'Making off: un nouveau sprite pour Newton'
date: 2012-12-27 00:21:45
tags:
---

{% asset_img newnewton.jpg newnewton %}

Le jeu que je développe, [Newton Adventure](http://newtonadventure.bci.im/), utilisait jusqu'ici un sprite sans rapport avec le thème du jeu.

{% asset_img oldnewton.jpg oldnewton %}

J'ai décidé de m'attaquer à la réalisation d'un personnage ressemblant à Newton à l'aide des logiciels libres suivant:

*   [gimp](http://www.gimp.org/) pour le dessin et la retouche d'image.
*   [nanim](https://git.bci.im/nanim/) pour la création de l'animation.
*   [imagemagick](http://www.imagemagick.org/) pour la création du gif animé visible à la fin du billet.

Voici la procédure que j'ai suivi.

Première étape, faire un dessin grossier au crayon:

{% asset_img sketch1.jpg sketch1 %}

Deuxième étape, scanné et utiliser des filtres (Dessin au crayon, nettoyer...) pour avoir un contour net:

{% asset_img sketch2.jpg sketch2 %}

Troisième étape, réduire la résolution et faire un coloriage rapide:

{% asset_img newton_64x64_color.png newton_64x64_color %}

Quatrième étape, réduire encore la résolution et faire essayer de faire juste ressortir les détails importants:

{% asset_img newton_32x32_montage.png newton_32x32_montage %}

Pour cela il est indispensable de bien configurer gimp. J'ouvre deux vues sur la même image, l'une avec un zoom important, l'autre en taille réelle et qui n'affiche pas les sélections ou bords de cadre. Je mets aussi un calque d'une couleur que je n'utilise pas pour faire bien ressortir les contours.

{% asset_img gimp_config.png gimp_config %}

Enfin, il faut recommencer pour toutes les positions clefs de l'animation:

{% asset_img newton_montage.png newton_montage %}

Avec le sdk de nanim, la commande suivante permets de créer l'animation:

    nanimenc -author devewton -license "CC-BY-SA 3.0" -d 100 -a stay -f newton_03.png -a walk -f newton_03.png -f newton_04.png -f newton_05.png -f newton_04.png -f newton_03.png -f newton_02.png -f newton_01.png -o hero.nanim

Pour obtenir le gif, il faut utiliser la commande convert d'imagemagick:

convert -delay 10 -dispose Background newton_03.png newton_03.png newton_04.png newton_05.png newton_04.png newton_03.png newton_02.png newton_01.png hero.gif

Et voilà le résultat:

{% asset_img hero.gif hero %}