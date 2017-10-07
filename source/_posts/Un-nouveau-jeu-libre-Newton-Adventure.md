---
title: 'Un nouveau jeu libre : Newton Adventure'
date: 2010-01-02 07:32:31
tags:
---

La première démo jouable de [Newton Adventure](https://play.bci.im/) est sortie. Il s'agit d'un jeu de plates-formes 2D proche des classiques du genre en apparence, mais qui propose une nouveauté majeure : le personnage principal, Newton, a le pouvoir de modifier le sens de la gravité.

Cela permet de parcourir les niveaux dans tous les sens, d'atteindre des plates-formes inaccessibles, de faire tomber des objets ou des ennemis pour les atteindre, etc.

# La démo

La démo qui propose un niveau très simple, pour montrer le concept, a été testée sous Linux, mais devrait aussi tourner sous Windows, Mac OS X et Solaris. Un greffon pour Tiled permet de créer de nouveaux niveaux.

# Le développement

Techniquement, le jeu est écrit en Java avec les bibliothèques lwjgl pour l'affichage et phys2d pour la physique.

Les sources, fournies avec la démo, sont sous licence BSD tandis que les graphismes et les données du niveau relèvent de la Creative Commons BY-SA 3.0.

# Le développeur

Je réalise Newton Adventure sur mon temps libre et les vacances de fin d'année m'ont permis de bien avancer. J'espère pouvoir sortir dans l'année une version complète qui sera aussi amusante à jouer qu'à créer.

Pour l'instant je vais prendre un peu de recul et attendre les retours sur la démo, car j'ai beaucoup d'idée pour la suite et il va falloir faire le tri :

*   Framework pour ajouter des ennemis avec une IA sous forme de greffons ;
*   Objets utilisant le moteur physique : trampolines, cordes, pendules, rochers géants à la Indiana Jones, vent... ;
*   Des plates-formes particulières : glissantes, mobiles, déplaçables... ;
*   Musiques et effets sonores ;
*   Thèmes graphiques (jungle, ville...).

Enfin, j'aimerais porter le jeu sur téléphone mobile, mais je ne sais vraiment pas comment faire techniquement.