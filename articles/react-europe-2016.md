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

@vjeux est un français qui travaille chez Facebook. Il est impliqué dans tous les projets open source qui ont fonctionnés chez Facebook. **Comment fait-il?**.
Premier point, chez Facebook, on ne sort en open source que les projets qui sont utilisés en production et qui sont suceptibles d'avoir une utilité à l'extérieur.
Pour lui il est important de se poser la question suivante: Comment faire participer la communauté?
Quand ils ont open sourcé **React**, plusieurs personnes étaient présentes sur les différents canaux de communications: Github, Stack OverFlow, des conférences mais toutes étaient  sur IRC.
- Le pluse simple pour avoir du bon feedback, poser la question suivante:  Qu'est ce qui est difficile à faire? Les utilisateurs savent le mieux ce qui fonctionne et ce qui ne fonctionne pas. En revanche pour certains points, il est plus utile d'avoir le feedback des utilisateurs plutôt que les suggestions de corrections, en général, la core team sait le mieux comment résoudre le problème, car ils ont tous les cas en tête.
- Un autre point est d'éduquer les utilisateurs. Par exemple les utilisateurs de react avaient toujours le message d'erreur sans en comprendre la source: `Invariant Violation`. Ils ont fait une doc pour expliquer qu'il ne fallait pas utiliser les sources minifiées en dev afin d'avoir les vrais messages d'erreur. Mais personne ne lit la doc... Ils ont donc changés le message d'erreur en disant que s'ils voulaient le message complet il suffisait d'utiliser les sources non minifiées.
- Une autre question à poser est qu'est ce que vous avez construit d'intéressant avec ma librairie? 
- Egalement faire du `Demo Driven Developpement`, le feedback visuel régulier est très important.
- Il faut également encourager les utilisateurs à écrire des articles de blog. Au début de React, il a demandé  30 utilisateurs de faire un article sur leur utilisation de React. Ceci a généré une très forte impression d'adoption de react dès le début et a grandement favorisé son adoption.

> Ce talk était vraiment super instructif, et très inspirant. Je pense que je vais essayer d'en appliquer les grands principes rapidement.

## Facebook GraphQL stack

Le but de ce talk était de présenter comment faire pour traiter les problématiques courantes avec GraphQL ou plutôt comment il font chez Facebook.
Les problématiques abordées étaient: l'autorisation, le cache et les performances.
Le premier point sur lequel il a insisté était le fait qu'il faut voir les données comme un graph et non comme un endpoint.
Le but de GraphQL est d'avoir une source unique de vérité.

- Pour la sécurité, un pattern émerge, l'ensemble des fonctions `resolve` doivent prendre en entrée un second argument avec `async gen(viewer, resourceId)`, le viewer étant récupéré depuis un token fournit dans la requête HTTP via `Viewer.fromAuthToken(request.authToken)`
- Pour les performances, ils ont ajouté pour tous les noeuds de même niveau du `batch request` et il y ba un `data-loader` qui a été open sourcé par Facebook à ce propos. Ceci sert à la fois au cache et au batch des requêtes de même niveau.

> Ce talk était très intéressant car permettait d'adresser des problématiques très concrètes et pas forcément mise en avant avec GraphQL. Il était également très clair dans sa formulation.


## Flow : linter on steroids

Flow est un outil développé par Facebook et utilisé massivement sur leurs projets. Il permet par une analyse poussée du code de : 
- Prévenir les erreurs
- Fournir de l'auto complétion
- D'ajouter du typage aux définitions de certaines fonctions et objets

Il a bien insisté sur le fait que Flow n'était pas un langage qui redéfinissait JavaScript, ni un compilateur mais bien un outil d'analyse de code. Flow fonctionne directement sur n'importe quel fichier JavaScript. 
Il a ensuité détaillé le fonctionnement de Flow: `codeJS => AST (Abstract Syntax Tree) => Flow Graph`.
Le flow graph étant un flux de data en provenance du code source. A partir de ce graph il est possible de trouver: le code mort, les erreurs de syntaxes, c'est un outil pour l'intelligence du code.
Les performances de flow sont très élevées.
Le support Windows a été annoncé pour ce mois dans la conférence, et il fonctionne déjà sur la version beta de windows 10.1.

> L'approche de flow est vraiment très interessante, il se pose comme une alternative à TypeScript. Bien qu'ayant des objectifs légèrement différents. On sent que l'objectif ici est vraiement d'améliorer l'expérience du Dévelopeur plus que de définir un nouveau langage.

## Redux dev tools extension

Redux est venu avec pas mal de petites extensions visant à améliorer l'expérience du développeur. Un contrat de définition d'un extension a même été défini. 
Ici il était question d'un projet qui permet de faire tourner ces extensions à l'intérieur d'une extension chrome et ou en remote.
Il est donc possible d'activer ces extensions sur des environnements de test et/ ou de recette afin de récupérer des informations sur l'application ou rejouer facilement des actions utilisateurs.

> Cette présentation était pleine de démos et avec pas mal de petites astuces à mettre en place dans les projets.

## On the spectrum of abstraction par @_chenglou

Faire une librairie revient à prendre des décisions tout le temps.
- Pour les `Computer Scientist` abstraire les choses représente le graal. => Abstraire apporte un pouvoir
- Pour les `Software Engineer` ce sont les cas concret qui sont son travail quotidien => cac concret contrait par l'abstraction

Plus on abstrait plus on perd potentiellement l'utilisateur,  plus on essaye d'abstraire des cas spécifiques plus on perd du pouvoir.
Si on cherche tous du pouvoir, quel est la bonne manière de l'utiliser ?

Par exemple pour React l'abstraction est `react` qui dispose de très peu de concept, l'utilisateur construit des apps avec React et entre les deux il y a le système de plugin de react.

Il est ensuite revenu sur plusieurs cas concrets:
- Les templates en JS plutôt qu'en HTML, c'est une contrainte et donc concession intellectuelle, mais qui apporte beaucoup plus de pouvoir à l'utilisateur: un template est une fonction plutôt que des data. Diff sur les vues plutôt que sur les modeles.

- La mutabilité vs l'immutabilité
- Le css en JS plutôt que via des feuilles de styles (function vs data)

Le plus important est d'avoir une api de faible surface et de faire des cas concrets.
