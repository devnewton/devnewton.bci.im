---
title: Grand nettoyage d'hiver
date: 2013-02-23 14:11
tags:
---

J'ai fait un gros nettoyage du code de Newton Adventure:

*   Il est maintenant plus facile pour les graphistes de contribuer.
*   Le portage android a été supprimé en attendant de trouver un développeur pour le faire renaître.
*   La version Java Web Start est abandonnée.

# Plus facile la contribution

Le grand changement est une meilleure utilisation des fichiers: avant un fichier *.tmx contenait toutes les informations, images comprises, ce qui rendait pénible leur édition, car pour éditer une tuile, il fallait l'extraire via l'éditeur de niveau, l'éditer avec gimp (par exemple), puis la réintégrer via l'éditeur. Pour voir les changements en jeu, il fallait aussi systématiquement recompiler. Ce fonctionnement était nécessaire pour le portage android où on n'a pas accès à vrai système de fichier.

Maintenant le jeu stocke ses données dans un sous dossier data/ qui contient toutes les images au format png. On peut les éditer et lancer le jeu pour voir les changements directement.

J'ai fait l'essai avec ce bonhomme de neige dessiné par [Julien Jorge](http://julien.jorge.free.fr/):

{% asset_img snow.jpg snow %}

# La fin du portage android

Il est toujours resté à l'état de prototype, je n'ai pas beaucoup de temps pour m'en occuper et il faudrait sans doute une réécriture plutôt qu'un portage pour s'adapter à ces petites machines. Je pense qu'il vaut mieux essayer de recruter un développeur motivé pour faire une vraie version mobile/tactile de Newton Adventure en reprenant juste les données et en faisant un code neuf avec son langage et ses apis préférés.

# Java Web Start aux oubliettes

Java Web Start est une très bonne idée pour déployer des applications simplement, malheureusement ce n'est pas trop compatible avec l'utilisation de bibliothèques natives et de certificats SSL autosignés: l'utilisateur voit des messages d'avertissements trop dissuasifs...