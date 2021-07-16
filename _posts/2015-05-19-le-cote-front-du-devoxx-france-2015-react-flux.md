---
layout: post
title: Le coté Front du Devoxx France 2015  - Part 4
excerpt: "Ce qu'il faut retenir de l'actualité Front durant Devoxx France 2015. Partie 4 : React & Flux, ce n'est pas seulement du buzz"
tags: [web, javascript, Web Components, react, flux, devoxx, fr]
comments: true
image:
  feature: header/mac/mac-hand-code.jpg
---
# Introduction
<p class="image-pull-right">
<img src="/images/2015/js-logo.png" style="width: 150px; margin-left: 5px"/>
</p>

La suite de mes notes Front lors de mon dernier Devoxx France 2015.

> Dans le même registre, lire l'introduction précédente ainsi que la première partie consacrée à <a href="/le-cote-front-du-devoxx-france-2015-es6/">l'ECMAScript 6</a>,  la deuxième partie sur les <a href="/le-cote-front-du-devoxx-france-2015-wc/">Web Components</a> et la troisième partie qui parle de <a href="/le-cote-front-du-devoxx-france-2015-angular-aurelia/">Angular 2 et Aurélia</a>.

<div style="clear: both"></div>

# React : Le buzz gagnant de 2015

Pour être bref, ReactJS c'est :

- Librairie créé par Facebook pour faire des interfaces graphiques (open source depuis 2013)
- C'est le V du MVC (Rend des vues et répond à des évènements, pas de full stack)
- Cible les applications à haute influence destinées à être réactives (il est adopté également par Instagram, Airbnb, Netflex, Flipboard, HipChat...)
- Approche purement composants (et non pas templates)
- Mécanisme de databinding performant: génère les vues quand les données changent mais ne patch le DOM que avec les différence
- Ce calcul de différence est fait sur le Virtual DOM (et c'est ce qui fait la performances de React) puis batch que les changements nécessaires vers le vrai DOM.
- Une librairie isomorphique, grâce à son DOM virtuel, elle n’est pas dépendante du DOM navigateur et peut donc fonctionner coté client comme coté serveur.  Elle constitue ainsi un excellent choix  si vous servez du HTML depuis du Node.js (express) 

<p class="image-pull-right">
<img src="/images/2015/react-logo.svg" width="150" />
</p>

Attention: Le HTML( ou JSX) de la vue est mis directement à l'intérieur du code JS
problème de séparation des préoccupation ?

- non, car la template est fortement couplée au composant dans toute les manières
- les templates séparent les technologies, pas les préoccupations.

Last but not least, React propose aussi React Native: version qui ne cible pas le DOM mais un moteur de rendu native sur mobile (Android et iOS)

<center>
<script async class="speakerdeck-embed" data-id="e5648e088a7c4a39ae8148d73503aaa7" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>
</center>

## Flux :

<p class="image-pull-right">
<img src="/images/2015/flux-logo.png" width="150" />
</p>

- Un pattern plus qu'une librairie recommandé par Facebook pour gérer la partie full stack qui interagit avec la vue (React ou autres)
- Basé sur le principe de flux de données unidirectionnel (la flèche va toujours dans le même sens : Action -> Dispatcher -> Store -> View -> Action -> Dispatcher -> Store ....

Dispatcher: Rien d'autre d'un gestionnaire de catalogue de callback (register, unregister, disptach, waitFor)

<p class="image-pull-center">
<img src="/images/2015/flux-workflow.png" />
</p>

Flux c'est le retour vers la simplicité : 4 Composants + des évènements et c'est tout !
Résultat => Simplification de la maintenance, debuggage, testabilité...
Plusieurs implémentations existent: RefluxJS, Fluxxop, Fluxy, Tuxx, Alt...

<center>
<iframe src="//www.slideshare.net/slideshow/embed_code/key/bTko0mt1XCuuQT" width="600" height="450" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe>
</center>
