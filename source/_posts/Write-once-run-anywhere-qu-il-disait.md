---
title: 'Write once, run anywhere qu''il disait'
date: 2012-12-03 11:20:27
tags:
---

Ces derniers jours, j'ai travaillé sur le packaging de [Newton Adventure](https://play.bci.im/) et ce n'est pas de tout repos!

Voici un résumé de mes recherches sur le sujet.

# Du simple zip...

Jusqu'ici je distribuais une simple archive au format zip contenant l'exécutable java du projet, cad un fichier jar, ainsi que les bibliothèques dont il dépend: certaines sont aussi écrites en java, ce sont donc aussi des jars, d'autres sont des bibliothèques natives destinées à accéder au matériel graphique via OpenGL ou sonore via OpenAL.

La production d'un jar exécutable est difficile, mais pas insurmontable: il faut indiquer à Java où sont les bibliothèques. Pour les jars, il faut jouer avec maven, le  
programme utilisé pour compiler le projet, tandis que du code spécifique  
doit être écrit pour trouver les bibliothèques natives.

Toutefois ce mode de distribution pose plusieurs problèmes:

*   beaucoup d'utilisateurs ne savent pas décompresser une archive.
*   aucun raccourci dans le menu de l'environnement de bureau n'est créé automatiquement et avec certain (Unity par exemple), c'est très difficile de le faire à la main.
*   sur la plupart des PC, lorsque l'utilisateur double clique sur un jar, cela ouvre un gestionnaire d'archive au lieu d'exécuter le programme.

Sur ce dernier point, les environnements de bureau sont les grands coupables de ce comportement simple, mais stupide: combien d'utilisateurs veulent par défaut voir les entrailles d'un programme java plutôt que de l'exécuter? C'est aussi idiot que d'ouvrir par défaut les exécutables avec un éditeur hexadécimal.

Changer les associations de fichier étant souvent très compliqué, je distribue des batchs pour aider l'utilisateur à lancer le programme, mais là aussi les fichiers batchs s'ouvrent souvent avec un éditeur de texte sur la plupart des machines. Avec Windows, c'est le top: la commande java est souvent  inaccessible, l'exécution d'un batch provoque parfois des popups d'alertes...

# ... au paquet d'installation

Pour simplifier la vie des utilisateurs, j'ai décidé de créer des paquets pour les différents OS.

## Debian

J'ai commencé par debian, puisque l'OS que j'utilise est basé dessus. Les dépendances que j'utilise (lwjgl, phys2d, twl...) n'étant pas dans les paquets de cette distribution, j'ai fait un "gros deb", cad en embarquant toutes mes dépendances. Généré via maven par l'excellent plugin [jdeb](https://github.com/tcurdt/jdeb), ce paquet pourra servir de base de travail à de vrais empaqueteurs debian. J'ai découvert à cette occasion que la création de deb est un art difficile et je comprends mieux <del>le manque de paquets à jour</del> le travail titanesque que font les contributeurs debian.

## Les autres

Pour les autres OS, j'ai fait appel à [izpack](http://izpack.org/), un logiciel qui crée des installeurs clickodromes multiplateformes. Un peu difficile d'accès, mais disposant d'un plugin maven, il me permet de créer facilement des installations de qualité (sauf pour Macosx, où ce n'est pas aussi bien qu'un .app).

Ecrit en java, izpack génère un jar exécutable, il y a donc toujours le défaut des environnements de bureau décrit au début. Pour Windows, j'ai pu venir à bout de ce problème à l'aide d'un autre logiciel / plugin maven, [launch4j](https://github.com/cvgaviao/launch4j) qui transforme un jar en exe.

# Et Java Web Start?

Java Web Start est une technologie qui permets en cliquant sur un lien d'installer ou mettre à jour automatiquement une application Java et de créer un raccourci sur toutes les plateformes où tourne Java. Génial en apparence, elle a de gros défauts: une fois encore, l'association entre l'extension (jnlp) et le programme javaws n'est pas effective sur beaucoup de PC et l'utilisation de bibliothèques natives provoquent l'affichage de popups d'alerte à faire fuir  le plus intrépide des utilisateurs.

# Conclusion

Le packaging d'applications multiplateformes, est une tâche complexe, mais indispensable pour toucher un large public. La charge est importante pour les développeurs de logiciel et c'est autant de temps perdu pour la correction de bug ou l'ajout de fonctionnalités.

J'espère qu'à l'avenir les environnements de bureau travailleront le support des programmes créés avec des outils de développement portables, car Java n'est pas le seul touché, afin de faciliter la vie des utilisateurs et des développeurs.