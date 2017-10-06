---
title: Jnuit, une bibliothèque pour créer des interfaces pour les jeux
date: 2014-05-17 23:26:42
tags:
---

J'ai créé jnuit, une bibliothèque pour créer des interfaces graphiques pour les jeux avec Java/lwjgl.

Pour créer mes jeux, j'ai suivi le conseil d'un article célèbre dans le milieu, [Write Games, Not Engines](http://scientificninja.com/blog/write-games-not-engines), qui explique en gros qu'il est beaucoup plus efficace de se concentrer sur la réalisation d'un jeu spécifique plutôt que de tenter de créer un moteur générique.

Ce principe m'a beaucoup aidé, mais aujourd'hui j'ai du mal à maintenir du code pour mes deux jeux, j'ai donc décidé de factoriser petits à petits leurs parties communes dans des bibliothèques réutilisables:

*   le chargement des niveaux créés avec [Tiled](http://www.mapeditor.org/): [libtiled-jpurexml](http://git.bci.im/libtiled-jpurexml).
*   la gestion des menus et des configuration: [jnuit](http://git.bci.im/jnuit/).

## jnuit

jnuit est une bibliothèque de composant pour la création d'interfaces homme-machine pour les jeux vidéos. Elle tient compte des contraintes suivantes:

*   un joueur peut utiliser un clavier, une souris, un écran tactile, une manette ou une combinaison des quatre.
*   les manettes peuvent être très différentes: joystick, gamepad, stick arcade… Le nombre d'axes, leurs orientations, le nombre de boutons sont très divers.
*   il faut s'intégrer dans la boucle d'évènement d'un jeu.

Pour cela, j'ai réalisé jnuit suivant un modèle très simple avec seulement quelques concepts:

*   widget: l'élément de base de l'interface.
*   layout: des widgets destinés à en contenir d'autres.
*   curseur: un focus sur un widget qui peut être déplacé.
*   peu d'événements: déplacement du curseur, "ok", "annuler".

Sur cette base, j'ai implémenté des widgets génériques (select, toggle, label…) et spécifiques (configuration des clavier/souris/manettes, réglages du son, changement de la résolution, de la langue…).

### Demo

Voici un exemple simple en image et en vidéo:

{% asset_link jnuit.webm Demo %}

#### Créer son propre jeu en une commande!

Cet exemple est ce que l'on obtient en utilisant [l'archetype maven](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html) que j'ai créé pour l'occasion et qui permets de démarrer un projet de jeu vidéo moderne (injection de dépendances, système d'entités, GUI complète, génération de paquets/installeurs pour la plupart des OS…) avec une simple commande:

    mvn archetype:generate -DarchetypeGroupId=im.bci -DarchetypeArtifactId=jnuit-archetype -DarchetypeVersion=LATEST -DgroupId=comycompagny.superbaryo2 -DartifactId=superbaryo2 -Dgame-name=superbaryo2 -Dgame-package=com.mycompagny.superbaryo2 -Dversion=1.0-SNAPSHOT

Ensuite pour apprendre l'api, il suffit de consulter les exemples et la javadoc (fournit avec les livrables récupérés par maven).

### Exemples de code

_Note: pour ces exemples, il faut considérer que l'on a déjà créé deux objets toolkit et root. Leur création étant dépendante de l'API graphique utilisée (pour l'instant seulement lwjgl, mais je prévoie des portages sur playn), je ne la détaille pas ici._

#### Hello world

    Label hello = new Label(toolkit, "Hello world!");
    root.show(hello);

#### Formulaire simple avec un layout de type "table"

        Table table = new Table(toolkit);
        table.setBackground(new ColoredBackground(0, 0, 0, 1));
        table.defaults().expand().fill();

        Label fruitsLabel = new Label(toolkit, "Do you like fruits?");
        table.cell(fruitsLabel);
        Toggle fruitsToggle = new Toggle(toolkit);
        table.cell(fruitsToggle);
        table.row();

        Label kindLabel = new Label(toolkit, "What kind?");
        table.cell(kindLabel);
        Select<String> kindSelect = new Select<String>(toolkit, Arrays.asList("banana", "apple", "orange"));
        table.cell(kindSelect);
        table.row();

        table.cell(new Button(toolkit, "quit") {

            @Override
            public void onOK() {
                System.exit(0);
            }
        }).colspan(2);

        table.layout();

        root.show(table);
