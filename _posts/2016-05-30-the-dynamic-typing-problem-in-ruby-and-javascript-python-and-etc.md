---
id: 225
title: 'The dynamic typing problem in Ruby (and javascript, python, and etc&#8230;)'
date: 2016-05-30T05:13:21+00:00
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=225
permalink: /2016/05/30/the-dynamic-typing-problem-in-ruby-and-javascript-python-and-etc/
categories:
  - .net
  - javascript
  - ruby
  - web
tags:
  - dynamic
  - dynamic languages
  - interface
  - javascript
  - OOP
  - ruby
  - typescript
---
In working with Ruby the past 2 months, I have noticed my normal programming mojo was off.  While I was able to navigate the codebase, I was unsure what I was doing.  I thought that maybe .net was the only thing I could ever program in because I wasn&#8217;t getting this whole ruby thing.  But that isn&#8217;t it, I programmed a bunch in javascript (node.js) and never had a problem.  Maybe I can&#8217;t tolerate other people&#8217;s code?  No, I have worked in the software industry for more than 9 years and haven&#8217;t had a problem and let me tell you, I have seen some shit code.

Then it hits me, of course this code is hard to read, cause I don&#8217;t know the domain.  So, I talk with the fellow programmers on my team.  Nope, I have the right assumptions and I&#8217;m asking the right questions.  So, why am I so unproductive in switching to Ruby?

Dynamic languages suck in one regard, there is no type system!

There, I said it.  Mind you, I think it is a plus too, but it sucks.  I don&#8217;t think they need a full blow type system, but there is a lacking in the interface department.  For instance, look at this code:

<pre class="lang:default decode:true">def parse_html_for_escape_characters(html, options)
  ...
end</pre>

Sweet! I need a function to parse my html and transform the escaped characters.  Simple enough, but there are 3 questions about that code, what is the return and what are the 2 parameters being passed in?  I could think that the return type is a new string of html, but it could be an object.  Same for the html variable I passed in.  What about that options variable?  Who the fuck knows what that object is.

There are 2 schools of thought on this, one is my code should be expressive enough to tell what it is.  The other is that you should have documentation.  BOTH ARE WRONG IN RUBY.  If your code was expressive enough, it would have some type information to tell me what to expect when calling this method.  I could read the implementation of the code, but isn&#8217;t that what OOP is suppose to stop me from?  I shouldn&#8217;t have to read the implementation of the code because it could be a library, or code I don&#8217;t have access to.  Reading the implementation of the code shouldn&#8217;t be the go to answer.  Worst yet, when the options parameter gets passed around like shots at a party.  Who knows when and where methods or properties you need to call are actually at.

Equally as dubious, you should have documentation for the code.  I agree, if you are discipline enough you should have code documentation all over the place.  But remember, developers are lazy sons of bitches.  They won&#8217;t document shit unless it is a public method, and worse yet, a private method.  Also, think about your boss who doesn&#8217;t give a shit about documentation, they just want to ship features.  Mind you this is a separate discussion, but the fact remains that developers won&#8217;t document their code and the function signatures are bullshit for conveying the correct usage of a function.

Interfaces are solutions!?

I get it, nobody likes Java, but there is a point to type systems.  They warn you about a bone headed compiler error.  Immediately!  One argument against type systems is that this does not add any code correctness, and only unit tests would provide that.  True to an extent, but what code do you work on that provides 100%+ code coverage?  Not only that, are you wasting time writing unit tests that would have been covered by a compiler in the first place?

Look, I get it, everyone wants to think that their language is the best for everything forever.  But its not, while every language is slightly different, they come from the same family of languages( function, object oriented, etc.) and they are either statically or dynamically typed.  So, now that we got off our high horse about how Ruby is the same as any other OOP language (c++/java/c#), let&#8217;s think about some solutions to our above problem.

Interfaces provide a mechanism for us programmers to know where to color in the lines of a painting.  They also have a hidden benefit to enforce a developer, who otherwise has zero time to document, to document.  This guy:  <http://victorsavkin.com/post/44861723903/i-wish-ruby-had-interfaces>  has a good article on what it provides us to get interfaces, and he programmed in dynamic languages as much as me in .net.  I think it is important to take away what advantages we can give ourselves in a language, instead of shutting down and saying we can&#8217;t.  We have always done it this way is not an excuse to not change.

If you want to include more developers to your platform or take the language seriously, it needs to adapt to changes.  Look at javascript.  It has a transpiler called Typescript which brings a shitload to the table in terms of types.  Microsoft made it, so everyone hates it.  But guess what, google is using it for Angular.js. The main reasons? Because types make things clearer.  Maybe Ruby needs something like this so I don&#8217;t have to go through the spaghetti of shit code at work.