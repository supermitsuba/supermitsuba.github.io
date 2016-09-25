---
id: 60
title: Add Facebook, Google and Twitter to Your Site
date: 2013-05-05T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Add_Facebook,_Google_and_Twitter_to_Your_Site
permalink: /2013/05/05/add-facebook-google-and-twitter-to-your-site/
categories:
  - HTML
  - web
tags:
  - facebook
  - google+
  - html
  - twitter
  - web
---
 <p> In order to spread the word of this awesome blog site, either that or annoy my friends and family that are not programmers, I started to look into how to integrate the social media sites into my own. Turns out, each of the big 3 have some great API&#8217;s (except facebook, it&#8217;s just ok). So this article describes how to do it. <p> <h2>1) Facebook</h2> <p> I will start here because it is the biggest social website out there. There are 3 different actions you have to keep in mind for facebook: </p> <pre class="formatCode"> 1)+1 or like or whatever 2)Post a message on your wall 3)Send a message to a friend </pre> <p> If you visit the page: <a href="https://developers.facebook.com/docs/reference/plugins/like/">https://developers.facebook.com/docs/reference/plugins/like/</a>, you will see the javascript and html code generator. It can&#8217;t get any easier than selecting a few things and done. The only problem is that some of the functionality may not work as you would expect. Below is the configuration I used, and if you want to have something straight forward, give it a try. </p> <p> <img src="/img/19.png" alt="Facebook" > </p> <p> Send button is key for sending messages, and posting. So if you want to do both of those, select send. I am selecting the button\_count layout, but you could go with the box\_count layout, too. These styles refer to how to present it, horizontal (button\_count) or vertical (box\_count). Standard is ok, but adds a bunch of text about likes and crap. Turn off faces, cause that adds more crap on the site, and if you want to change the other parameters, go for it. Just click ok and you can now add facebook into your site. </p> <p> <strong> SPECIAL NOTE </strong> The URL should be the whole URL, like www.fbombcode.com/title/blahblah. Later with google+, you will not want that to be the case. </p> <h2>2) Twitter</h2> <p> Twitter was easy to set up, but I am afraid I don&#8217;t know what Twitter is used for in social media. I guess a straight forward spam bot. Anyways, to get a twitter thing go here: <a href="https://twitter.com/about/resources/buttons#tweet">https://twitter.com/about/resources/buttons#tweet</a>. Below is a picture of the twitter page: </p> <p> <img src="/img/18.png" alt="Twitter" > </p> <h2>3) Google +</h2> <p> Last, but not least, Google +. Ok, maybe the least used out of the 3, so let&#8217;s see how to add this thing to our site. </p> <p> <img src="/img/17.png" alt="Google +1" > </p> <p> Google + is pretty simple and here is the link to it: <a href="https://developers.google.com/+/web/+1button/?hl=en">https://developers.google.com/+/web/+1button/?hl=en</a>. The one thing to note is that the domain is slapped on automatically, so don&#8217;t add it to the url in the data-href. </p>