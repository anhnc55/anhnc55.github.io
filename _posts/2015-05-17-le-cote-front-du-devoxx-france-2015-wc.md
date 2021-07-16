---
layout: post
title: Le coté Front du Devoxx France 2015  - Part 2
excerpt: "Ce qu'il faut retenir de l'actualité Front durant Devoxx France 2015. Partie 2 : Web Components c'est déjà Production ready"
tags: [web, javascript, Web Components, Polymer, devoxx, fr]
comments: true
image:
  feature: header/tech/book-mess.jpg
---
# Introduction
<p class="image-pull-right">
<img src="/images/2015/js-logo.png" style="width: 150px; margin-left: 5px"/>
</p>

La suite de mes notes Front lors de mon dernier Devoxx France 2015.

> Dans le même registre, lire l'introduction précédente ainsi que la première partie consacrée à <a href="/le-cote-front-du-devoxx-france-2015-es6/">l'ECMAScript 6</a>.

<div style="clear:both"></div>

# Web Components: Production ready

La tendance actuelle c'est des SPA orientée composants et non pas templates/vues.

Chaque framework propose déjà sa propre solution, les standards Web Components visent à uniformiser les implémentations pour avoir des composants réutilisables, inter-opérables, composables, sémantiques qui encapsulent une complexité technique/fonctionnelle particulière?

<p class="image-pull-right">
<img src="/images/2015/wc-logo.svg" />
</p>

Les Web Components c'est

- Custom elements (comment les créer et les ajouter au DOM à travers des méthodes Javascript qui assurent un cycle de vie compatible)
- Templates (bout de code analysé par le navigateur mais non rendu)
- Shadow DOM (ajoute des frontières aux Web Components pour éviter des conflits CSS/JS)
- Import (Importer un Web Component dans une page ou dans un autre Web Component)

L'API web components est toujours en cours d'élaboration mais le standard est déjà prés pour la PROD grace aux polyfills et surtout l'implémentation Polymer de Google, version 1.0 stable annoncée au Google I/O 2015.

Si les frameworks (Angular, Ember, React...) implémentent également ce standard, on pourra alors dans la même page cohabiter plusieurs composants réalisés avec différents frameworks.

Pour plus de détails, le talk <b>Web Components avec Polymer</b> de Horacio Gonzalez et la meilleure adresse.

<center>
<iframe src="//www.slideshare.net/slideshow/embed_code/key/c7cPN51E6omI3i" width="600" height="450" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe>
</center>
