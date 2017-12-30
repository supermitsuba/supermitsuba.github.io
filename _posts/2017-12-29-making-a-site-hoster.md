---
id: 247
title: Making a site hoster
date: 2017-12-25
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=247
permalink: /2017-12-29-making-a-site-hoster
categories:
  - docker
  - .net
tags:
  - docker
  - .net
---
Lately I have been working on a rapid prototyping .net website generator.  Here is something similar: [Glitch](https://glitch.com/).  This site is cool because I can build and have a site running in moments.  So I wanted to do this with C#, but I could see this with any kind of technology.  I did this with docker and .net, but we could use any language.  

So far I have built out the infrastructure.  Its important to have all the api's first.  Here are some of the API systems I needed:

1. Nginx
 *  Need to organize the websites through a single endpoint.  Nginx is a proxy server to help do that.
2. Docker
 *  Docker helps spin up environments for Nginx, discovery service, and any website that is built in the system.
3. Discovery Service
 *  This is how we find out where websites and apis are.
4. Dot net
 *  Used to build and deploy a .net website

Things I learned
----------------

Nginx is a cool piece of software.  I always hosted things from a bunch of different ports.  This is not good because it leaves a bunch of these ports open.  Instead, with Nginx, I can isolate outgoing traffic into one port.  The other thing is that we can make all the routes with great names instead of crazy ports in the address.

Controlling Docker from docker is awesome. You need to share a volume for the /var/run/docker.sock .  While I haven't gotten to the point of using Docker swarm or Kubernetes, this works good enough for a single machine.  Docker also helps build the sites, isolate them and run them super easily.  If they crash, then only that one container goes down.  The other thing about docker is how to share folders.  Consistent folder structures are key.

Discovery Service is a great service to have in a system.  It tells you where you can find anything.  Makes so you don't have to hardcode anything in a configuration file.  This is also a great place to save information for all the websites that are being generated.

Lastly, you need a service to build a dotnet website.  So I built that out to manage creating, building and deploying a website.

What's next
-----------

I'm not done yet but these services are a great start and actually can spin up everything in docker compose.  Then I can use the API's to build a generic website.  Works pretty nice.  This means I should probably start with the UI and orchestrating calls with a queuing system.  Most of that will be a new article in the future.  Here is where you can see the progress:  [https://github.com/supermitsuba/SiteHoster](https://github.com/supermitsuba/SiteHoster)
