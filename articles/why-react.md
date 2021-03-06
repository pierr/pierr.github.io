# Pourquoi utilise-t-on React ?

Dans la communauté JavaScript, il existe de nombreuses **librairies** et **Frameworks** permettant d'abstraire et de simplifier la création de composants graphiques, d'application , ...

Parmi les plus connus il y a:

- jQuery, qui a permi la démocratisation du JavaScript à grande échelle.
- Backbone.js, qui est la première librairie qui a permis le développement d'application complète en JavaScript côté client. Aujourd'hui encore il s'agit de la librairie la plus utilisée en production. La première version de Focus chez Klee était construite autour de Backbone.js. Backbone repose sur trois grands principes: le model, la vue et le routeur. Il est très léger (environ 1000 lignes de code) et simple d'utilisation.
- Angular qui est géré par Google est un Framework complet qui est aujourd'hui un des plus connus
- Ember.js qui est une librairie open source
- React qui est une librairie créé par Facebook servant à créer des composants graphiques
- Polymer qui est une  librairie de web-components créé par Google.
- Cycle.js qui est une librairie avec une approche fonctionnelle construite autour de Rx.

Le but de cet article n'est pas de vous détailler les autres librairies mais plutôt d'expliquer pourquoi nous avons fait le choix de React.
Il faut noter qu'il n'y a pas de mauvais ou de bon choix, et que chaque librairie apporte des réponses différentes à différents problèmes.


## React repose sur des concepts très simples

Dans React tout est composant, un composant dispose des fonctionnalités suivantes:
- Il dispose d'un cycle de vie clair et défini
- Il a des propriétés d'entrée qui sont les `props` qui ne peuvent être mis à jour que par le composant parent
- Il a des propiétés internes qui sont dans le `state`, qui sont de la responsabilité du composant et ne peuvent pas être modifiées par l'extérieur.

// Il est également possible et recommandé de faire un maximum de composant sans state appelés composants `pures`.

> React est donc très simple à comprendre et à prendre en main pour des personnes débutantes.

![schema state props]()

## L'approche DOM virtuel


Les concepteurs de React sont arrivés avec le constat suivant: faire une application très riche avec beaucoup d'interactions en JavaScript est très complexe à faire et entraîne à long terme des problèmes de :

- Performance
- Maintenance
- Compréhension

Le problème de performance trouvait principalement sa source dans le fait que le DOM JavaScript est très lourd et complexe à manipuler.
Celui-ci est particulièrement visible sur les grosses applications.

Ils ont donc choisi de s'inspirer de ce qui se fait dans les moteurs de jeux vidéo. React fournit un DOM JavaScript dit 'virtuel' qui permet de calculer pour chaque changement d'état de nouveau DOM virtuel et applique les différences uniquement au DOM JavaScript réel.

> Les modifications sont appliquées par lot et on ne se pose pas la question de ce qui doit être modifié, on calcul le nouveau DOM, pas d'état de vue incohérent.
> Le DOM virtuel permet de créer des applications performantes et moins sujettes aux bugs dits d'état résiduel d'application.

![schema dom virtuel]()

## Le JSX

Avec toutes les librairies JavaScript, il y avait la possibilité d'utiliser un language de templating, plus ou moins imposé.
Le problème réccurent avec ce langage de templating était le fait de devoir créer des fonctions utilitaires afin d'arriver à créer ou recréer une manière de composer les données avec les éléments de markup (html).
React a eu une approche différente, le rendu du html devait être généré par du JavaScript, ceci offre toute la libertée au développeur de traiter les données avec le language qu'il maîtrise: le JavaScript.
Facebook a introduit le jsx qui est un mélange entre le HTML et le JavaScript, très simple à comprendre et à prendre en main. Il est simplement transformable en JavaScript.

> Le jsx bien qu'étrange et rebutant au premier abord est une des clef du succès et de l'adoption rapide de React.
> Aujourd'hui d'autres librairies comme cycle.js se base sur le JSX pour rendre le HTML.
> On peut même utiliser le jsx pour avoir une autre sortie que le HTML.
![schema jsx => js]()

## React s'utilise-t-il seul?

A l'inverse d'Angular qui est un framework proposant une stack complète, React est une librairie qui sert à créer des composants graphiques et pas plus. Il est recommandé de l'utiliser avec le pattern `flux` qui permet de mettre en musique les composants sur une application assez large.
C'est ce qui fait sa force, React repose sur des concepts simples et souple dans son utilisation.
> Il faut noter que React et Angular par exemple n'ont pas le même périmètre, React s'utilise avec d'autres librairies alors qu'angular impose une stack complète.

## Qui utilise cette librairie en production ?

Une des forces de React est le fait qu'avant d'être ouvert en open source, il a été développé et utilisé en interne chez Facebook. Cette librairie a donc été déployée à grande échelle en production avant d'être ouverte au monde.
La simplicité de React est le fait que cette librairie serve à une chose: créer des composants graphiques, a sucité une adoption immédiate par la communauté JavaScript.
Aujourd'hui React est utilisé par Netflix, Yahoo, Twitter, AirbnB, M6 web, Cana plus et même Klee Group...
A titre d'exemple aucune application google en production utilise angular.

> React dispose aujourd'hui:
> - d'une communauté très importante et grandissante. 
> - de retours très complets d'utilisation en production sur de grosses applications

## React est aujourd'hui un écosystème

React est à l'origine à destination du web. Mais l'abstraction du dom virtuel a permis l'émergence de nouvelles librairies à destination d'autres 'sorties'.
Facebook a donc séparé React en deux: React, le coeur et ReactDOM qui est le branchement au dom javascript.
Ils ont annoncé il y a maintenant un an et demie "React Native" qui utilise le coeur de React mais a pour sortie une application iOS ou une application Android native.
Attention cette solution est complètement différente de l'approche PhoneGap/ Cordova qui produisent une application web ambarquée dans une application native. Avec React Native on produit une vraie application native mais en utilisant les mêmes compétences utilisées pour développer une application web.
Encore une fois, cette librairie était utilisée par Facebook en interne avant d'être diffusée en open source et bénéficie d'une large adoption par la communautée. A titre d'information Google a annoncé qu'ils allaient sortir un adapteur pour Angular afin de gérérer du React native.
Il existe d'autres adapteurs react comme react vers WebGL, vers les Canvas, vers Ascii, ....

## Evolutions

React a une API très simple à prendre en main et également très stable dans le temps.
La roadmap est pilotée par Facebook et la communauté, l'objectif pour React est d'améliorer les performances et de se focailser sur l'écosystème.

> Merci d'avoir pris le temps de lire cet article, n'hésitez pas à faire des remarques ou commentaires et / ou à venir poser des questions si vous en avez.
> Un prochain article essairea d'expliquer Flux et les raisons de son utilisation.
