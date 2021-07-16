---
layout: post
title: Penser les tests "out of the box"
excerpt: "Regarder les tests plus loin que le bout de son nez"
tags: [architecture, tests, tdd, bdd, devoxx, fr]
comments: true
image:
  feature: header/nature/horizon.jpg
---

Pour ma mission actuelle, on m’a demandé de présenter à un auditoire constitué de responsables et de profils MOE, l’importance du développement piloté par les tests et de les convaincre de l’intérêt  des tests automatisés (Tests Unitaires  et du Comportement/Behavior) d’une façon générale...

J’ai trouvé malheureux qu’en 2015, il existe encore des hésitants auprès desquels, les tests automatisés ne jouissent toujours pas d’une bonne réputation… J'ai cru comprendre que les raisons avancées sont souvent :

- Pour les décideurs : "ça fait flamber le chiffrage et le budget"
- Pour les développeurs : "ça fait du code de plus à écrire et à maintenir( parfois plus compliqué que la vraie implémentation)"

Dans mon projet actuel, on est conscient de ses points « négatifs » mais on est convaincu que les avantage et les solutions que le TDD/BDD peuvent nous apporter, dépassent et éclipsent les autres "soi-disant" inconvénients.

Au passage un petit rappel sur les avantages ne fera de mal à personne :

- Contrôler la régression :
  - => Ne pas avoir peur du changement/évolution
- Faciliter la maintenance
  - => Plus de maitrise, confidence...
- Détecter et corriger rapidement
  - => Messages d'erreur plus explicites/ciblés
- Mutualiser les développements
  - => Grace à la vision unitaire (Sur une spec, story...)
- Améliorer la qualité des livrables en général

Tout le monde connait déjà ces avantages, mais rares les équipes qui arrivent à se lancer sur le TDD/BDD et surtout arrivent à les maintenir en vie…

Pour ne pas connaitre le même sort dans notre projet, on essaye de voir ce sujet d’une façon plus globale, on essaye de penser "**out of the box**" en donnant aux tests **plus de responsabilités**.

On essaye alors que les tests soient un moyen de :

- Mieux préciser les spécifications
  - Résultat immédiat : Réduire l'ambiguïté / incompréhension
  - On parle alors de **Tests as Specifications** ou **Spécifications Exécutables**  qui sont souvent le résultat de mini ateliers d’**Event Storming** pour identifier les stories ainsi que les échanges/intéractions entre les différents intervenants...
- Enrichir la documentation
  - Résultat immédiat : Langage/Vocabulaire commun entre Client, MOA et MOE
  - On parle alors de **Tests as Documentation** puisque les tests contiennent un langage naturel orienté métier (**Domain Driven**)
- Tracer des exemples significatifs
  - Résultat immédiat : Scénarii de tests bien ficelés
  - On parle alors de **Tests as Examples**, en plus chaque anomalie remontée donne lieu à un nouveau test pour "immortaliser" le jeux de données du cas "tordu"
- Mieux concevoir et structurer le code de l'implémentation
  - Résultat immédiat : Respect naturel des bons pratiques SOLID & Co
  - On parle alors de **Design for Testability**, généralement les développeurs ont souvent le choix de respecter ou non les bonnes pratiques de développement,  mais tout code n’est pas testable, et pour faire un code testable, ces développeurs se trouvent **obligés** d’adopter des principes comme le **Single Responsability Principle, Dependency Inversion Principle, Open Closed Principle**…

Et finalement:

- Généraliser l’automatisation
  - Réduire l'intervention humaine
- Assurer un meilleur taux de couverture
  - Résultat fidèle à la stabilité réelle

> Pour résumer,  le Test Driven Development et le Behavior Driven Development ce n'est pas seulement à propos d'écrire des tests, c'est plutôt à propos de mieux décrire le comportement du produit et mieux le concevoir et l'implémenter…

à méditer…

Credits : Notre démarche est en grande partie inspirée des articles du maître artisan "Sir" <a href="http://martinfowler.com/" target="_blank">Martin Fowler</a> et du livre <a href="http://martinfowler.com/books/meszaros.html" target="_blank">xUnit Test Patterns</a>
{: .notice}
