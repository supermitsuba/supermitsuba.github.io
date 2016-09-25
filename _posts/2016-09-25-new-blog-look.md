---
id: 242
title: New Blog Look
date: 2016-09-25T02:52:43+00:00
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=242
permalink: /2016/09/25/new-blog-look/
categories:
  - any
  - general
tags:
  - html
  - blog
---
Just got done, yet again, migrating my blog.  The reason for the move is that I found out that Github can host content for free at [Github Pages](https://pages.github.com/).  This allows me some flexibility in how the content will look and feel, but for a great price of free.  Here is how it works:

You want to use a thing called [Jekyll](https://jekyllrb.com/).  Jekyll is actually built into github pages and what it does is it takes your markdown content that is checked into github and it builds it.  This is much like how you would build a nodejs web server, using grunt/gulp/etc, but this technology uses Ruby behind the scenes instead.  

>>>> Pro Tip:  you can even use this on Windows subsystem for Linux.  Just make sure you use the argument ```jekyll s --force_polling``` .  The windows subsystem does not have the same file watcher capabilities, so the program must watch the files by polling.

All I have to do is post a markdown file in my _post folder and github takes care of the rest.  You might be wondering if there is themes available.  Of course!  You can edit css, html and javascript directly or you can visit this site: http://jekyll.tips/templates/ and get templates there.  Thats what I did.  

If you want to have a rich blog experience but without the maintenance, Github pages and Jekyll might be worth a try.  Can't hurt because its FREE.
 



