---
title: Nouvelles versions natives de Newton Adventure
date: 2019-11-16 14:57:34
tags:
---

Les nouvelles version de [l'openjdk](https://adoptopenjdk.net/)
permettent facilement de l'embarquer pour éviter aux utilisateus d'avoir
à installer Java.

Cela m'a permit de créer deux nouvelles versions natives pour Linux
et Windows de mon jeu [Newton Adventure](https://play.devnewton.fr/).

La version Linux utilise [AppImage](https://appimage.org/). Cet outil
génère un exécutable qui embarque tout: jar, données, jdk. Il suffit de 
le télécharger, de le rendre exécutable (chmod +x) et de le lancer.

La version Windows est un installeur construit par
[NSIS](https://nsis.sourceforge.io).

N'ayant pas de Mac, je n'ai pas tenté de faire une version pour cet OS,
mais les apple fanboys pourront utilisé le jar exécutable à condition
d'avoir préalablement installé [l'openjdk 11](https://adoptopenjdk.net/).

Liens:

 * [Le jeu](https://play.devnewton.fr/)
 * [Source AppImage](https://github.com/devnewton/newton_adventure.appimage)
 * [Source NSIS](https://github.com/devnewton/newton_adventure.exe)
