---
layout: post
title: Docker for PHP/WordPress projects
excerpt: "Getting started to run PHP projects in Docker containers"
tags: [docker, deployment, virtual, infrastructure, php, symfony, wordpress, eng]
comments: true
image:
  feature: header/tech/electronics.jpg
---

#Introduction

A friend of mine asked me a little help on a WordPress plugin, and since Linux/Apache/MySQL/PHP is no more my full time work environment, I wanted to help him but in the same time try to keep my laptop light by avoiding installing this whole stack for a such very punctual need. One of the solutions is to use a temporary VM, with tools like Vagrant, Ansible and Puppet, automating transient VM has become easy like never before. But this approach have disadvantages too, and the main one is the resources consuming side effect. And this is where Docker shines, with Docker, we are not virtualizing operating systems but rather virtualizing processes.

Here is a an quick comparison form Jérémy DERUSSÉ <a href="#specific-to-phpsymfony">talk</a>

<img src="/images/2015/docker/vm-vs-docker.png" />

<img src="/images/2015/docker/vm-vs-docker-perfs.png" />


If you're using Docker in linux, then Docker containers have direct access to the host hardware, since it's not possible in Mac/Windoz, Docker containers are ran in a single lightweight and optimized VM used like a mediator. The gain is significant if you need to run multiple linked containers at the same time (Imagine a container for Apache, the second for MySQL, the third for an external service like MongoDB, RabbitMQ...)

<img src="/images/2015/docker/boot2docker.png" />

Docker automatically shares the user home folder between the host (your laptop) and Docker Machine (boot2docker) where you can locate your code source, if like me you customized the home folder path, here is a quick workaround how to tell the default Docker Machine to mount your customized path: 

<img src="/images/2015/docker/docker-virtualbox-shared-folder.png" alt="Change Docker Virtualbox Shared Folder" />

#Start point

- <a href="https://docs.docker.com/installation/mac/">Official Installation Guide</a>

#Recommended talks

Docker for developers by Jérôme Petazzoni

<iframe width="420" height="315" src="https://www.youtube.com/embed/FdkNAjjO5yQ" frameborder="0"> </iframe>

<br />


Workshop : 45 minutes pour comprendre Docker avec Jérôme Petazzoni

<iframe width="560" height="315" src="https://www.youtube.com/embed/bXSC3-mrgWA" frameborder="0"> </iframe>

##Specific to PHP/Symfony

Docker pour le Dev & CI @ Symfony Live 2015


<iframe width="560" height="315" src="https://www.youtube.com/embed/G_msP7OqTLU" frameborder="0"> </iframe>


<br />

<a href="http://slides.com/jeremyderusse/docker-dev" target="_blank">Slides</a>


<iframe width="614" height="450" src="//slides.com/jeremyderusse/docker-dev/embed"  scrolling="no" frameborder="0"> </iframe>


<br />

#Top Commands

##Playing with Docker Machine

List, start & get the docker-machine VM IP:


{% highlight bash %}
docker-machine ls
docker-machine start default
docker-machine ip default
{% endhighlight %}

Connect (ssh) to default machine

{% highlight bash %}
eval "$(docker-machine env default)"
{% endhighlight %}

##Playing with containers

Launch a Docker container:

{% highlight bash %}
docker run -d -P -v /Volumes/Data/Users/fayway/site:/usr/share/nginx/html  --name web nginx
{% endhighlight %}

* -d flag keeps the container running in the background 
* -P flag publishes exposed ports from the container to your local ost
* -v share between docker-machine and the container


##One liner to stop / remove all of Docker containers:

{% highlight bash %}
docker stop $(docker ps -a -q)
docker rm $(docker ps -a-q)
{% endhighlight %}

#My docker-compose.yml using WordPress and MySQL official containers

{% highlight yaml %}
web:
    image: wordpress
    restart: always
    links:
     - mysql
    environment:
     - WORDPRESS_DB_PASSWORD=wordpress
    ports:
     - "8080:80"
    volumes:
     - /Users/fayway/Workspaces/WordPress/wp.last:/var/www/html
mysql:
    image: mysql:5.7
    environment:
     - MYSQL_ROOT_PASSWORD=wordpress
     - MYSQL_DATABASE=wordpress
{% endhighlight %}

And execute

{% highlight bash %}
docker-compose up
{% endhighlight %}


#Extra Resources

### Synmfony

- http://vincent.composieux.fr/article/run-a-symfony-application-using-docker-and-docker-compose
- http://vincent.composieux.fr/article/faire-tourner-une-application-symfony-avec-docker-et-docker-compose


### WordPress

- 1 - http://www.sitepoint.com/docker-for-wordpress-developers
- 2 - http://www.sitepoint.com/how-to-manually-build-docker-containers-for-wordpress
- 3 - http://www.sitepoint.com/how-to-use-the-official-docker-wordpress-image
- 4 - http://www.sitepoint.com/deploying-wordpress-with-docker
- 5 - http://www.sitepoint.com/wocker-easy-dockerized-wordpress

### Workaround to use ngrok for a Docker container

If `local.dev` is the address of the Apache/nginx container server, so the workaround consists of creating a first tunnel via browser-sync and make ngrok using it since the new proxy will have a `localhost` address

{% highlight bash %}
browser-sync start --proxy "local.dev"
ngrok http localhost:3000
{% endhighlight %}







