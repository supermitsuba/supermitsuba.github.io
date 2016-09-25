---
id: 234
title: Docker Linking
date: 2016-07-11T02:33:12+00:00
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=234
permalink: /2016/07/11/docker-linking/
categories:
  - general
tags:
  - docker
---
I have been working on docker stuff for the past few weeks.  The biggest reason is to spin up our whole development environment together.  This can be complicated because of all the vm&#8217;s, frameworks and databases we have in our development environment.  While I wanted to use docker-compose, I wanted to know what it would take for one to get a docker instance up from scratch.

The idea of docker is that everything is in it&#8217;s own container, and that containers should use child containers.  So I made a few containers:

  1. base &#8211; This has stuff like git, wget, etc.  Any tools needed for a VM/Container and the base OS to use, like Ubuntu.
  2. MySQL -A service to store data.
  3. Ruby &#8211; A base image with all my ruby dependencies
  4. code &#8211; Uses the ruby base image and then links to mysql.  This is where my web service lives

That is a bunch of dockerfiles, and while experimenting, I made a bunch of space on my hard drive.  There are some handy scripts to help, like this one:

<pre class="lang:default decode:true ">docker rmi $(docker images -q -f dangling=true)</pre>

This script will delete any images and containers that are not taged anymore.

For starting the Base image, this was simple enough.  Just add a bunch of software, like wget, git, curl, vim.  This also used ubuntu 14.04 for the VM.

For the mysql database, I found a docker image that I liked; https://github.com/tutumcloud/mysql .  I like this one because you can just start up an instance immediately, give it your username and password to use, and you are done.  This image is using my Base image from above, so it will have all the tools on the container.

For my Ruby image, this installed all the tools and prerequisites that I need for Ruby, like rbenv, ruby, mysql clients and etc.  This makes it so every time I make a new web service or site, it takes seconds to create a new environment.

Now, for my Code image, I need to reference the mysql database image.  This is so in my configuration, i will put down my username, password and servername (this comes later with linking).  But for this I just pull down the code and run bundle install.

Build your machines:

<pre class="lang:default decode:true">docker build -t base:latest .
docker build -t mysql:latest .
docker build -t ruby:latest .
docker build -t code:latest .</pre>

Start up your mysql instance:

<pre class="lang:default decode:true">docker run -d -p 3306:3306 -e MYSQL_PASS="password" MYSQL_USER="root" --name db mysql:latest</pre>

In the mysql instance,  I have a &#8211;name db.  If I want to reference a database in code, all I have to do is make the hostname &#8216;db&#8217;.

Next, initialize database stuff in Ruby with db:setup.  In the command below, I will be put on a prompt in a container.  This helps me initialize the database when I have to run db:setup.  You can do this with run -it and at the end /bin/bash:

<pre class="lang:default decode:true ">sudo docker run -it code --name web2 --link db:db code:latest /bin/bash</pre>

Boom done.  Next, start your code (notice, i use the same image, but this time I used -d instead of -it.  This runs it in the background):

<pre class="lang:default decode:true ">sudo docker run -d -p 3000:3000 --name web --link db:db code:latest</pre>

Notice, that you have a &#8220;link&#8221; to db as db.  In your configuration, your code will think db is a server name and will be able to connect to it.

You should have a full environment set up for testing.   I will post my dockerfiles on github to help show these work together.  Later, I will be talking about persisting the database stuff, and how all this relates to docker compose.