# React Europe 2016


L'année dernière je m'étais rendu à la promière conférence sur React en europe et avait déjà réalisé un premier compte rendu: [react-europe-2015](https://gist.github.com/pierr/639b994534924c75f7e6)
Cette conférence avait été le théâtre de plusieurs annonces majeures: [Redux](), la spec de [GraphQL](), l'annonce su support proche d'Android pour React Native et Relay.
C'est donc très enthousiaste que je me suis rendu à l'édition 2016 de la React Europe.


## Keynote par [@dan_abramov](https://twitter.com/dan_abramov) aka le dieu du JS

Comme Dan Abramov a annoncé redux l'année dernière lors de la précédente édition de la React europe, il a souhaité faire un retour d'expérience sur Redux.
Redux c'est :
 - Flux + Elm
 - 3 millions de downloads sur npm
 - Une utilisation massive: Twitter mobile, Facebook F8, Netflix, 
 - Une API core résumable en 15 lignes de code
 Ensuite il est revenu sur la clef du succès d'une librairie: trouver l'équilibre entre contrainte | fonctionnalités |contrat et API. Pour lui (ça semble logique) une contraintre doit être socialement utile, et l'important est la composabilité.
Il est revenu sur le fait d'avoir **marquetté** sa librairie: documentation, twitter, github et screencast sur egghead.

> Cette Keynote était très interessante mais à mon sens ce n'était pas une keynote mais un talk comme un autre.
> Ce retour d'expérience qur redux était cependant très intéressant, il m'a conforté dans le choix de redux pour les extensions et la prochaine version du form.

## Navigation native pour toutes les plateformes par [Eric Vicenti](https://twitter.com/ericvicenti)

Son objectif est de résoudre le problème de la navigation entre application native, le web et intra application.
Il a commencé par montrer comment structurer son code avec redux afin d 'avoir des modules applicatifs complètements indépendants.
En gros il y a un manager d'url externe et plusieurs reducer indépendants qui contiennent une possibilité de commiquer avec un hub de navigation.
Il a ensuite réalisé une démo d'intégration d'une extention de chat au sein de plusieurs applications natives.
> Ce talk était intéressant au début pour les principes exposés ainsi que par les problèmes qu'ils cherchent à résoudre.
> En revanche le présentateur s'est embarqué dans une explication de code très détaillée qui était un peu longue.

## A cartoon intro to performance par [@linclark](https://mobile.twitter.com/linclark)

Ce talk de @linclark était vraiment géniale. J'avais déjà vu une autre conférence d'elle à la react conf (en streaming) sur les différentes implémentations de flux et c'était extrèmement bien présenté.
Concernant ce talk, il s'agit d'un sorte de personification de ce qu'il se passe dans le navigateur lors du rendu et ensuit  de comment procède React pour rendre les composants. 
Il y avait ensuite plusieurs conseils concernant les optimisations facile à faire sur du code React.
Exemple simple: `{(props) => <ul>{props.list.map(element => <div key={element.id}>{element.name}</div>}</ul>}` permet d'améliorer les performances de rendu des listes en utilisant une clef unique sur la données.( Mettre la position dans la liste est par exemple une mauvaise idée).
> Ce talk est vraiment super, je pense que je volerai quelques idées pour la prochaine session du formation

## Transition, Animation avec React native par @krzys

Ce talk était à propos des animations dans React Native, par un ancien de Facebook. Il a parlé des différences entre les animations de Layout et de composants,. `<AnimatedView><Component /></AnimatedView>`
> Ce talk m'a rappellé les talks de l'année dernière sur les animations de composants. Il était très technique et répond à des problématiques assez poussées sur les animations avec React native.

## Comment avoir un projet open source qui marche par @vjeux

