---
id: 53
title: Better than MySQL. NoSQL
date: 2013-07-15T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Better_than_MySQL._NoSQL
permalink: /2013/07/15/better-than-mysql-nosql/
categories:
  - database
tags:
  - databases
  - NoSQL
---
 <p> In Node.js, I had some frustrations with the MySQL libraries out there. So, I decided to go NoSQL to give it a try. I found out there were lots of things I needed to think about to make the jump to NoSQL. </p> <p> First things first, remember that NoSQL does not replace EVERYTHING. Relational databases are great at relationships. They also are more efficient at storing data. But sometimes, you dont need those things. In my case, Microsoft Azure is pretty cheap on storage, it&#8217;s free communication between the web server and the database, and the blog database for NoSQL can be easily translated. Before we can translate, we have to see how they work first. </p> <p> In Azure Tables, there are 2 Keys, one is a <strong>partition key</strong> and a <strong>row key</strong>. A <strong>partition key</strong> is a key Azure uses to split the data between servers. In my blog, I used categories to spilt the data. This will allow Azure load balance data for faster results. Now, you don&#8217;t want to split it too much, as this will make it harder to return the data during the join. A nice balance will work. Next, is <strong>row key</strong>. This is like an identity column, except it does not auto increment. The trick around this is to use the ticks from date time. Now, if you have something that is operating on multiple times per millisecond, then you may want to use a Relational database, or another key scheme. </p> <p> Lastly, how do you create a NoSQL database? The approach I took was to take all the simple tables, you know the ones, the ones that contain very few columns, like a category. Really the tables resemble stored procedures that you would create in a relational database, but now in NoSQL. This is because in NoSQL, the idea is that returning full object graphs is faster than a join from a relational database. </p> <p> The application level code is very similar, except that you need to pull back a large data set back, then parse the data to what you want exactly. In node.js, I use underscore.js to filter, where clause and find the items that I want to get. Now my site looks like it is responding faster, and I&#8217;m hoping that the bill is cheaper, too. We shall see. </p>