---
layout: post
title: Le coté Front du Devoxx France 2015  - Part 5
excerpt: "Ce qu'il faut retenir de l'actualité Front durant Devoxx France 2015. Partie 4 : Le coup de coeur Ionic mais aussi le résistant GWT"
tags: [web, javascript, angular, ionic, gwt, devoxx, fr]
comments: true
image:
  feature: header/tech/electronics.jpg
---
# Introduction
<p class="image-pull-right">
<img src="/images/2015/js-logo.png" style="width: 150px; margin-left: 5px"/>
</p>


La suite de mes notes Front lors de mon dernier Devoxx France 2015.

> Dans le même registre, lire l'introduction précédente ainsi que la première partie consacrée à <a href="/le-cote-front-du-devoxx-france-2015-es6/">l'ECMAScript 6</a>,  la deuxième partie sur les <a href="/le-cote-front-du-devoxx-france-2015-wc/">Web Components</a>, la troisième partie qui parle de <a href="/le-cote-front-du-devoxx-france-2015-angular-aurelia/">Angular 2 et Aurélia</a> et la dernière partie sur <a href="/le-cote-front-du-devoxx-france-2015-react-flux/">React & Flux</a>.

<div style="clear: both"></div>

# Ionic framework : Le coup de coeur en 2015

<p class="image-pull-right">
<img src="/images/2015/ionic-logo.png" width="150" />
</p>

C'est un écosystème complet pour faire des applications mobiles hybrides.
Il embarque entre autres :

- Build tools (npm, gulp, less...)
- AngularJS pour le SPA
- Cordova pour les fonctionnalité natives
- Ligne de commande puissante (création d'un projet à, partir d'une template, watch, live reload, émulation ou build...)
- Offre des composants(directives) prêts à l'emploi avec le look & Feel de iOS et Android

<center>
<iframe src="//www.slideshare.net/slideshow/embed_code/key/9hgZapeu2pR0bM?startSlide=35" width="510" height="420" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; max-width: 100%;" allowfullscreen></iframe>
</center>
<br />

<div style="clear: both"></div>

# GWT : Le résistant

<p class="image-pull-right">
<img src="/images/2015/gwt-logo.png" width="150" />
</p>

Pour les javaitiste qui n'aiment pas JavaScript ou qui sont obligés de faire du JavaScript.

GWT est plus mûr que les autres framework JS: il a déjà 10  ans

Google a porté en GWT des appli complexes comme Google SpreadSheet, Google Inbox...

GWT supporte Java 8 (verbosité de code java réduite), SuperDevMode (compilation instantanée de JS)

<iframe src="//www.slideshare.net/slideshow/embed_code/key/AJK3Kt3YHvMEdy" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/samijaber/devoxx-fr2015-gwt" title="Présentation DevoxxFR 2015 sur GWT" target="_blank">Présentation DevoxxFR 2015 sur GWT</a> </strong> from <strong><a href="//www.slideshare.net/samijaber" target="_blank">samijaber</a></strong> </div>

<br />
A venir : Singular, un framework à mi-chemin entre GWT et Angular

- Réutiliser des concepts connus dans Angular comme MVC et databinding
- API cross-plateformes (template UI par plateforme)

Plus sur <a href="http://www.daniel-kurka.de/talks/gwtcreate15/singular.pdf" target="_blank">Singular</a>
