---
title:  Maki à la vapeur
date: 2013-10-25 00:00:42
tags:
---
Voici quelques nouvelles de mes projets libres. Au menu, nanimstudio, Newton Adventure, un nouveau jeu (Ned et les maki) et de nouveaux projets (libtiled-jaxb et lwjgl-nuit).

## nanimstudio

Mon logiciel d'animation 2d continue à évoluer au fil de mes besoins et des retours des utilisateurs. Après le support de l'APNG et quelques améliorations de l'ergonomie, mon prochain grand chantier est l'ajout d'algorithme de scaling. Pour cela j'utilise la bibliothèque scilter. Le but est de pouvoir prévisualiser les sprites tels qu'ils pourraient être affichés en jeu via des shaders implémentant des techniques d'agrandissement dédiées au pixel art (scale2x, hqx, rotsprite…).

[Site officiel](https://git.bci.im/nanim/)  
[scilter](https://github.com/kayahr/scilter)

## Newton Adventure

Mon projet le plus important continue sa carrière commerciale sur Greenlight. Il s'agit d'un système dédié aux jeux qui candidatent pour être vendu via la base de données sociale / plateforme de vente / adware / DRM / … préférée joueurs PC: Steam. Les clients peuvent voter pour dire s'ils seraient intéressés par l'achat d'un jeu candidat. A partir d'un certain nombre de vote et suivant des calculs et des critères internes à Valve, le jeu peut être accepté.

Si vous êtes du côté de Nice, je présente le jeu sur un stand au JM2L le mois prochain!

[Site officiel](https://play.bci.im/)  
[La page sur Greenlight](http://steamcommunity.com/sharedfiles/filedetails/?id=187107465)  
[Le site des JM2L](http://jm2l.linux-azur.org/)

## Ned et les maki

Si vous suivez linuxfr régulièrement, vous avez peut être vu que les [Geeky Goblin Productions](http://geekygoblin.org/) ou GGP ont passé une [annonce](http://linuxfr.org/users/aljes/journaux/gobelins-cherchent-geeks-pour-koala-masque) pour recruter des développeurs pour un projet de jeu. Je suis l'un d'eux!

La production a démarré sur les chapeaux de roue: on a déjà des graphismes, un petit moteur d'affichage, le gameplay est bien défini… J'espère même avoir une petite démo pour les JM2L!

Bien sûr comme dans tout projet libre, il a fallu faire des choix techniques et politiques difficiles. Heureusement l'équipe a l'esprit de compromis, ce qui nous a permis de faire rapidement les choix suivants:

### Moteur de jeu

La solution retenue est basée sur [Java](http://www.infoq.com/articles/javaone2013-roundup), [lwjgl](http://lwjgl.org/) et de gros bouts du code de Newton Adventure!

C++/SDL et Monogame ont été envisagé, mais le premier a dû être écarté pour des raisons de productivité et d'intérêt: j'ai fait valoir que les releases multiplateformes et la gestion des dépendances en C++ sont des tâches très consommatrices de temps et au niveau d'intérêt intellectuel proche de 0, ce qui est contraignant pour qui travaille sur son temps libre. Le second n'a pas été retenu à cause du rejet général de Mono par la communauté libre et de l'incertitude quant à son avenir après l'abandon de XNA par Microsoft (Monogame est une implémentation de XNA).

### Licences

Le choix des licences a été compliqué. Les GGP voulaient du Art Libre et seulement du Art Libre. Je voulais que le code soit sous BSD (pour pouvoir échanger du code avec mes autres projets) tandis l'autre développeur préférait MIT. Ce sera finalement MIT pour le code et Art Libre pour les données. La licence MIT permettant le sublicencing, les GGP pourront ainsi distribuer le jeu entièrement sous Art Libre!

### Outils pour le travail collaboratifs

git a été choisi pour partager les sources et gérer les versions. Là c'est plus une question de _personne n'a jamais été viré pour avoir choisi git_…

En attendant une mise à niveau du serveur des GGP, nous utilisons une instance de [gitlab](https://gitlab.pierre.marijon.fr/) et des dépôts sur [github](https://github.com/devnewton/ned-et-les-maki)

### Editeur de niveau

Le choix d'une vue en 3d isométrique nous a amené à choisir [Tiled](http://www.mapeditor.org/) pour l'édition des niveaux. Là aussi c'est un choix par défaut, car il n'y a pas beaucoup d'alternatives sur ce "marché".

## Nouveaux projets

Je profite du développement de Ned et les maki pour y faire "incuber" deux nouveaux projets de bibliothèques Java:

*   libtiled-jaxb: un parseur moderne pour les fichiers de Tiled. Ceux qui existent ont le gros défaut de charger les images avec java.awt ou android.graphics, ce qui ralentit considérablement le chargement des niveaux puisque ces API stockent les bitmaps dans des formats qu'il faut convertir en texture OpenGL. Ma bibliothèque laisse le jeu faire le chargement lui même.
*   lwjgl-nuit: une bibliothèque pour créer des interfaces graphiques pour les jeux écrits avec lwjgl. Il en existe déjà [plusieurs](http://lwjgl.org/wiki/index.php?title=Game_Engines_and_Libraries_Using_LWJGL#GUI_Libraries), mais aucune ne permets de contrôler l'interface uniquement avec une manette de jeu. Je joue souvent en utilisant mon PC comme une console, j'ai donc envie que mes jeux puissent être joués sans avoir à sortir un clavier et une souris.

{% asset_img nanim.jpg nanim %}
{% asset_img ned_et_les_maki.jpg Ned et les maki %}
{% asset_img newton_et_ned.jpg Newton et Ned %}