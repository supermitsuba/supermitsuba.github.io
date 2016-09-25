---
id: 228
title: Parsing Exceptions in Ruby
date: 2016-06-12T03:52:37+00:00
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=228
permalink: /2016/06/12/parsing-exceptions-in-ruby/
categories:
  - ruby
tags:
  - exceptions
  - ruby
---
One thing that is very subtle in Ruby that is an issue is how parsing works.  Say you have an Integer in C#, you would probably code something like this:

<pre class="lang:c# decode:true ">Int32.TryParse(value, out number);</pre>

But, if you look at Ruby, it is something like this:

<pre class="lang:ruby decode:true">def parse_integer(number) 
  Integer(number) 
rescue ArgumentError 
  nil 
end</pre>

While I could do the same logic in C# as in Ruby, the difference is the exception handling.  The problem is that throwing exceptions are way slower to handle.  Worse yet, it does not enforce trying to code as much as you can around exceptions.

I get it that Ruby is meant to get something up and running quickly.  But if we don&#8217;t have good practices like the tryparse function above, then we are writing slower code every time.

</end_rant>