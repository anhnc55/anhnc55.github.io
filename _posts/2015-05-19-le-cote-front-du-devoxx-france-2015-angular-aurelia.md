---
layout: post
title: Le coté Front du Devoxx France 2015  - Part 3
excerpt: "Ce qu'il faut retenir de l'actualité Front durant Devoxx France 2015. Partie 3 : La déception AngularJS 2 & l'outsider Aurélia"
tags: [web, javascript, Web Components, AngularJS, angular, aurélia, devoxx, fr]
comments: true
image:
  feature: header/tech/bookshelf.jpg
---
# Introduction
<p class="image-pull-right">
<img src="/images/2015/js-logo.png" style="width: 150px; margin-left: 5px"/>
</p>

La suite de mes notes Front lors de mon dernier Devoxx France 2015.

> Dans le même registre, lire l'introduction précedente ainsi que la première partie consacrée à <a href="/le-cote-front-du-devoxx-france-2015-es6/">l'ECMAScript 6</a> et la deuxième partie sur <a href="/le-cote-front-du-devoxx-france-2015-wc/">les Web Components</a>.

#Angular 2: La déception ?

Angular 1 : Un vrai succès mais la 1ere release date déjà de 2009, certains choix architecturaux sont devenus dépassés par rapport à l'avancé général du Web et les capacités des navigateurs en particulier.

Une refonte complète s'est imposée pour faire de Angular un framework aussi performant et aussi simple que d'autres frameworks récents.

<p class="image-pull-right">
<img src="/images/2015/angular-logo.png" width="150" />
</p>

Angular 2 :

- Abondons de angular.module, $scope, Controllers, directive, jqLite
- Réécriture de la DI, templating, routing, logging, annotations...

Pour se préparer :

- Comprendre les nouveaux concepts de Angular 2 (surtout le fait qu'il devient plus orienté Web Composant)
- Apprendre TypeScript, sur-couche de javascript, compatible ES6, ajoute du typage statique (typage fort des variables et des retour de fonctions), énumérations, class/interface...
- Maitriser encore mieux les directives, la notion de Angular 1 qui se rapproche le plus des Web Components
- Rester à l'écoute de l'actualité car la syntaxe connait toujours des modifications

<center>
<iframe src="//www.slideshare.net/slideshow/embed_code/key/dPWOAkLihTX5tp" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe>
</center>

<br />
<br />

# Aurélia: L'outsider trouble-fête

Créé par Rob Eisenberg, un expert Front respecté qui a été débouché par Google pour travailler sur Angular 2, il n'était pas d'accord avec l'équipe Google sur pas mal d'aspects fondamentaux et a fini donc par quitter pour fonder Aurélia.

<p class="image-pull-right">
<img src="/images/2015/aurelia-logo.png" width="150" />
</p>

Aurélia vise le long terme:

- ES6 et même ES7
- Web Components
- Framework entièrement modulable
- Encourage Clean Code, Testable, privilégie les Standards, minimise la configuration, se base sur des Simple Conventions
- Communauté active + Support commercial possible par Durandal Inc.

Pour savoir plus sur Aurélia:

<iframe src="https://player.vimeo.com/video/131641012" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe> <p><a href="https://vimeo.com/131641012">Aurelia: Next Generation Web Apps - Rob Eisenberg</a> from <a href="https://vimeo.com/ndcconferences">NDC Conferences</a> on <a href="https://vimeo.com">Vimeo</a>.</p>
