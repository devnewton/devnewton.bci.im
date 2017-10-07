---
title: Newton Adventure 1.2
date: 2012-02-09 17:13:28
tags:
---

Voici une nouvelle version de Newton Adventure, le jeu de plateforme 2D libre pour Linux, Windows ou Mac OS X qui vous permet de changer la gravité et faire tourner les niveaux à 360°

{% asset_img montage.jpg montage %}

## Les nouveautés

### Musiques

Grâce à , j'ai pu ajouter des musiques pour tous les niveaux et écrans du jeu.

### Scores

A la fin de chaque quête, un score est attribué au joueur. Ce score peut être envoyé au [serveur de score](https://git.bci.im/scoreserver/), soit en anonyme, soit avec un nom de joueur à configurer dans les options du jeu.

Le score est déterminé par le nombre pommes reçues ou perdues, les niveaux traversés, les ennemis tués et les pièces collectées.

### Niveaux bonus

Pour ajouter une possibilité pour faire un highscore, j'ai ajouté un ensemble de niveaux bonus. Ceux-ci sont accessibles en collectant toutes les pommes d'un niveau et en trouvant un téléporteur. Dans les niveaux bonus, il n'est plus possible d'utiliser le changement de gravité, il faut donc utiliser des plateformes mouvantes ou rebondissantes pour collecter un maximum de pièce en moins d'une minute.

### Menu d'options

Jusqu'ici Newton Adventure n'était configurable qu'en éditant un fichier et en relançant le jeu. Un menu d'options est maintenant accessible depuis l'écran d'accueil.

### Portage sur Android en cours

J'ai commencé un portage sur Android, il fonctionne peut être, mais ne possédant pas un téléphone de ce type, je n'ai pu le tester qu'avec l'émulateur fourni par Google. Malheureusement ce dernier est si lent qu'il est impossible de faire un développement OpenGL sérieux avec... N'hésitez à faire un don pour que je puisse m'en offrir un :-)