---
layout: post
title: Silex based WordPress Plugin  
excerpt: "How to use Silex as a micro-framework for developing a WordPress Plugin"
tags: [POC, software, wordpress, silex, php, architecture, eng]
comments: true
image:
  feature: header/mac/mac-code.jpg
---

## Introduction

In this POC, I used [Silex](http://silex.sensiolabs.org/){:target="_blank"} as a micro-framework for developing a WordPress plugin to validate if Silex is small but efficient enough to wrap informal and not object oriented code into more clean and service oriented one.

The main "benefits" can be:

* Use [Pimple](http://pimple.sensiolabs.org/){:target="_blank"} as a service container for various plugin services
* Use [HTTP Foundation components](http://symfony.com/doc/current/components/http_foundation/index.html){:target="_blank"} (Request & Response) to handle all the HTTP layer interactions
* Use [Twig](http://twig.sensiolabs.org/){:target="_blank"} as a template engine. eg the plugin setting page
* Use the [EventDispatcher](http://symfony.com/doc/current/components/event_dispatcher/index.html){:target="_blank"} component as a complementary of WordPress Actions
* Use [Monolog](https://github.com/Seldaek/monolog){:target="_blank"} to trace what's happening under the hood
* ...

You can find the complete code in this [GitHub repo](https://github.com/fayway/silex-wordpress){:target="_blank"}

## Disclaimer

That's what's going to happen inside Uncle Bob head if by chance he finds this repo:

> Why would someone need to use Silex as a developing platform for a WordPress plugin?!!!

> What kind of nonsense is that?!! Putting business rules inside a tool that's itself bundled inside another tool!!!
The ULTIMATE INFINITE ENSLAVEMENT this hack screams !

> What's the purpose of the plugin? Why don't you talk about the business instead of WordPress or Silex, those are just tools

> Arghhh... God help you, cause the tools will not!

So you're warned, don't try this at home or do it at your own risk :)


## Installation

To test the plugin directly into your already setup WordPress installation, please follow those steps:

{% highlight bash %}
> cd /path/to/wordpress/plugins
> git clone https://github.com/fayway/silex-wordpress.git
> cd silex-wordpress
> composer install
{% endhighlight %}

Finally activate the plugin from the WordPress Admin Dashboard.

## Code explanation

#### Main Plugin File

<script src="http://gist-it.appspot.com/https://github.com/fayway/silex-wordpress/blob/master/SilexProof.php?footer=1"></script>

#### An Exemple of a Pimple Service that uses Monolog for logging and Twig to render a WordPress Admin Setting Page

<script src="http://gist-it.appspot.com/https://github.com/fayway/silex-wordpress/blob/master/src/SilexProof/SomeService.php?footer=1"></script>

#### An Exemple of a Pimple Service exposing a function callable by `wp_ajax`

<script src="http://gist-it.appspot.com/https://github.com/fayway/silex-wordpress/blob/master/src/SilexProof/SettingsProvider.php?footer=1"></script>

You can find the complete code in this [GitHub repo](https://github.com/fayway/silex-wordpress){:target="_blank"}
