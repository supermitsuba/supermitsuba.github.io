---
id: 48
title: One way to go about SOA
date: 2013-08-25T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/One_way_to_go_about_SOA
permalink: /2013/08/25/one-way-to-go-about-soa/
categories:
  - .net
  - general
tags:
  - .net
  - service oriented architecture
  - SOA
---
 <p> I had to give a presentation at work about SOA. I did a little reading on Command-Query Segregation Responsibility and how to fuse these things together to give someone the scaling they may need. Enterprise software isn&#8217;t that bad, right? </p> <p> Say you have some code, like so: </p> <pre class="formatCode"> class Repository<t> : where T class { public void Insert(T obj); public void Update(T obj); public void Delete(T obj); public ICollection<t> GetAll(Func<bool, T> whereClause); } </pre> <p> What command-query segregation responsibility says is to just split up all the queries and commands into separate classes, modules, etc. A query is something that gets back data, so think of a function that returns data like GetAll. A command is something that alter&#8217;s state, like inserts, updates and deletes. Now let&#8217;s see a separated class: </p> <pre class="formatCode"> class CommandRepository<t> : where T class { public void Insert(T obj); public void Update(T obj); public void Delete(T obj); } class QueryRepository<t> : where T class { public ICollection<t> GetAll(Func<bool, T> whereClause); } </pre> <p> What does this have to do with SOA? Well Commands and Queries are 2 separate functions that you can separate out and scale REALLY well. Now, if you listen to some videos, or read post from <a href="http://www.udidahan.com/2009/12/09/clarified-cqrs/">Udi Dahan</a>, he says to use a message queue, instead of just sql. He says to use both of these together because one scales horizontally well (message queues) and the other does not (Sql database). The benefits of a message queue are as follows: </p> <p> <ol> <li>1 Reliable – Delivery Guaranteed</li> <li>2 Scalable</li> <li>3 Resilient – compared to SQL</li> <li>4 Decoupling</li> <li>5 Interoperable</li> </ol> </p> <p> The downside of all of this is that message queues are not instant. They do not have transactions. If you can deal with these constraints, and most of the time you can. Then look into a message queue. Whoa, Jorden, you kinda went on a tangent, WTF? Ok, here is an example layout with all of this: </p> <p> <ol> <li>UI wants to add stuff</li> <li>Command inserts into queue</li> <li>When a service can, then inserts results into database </li> <li>UI wants to see status of stuff</li> <li>Query checks database if it is done</li> <li>If it isn’t done yet, the service that is processing it will let you know.</li> </ol> </p> <p> If all of this still sounds fuzzy, read up more about CQRS and how it fits into SOA pattern. Here is a start, I got a few articles for you guys to check out: <a href="http://martinfowler.com/bliki/CQRS.html">Martin Fowler</a> and <a href="http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/">Greg Young</a> have some good articles about the subjects. </p>