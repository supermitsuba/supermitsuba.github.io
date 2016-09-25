---
id: 241
title: Docker shared space
date: 2016-07-12T02:52:43+00:00
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=241
permalink: /2016/07/12/docker-shared-space/
categories:
  - any
  - general
tags:
  - docker
---
Much of the docker stuff is coming together, but it has been slow.  So far I have learned how to get state saved in a VM!  It is easy actually and documented, but you have to watch out for a few details.

So you use -v like something like this:

<pre class="lang:default decode:true ">sudo docker run -d \
  -p 3306:3306 \
  -e MYSQL_PASS="password" \
  -e MYSQL_USER="root" \
  -v /var/apps/mysql/1:/var/lib/mysql  \
  --name db \
    mysql:latest</pre>

But, the things to watch out for is what you share.  It is advised to use this directory as a read-only from the host perspective.  This is because you can get into some weird OS lock magic.

The other gotcha is that don&#8217;t share a directory that is needed for configuration or binaries.  I think eariler I was doing that and it was deleting my directory in the container for some reason.

This makes me think, if you have a directory that will be RW for a container and Read Only for host, then go ahead and use it.  Dont share out bin directories because the container will freak out and stop.