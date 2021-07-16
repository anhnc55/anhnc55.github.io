---
layout: post
title: Le Réveil des Tests des Composants Graphiques
excerpt: "Les Jedis Frontistes se révoltent sur le temple du Back et montrent qu'ils maîtrisent également la sagesse du TDD, BDD et les patterns xUnit... To be continued"
tags: [TDD, BDD, xunit, JavaScript, Component, UI]
comments: true
image:
  feature: header/tech/tests_sith_and_jedi.jpg
---

Comme vous l'avez surement constaté, JavaScript n'arrête pas de gagner du terrain par rapport aux langages traditionnels côté serveur. Alors qu’il était utilisé uniquement pour valider superficiellement les formulaires avant l’envoi des données aux serveur (où les technologies Back avaient le monopole total des traitements métiers), à présent, et pour des raisons d'ergonomie, de réactivité et la nécessité de supporter plusieurs périphériques, l'architecture des applications a été repensée et limite de plus en plus le Back à de simples APIs REST retournant des données brutes, et passe désormais la main aux applications clientes pour implémenter les différents workflows et règles métiers.

Les développeurs JavaScript se sont donc retrouvés du jour au lendemain obligés d'adopter un style de programmation modulaire, de faire de l'inversion de contrôle via l'injection de dépendance, d'avoir une couche Modèle, de séparer les préoccupations entre les contrôleurs et les vues etc.

Avec ces nouvelles exigences viennent de nouveaux pouvoirs, et avec plus de pouvoirs viennent plus de responsabilités; Il ne fallait surtout pas compromettre la qualité des livrables et on demande de plus en plus aux développeurs JavaScript d'assurer le même niveau de qualité qu'on exigeait à des techno mûres comme Java par exemple.
Une chose est sûre, cuisiner du code spaghetti avec jQuery n'était plus tolérable, et, pour cette raison, les tests JavaScript ont commencé à prendre tout leur sens.

La présentation "<a href='http://fayway.github.io/ComponentsTesting/' target='_blank'>Le Réveil des Tests des Composants JavaScript</a>" a essayé de rebondir sur cette nouvelle nécessité, la première partie théorique a été consacrée aux concepts généraux tels qu’ils étaient définis dans le livre référence "<a href='http://www.amazon.com/xUnit-Test-Patterns-Refactoring-Code/dp/0131495054' target='_blank'>xUnit Design Patterns</a>", l'objectif de cette partie est de se mettre d’abord d'accord sur le même vocabulaire en rappelant en parallèle l'importance d'adopter une conception testable. C'était donc l'occasion de parler de :

