---
title: Newton Adventure 1.11
date: 2013-08-27 11:36:42
tags:
---

J'ai publié une nouvelle version de Newton Adventure, un jeu de plateforme 2D libre pour Linux, Windows ou Mac OS X.

Le but du jeu consiste à parcourir des niveaux en courant, sautant et faisant tourner la gravité. Pour passer au niveau suivant, il faut trouver une clef et l'amener à la porte de sortie en évitant les nombreux pièges et enemis.

## Nouveautés

Les nouveautés de cette version sont:

*   une refonte du menu d'options avec un nouveau thème ;
*   l'utilisation d'une base de données de manettes de jeu pour les configurer automatiquement ;
*   le partage des scores via [scoreserver](https://git.bci.im/scoreserver/) est désormais inactif par défaut. Je ne pourrais plus calculer de statistiques pertinentes, mais c'est un choix plus logique pour le respect de la vie privée ;
*   le passage à la version 2.9.0 de la bibliothèque [lwjgl](http://www.lwjgl.org/), équivalent Java de SDL ou SFML utilisé par la plupart des jeux écrits dans ce langage comme le célèbre Minecraft ;
*   des optimisations qui permettent de rendre le jeu à peu près jouable sur un netbook atom avec GPU intel.

## Debian

J'ai fait un effort particulier sur l'empaquetage pour debian : j'ai créé une branche spéciale afin que le paquet .deb ne dépende plus désormais que de bibliothèques et logiciels présents dans la distribution stable.

## Cherche contributeurs sérieux

Outre les contributions les plus simples (traductions, rapports de bugs…), je cherche des développeurs Android/iOS/consoles pour réaliser des portages sur d'autres plateformes.

{% asset_img screenshot.png Screenshot %}