---
title: Chronokiwi sort en version d3b63be4cb
date: 2011-11-02 23:10
tags:
---

Mon projet Chronokiwi, le wiki spécialisé dans la saisie et la présentation d'évènements et de chronologies écrit avec Django sous licence BSD, évolue.

La dernière version était assez basique, mais aujourd'hui commence vraiment à prendre forme grâce aux nouveautés suivantes:

*   liens entre les pages des évènements et les chronologies via une extension de la syntaxe Markdown.
*   flux RSS.
*   export de chronologies sous forme d'un graphe (via Graphviz)
*   géolocalisation des évènements via GeoDjango et Openlayers.

La prochaine fonctionnalité importante que j'aimerais implémenter est une "timeline" visuelle intégrée avec une carte afin de pouvoir, par exemple, visualiser de façon interactive l'évolution d'une invasion.

J'aimerais aussi améliorer la partie cartographique, mais je suis assez limité par les versions de Django et GeoDjango proposées par ma distribution. Apparemment les développeurs Python modernes se font des "virtualenv" et des "pip" pour résoudre ce genre problème, mais je n'ai pas eu le temps d'explorer le sujet.

*   [Page du projet](http://chiselapp.com/user/devnewton/repository/chronokiwi)

{% asset_img chronokiwi.jpg chronokiwi %}