- L'importance de définir un périmètre unitaire par chaque SUT (Respect du principe de la responsabilité unique, tester une seule chose à la fois, faire la différence entre un test unitaire et un test d'intégration)
- Expliciter l'API publique des composants et la concevoir pour être manipulable de l'extérieur (Injection de dépendance, conception ouverte à l'extension...)
- Faire la différence entre les paramètres d'entrée directs et indirects (introduits via l'API public ou par les dépendances)
- Bien cerner les paramètres de sortie qui peuvent aussi être directs ou indirects (pareil, retournés par l'API ou observés via les dépendances)
- Le rôle des doublures de tests dans le contrôle des paramètres d'entrée et l'observation des paramètres de sortie
- Tester l'état Vs Tester le comportement
- L'organisation d'un test unitaire et le rôle de chaque étape (Fixture Setup, Exercice, Assertion Tear Down)
- Un bon test doit suivre les principes FIRST (Fast, Isolated/Independant, Repeatable, Self-checking & Timely)

La deuxième partie a essayé de présenter le développement JavaScript avec une approche orientée Composants plutôt que MVC pour réussir une conception testable. Les avantages de cette approche :

- Niveau de granularité plus fin (contre Fat Controllers qui font souvent plusieurs choses à la fois)
- Les composants peuvent être autonomes, bootstrappés comme application, chargés comme une route ou utilisés comme fils d'un composant père…
- Les composants sont réutilisables
- Les composants ont une API publique explicite
- Les composants ne sont pas liés à un contexte particulier
- Les composants du bas niveau communiquent via le composant parent
- Éviter un couplage fort entre les différents composants et introduire un système de communication basé sur des évènements

Pour organiser les composants, on peut suivre le modèle de l'<a href='http://patternlab.io/about.html' target='_blank'>Atomic Design</a> qui organise les composants en :

- Atomes
- Molécules
- Organismes
- Ecosystèmes
- Environnements

Avec des recommandations comme par exemple la bonne pratique que les composants de type Atomes / Molécules / Organismes ne doivent avoir que des inputs directs, et ne doivent que qu'afficher des données ou interagir avec l'utilisateur. Par contre, c'est au niveau de l'Ecosystème / Environnement que les dépendances sont injectées pour introduire des inputs indirects, ou provoquer des outputs indirect.

Et avant de présenter comment tester ces composants graphiques, il faut d’abord rappeler leur rôle principal à savoir:

- Afficher une visualisation HTML des données passées en argument (inputs)
- Fournir à l'utilisateur un moyen d'interagir avec le SUT
- Communiquer avec les autres composants (Ecouter / émettre des évènements)
- Encore une fois on va pas se lasser de rappeler que même doté de tous les outils les plus puissants qu’on peut avoir, si le Design pour la Testabilité n’a pas été pris au sérieux, alors ces outils ne vont pratiquement servir à rien.

Vous pouvez accéder au code source de la démonstration via ce repo <a target="_blank" href="https://github.com/fayway/JsComponentsUnitTesting" target="_blank">GitHub</a>, cette application essaye d'illustrer les concepts théoriques, et utilise les technologies suivantes :

- EcmaScript 6 : Le code source est écrit avec la nouvelle version de JavaScript 2015
- Webpack : Le nouveau bundler qui écrase la concurrence (Gulp, Grunt, Browserfy...) grâce à qui le code ES6 est transpilé en ES5 (sans parler du serveur local qu’il embarque, le hot reload, etc.)
- Reactive.js : Une librairie aussi performante que React pour faire des vues (dotée de data-binding, gestion du cycle de vie, système d'évènements...) avec une courbe d'apprentissage bien plus courte qu'un framework full-stack comme Angular
- Mocha : Test runner qui supporte l'approche TDD / BDD
- Chai : Librairie d'assertion
- Sinon.JS : Librairie pour construire les doublures de tests
- jsdom : Pour faker un DOM en JavaScript et pouvoir tester nos composants JS en console (sans browser)

La procédure d'installation :

- <a href="https://github.com/fayway/JsComponentsUnitTesting/blob/master/Readme.md" target="_blank">Readme.md</a>

Un exemple de tests simples d'état :

- <a href="https://github.com/fayway/JsComponentsUnitTesting/blob/master/tests/slides/PureComponents.js" target="_blank">tests/slides/PureComponents.js</a>

Un exemple de tests de composant avec un fake DOM via jsdom :

- <a href="https://github.com/fayway/JsComponentsUnitTesting/blob/master/tests/slides/JsdomComponents.js" target="_blank">tests/slides/JsdomComponents.js</a>

Un exemple de tests d'état (Le HTML attendu) et test du bon comportement après des clicks :

- <a href="https://github.com/fayway/JsComponentsUnitTesting/blob/master/tests/components/CompteSwitcherSpec.js" target="_blank">tests/components/CompteSwitcherSpec.js</a>

Un exemple de test avec doublure de type Espion d'une Dépendance :

- <a href="https://github.com/fayway/JsComponentsUnitTesting/blob/master/tests/components/MainSectionSpec.js" target="_blank">tests/slides/components/MainSectionSpec.js</a>

Si vous l’avez raté, la ligne la plus importante :

{% highlight javascript %}
expect(VirementService.postVirement.withArgs(1, 300).calledOnce, "Le service VirementService.postVirement n'a pas été appelé avec les bons arguments").to.be.true;
{% endhighlight %}

N’hésitez pas à parcourir <a href="https://github.com/fayway/JsComponentsUnitTesting/tree/master/tests" target="_blank">l’ensemble des scénarios de tests</a> en installant et lançant d’abord le serveur local de tests via :

{% highlight bash %}
npm install
npm run devtest
{% endhighlight %}

Plus de détails: <a href="https://github.com/fayway/JsComponentsUnitTesting/blob/master/Readme.md" target="_blank">Readme.md</a>



