---
title: Une tribune décentralisée est-elle possible?
date: 2013-01-25 19:04:06
tags:
---

J'ai récemment changé de système de chat pour mon site web pour une tribune. Avant j'utilisais le protocole [XMPP](http://xmpp.org/about-xmpp/) avec comme serveur [ejabberd](http://www.ejabberd.im/) et comme client [muckl_tribune](../../../projects/muckl_tribune/index/index.html), une variante de muckl que j'ai modifié pour émuler l'ergonomie d'une tribune, mais la complexité de la solution et le manque de temps m'ont conduit à adopter l'une des meilleures tribunes du marché, celle de [Drupal](http://drupal.org/project/tribune). J'en ai aussi profité pour migrer mon blog dotclear.

Ces migrations m'ont conduit à m'intéresser de plus près au monde des tribunes.

# Qu'est-ce qu'une tribune?

Voici la meilleure définition que j'ai trouvée:

    Une tribune (parfois appelée "shoutbox") est une application Web permettant à plusieurs utilisateurs de discuter : il s'agit d'un chat Web caractérisé par l'utilisation des standards HTTP et XML. Ainsi, afin de mettre en oeuvre un chat Web, une tribune expose une API HTTP permettant à plusieurs utilisateurs 1) de poster un message et 2) d'obtenir les derniers messages postés sous la forme d'un fichier XML appelé backend. [devmoules](http://halifirien.info/index.php?title=Tribune)

Les tribunes les plus célèbres sont [dlfp](https://linuxfr.org/board) et [euromussels](http://euromussels.eu/).

# La centralisation

Contrairement à d'autres systèmes tels que XMPP ou Retroshare à l'heure actuelle les tribunes sont centralisées: elles sont toujours liées à un site web auquel il est parfois obligatoire de s'y inscrire. C'est donc du pur Minitel 2.0 avec tous les abus possibles que cela implique (atteintes à la vie privée, censure...).

{% asset_img tribune.png tribune %}


Note: la partie serveur s'appelle _bouchot_ ou simplement _tribune_ et la partie cliente _coincoin_.


# La décentralisation

## Le principe

J'ai essayé d'imaginer ce que pourrait être un système de tribune décentralisée: ce qui m'a semblé le plus simple, c'est de considérer que chaque utilisateur aurait sa propre base de données contenant les messages. Régulièrement, les utilisateurs amis synchronisent leurs bases, important les messages des autres, exportant les leurs.

{% asset_img tribune_distribuee.png tribune %}


## Le prototype

Définir et synchroniser des bases de données n'est pas une mince affaire, heureusement j'ai eu l'idée d'utiliser un système de bases synchronisées que je connais bien, puisque je m'en sers pour gérer mes projets: [fossil](http://fossil-scm.org/), un logiciel basé sur [sqlite](https://www.sqlite.org/)qui combine gestionnaire de version, wiki et bugtracker.

Une fonctionnalité peu utilisée de fossil est la création d'évènement. J'ai "hacké" ce système pour m'en servir de stockage de messages et réduire mon prototype à deux scripts: un pour transformer la liste des évènements en backend xml, un autre pour recevoir un message et le transformer en évènement.

Testé avec mon coincoin préféré ([onlinecoincoin](http://olcc.logicielslibres.info/)), le prototype est une tribune tout à fait fonctionnelle. En clonant le dépôt, j'ai pu voir que l'on peut gérer plusieurs tribunes indépendantes et les faire se synchroniser par fossil.

## Conclusion

La centralisation des tribunes n'est pas une fatalité, le prototype le montre, même s'il a ses limites: il se base sur un "hack" de fossil, l'authentification n'est pas gérée, les norloges sont forcément UTC... Mais peut être qu'un jour un développeur de talent reprendra cette idée et deviendra riche et célèbre avec!