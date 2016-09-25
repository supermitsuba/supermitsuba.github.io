---
id: 30
title: Difference between Async and Task
date: 2014-06-14T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Difference_between_Async_and_Task
permalink: /2014/06/14/difference-between-async-and-task/
categories:
  - .net
tags:
  - .net
  - async
  - task
  - threading
---
 <p> What are the differences between Async and Task? I think this is something to analyze in finding out how it might compare Erlang to F#. </p> <p> Josh from work told me of an <a href="http://ayende.com/blog/166913/mixing-sync-async-calls?Key=7e7ebf97-5b7a-4b46-b906-4fdada2e6388">article</a> by Oren Eini, the creator of NHibernate and Raven DB. The gist of it was that Task, which is the preferred method of creating threads, was not great to use with HttpClient. Instead, the article swapped it for async, and it sped up like a pro! Why? Threading makes everything awesome right? Sorta. This gets back to IO vs CPU bound threading. </p> <p> IO bound processing is something that is waiting for network, disk or some other task that calls in and out of the process. CPU bound processing is like crunching Fibonacci sequence. IO bound processing, you have to wait because no matter how many CPU&#8217;s you have, it will not speed up the network or disk. CPU bound processing needs, well the CPU. </p> <p> Knowing these 2 concepts, there is a difference between being asynchronous and being multi-threaded. Async keyword actually runs your code synchronously, until it finds await. When await is found it adds in code to pause that thread and not block any other thread from passing messages to it. A concept that is familiar in node and Erlang. When the operation returns, it knocks out the operations. This is done, without the use of ThreadPool. There is a cool article on it on MSDN <a href="http://blogs.msdn.com/b/pfxteam/archive/2012/04/12/10293335.aspx">here</a>. Task Parallel Library, on the other hand, spins up heavy ass threads that take time to create, which may cause slow processing. </p> <p> Going back to Oren&#8217;s article, async isn&#8217;t creating more threads, it is just waiting for responses and giving answers when it gets a result back. The task example was spinning up ALL 500 threads at once, and it took a while. When Oren put the async in the Task Factory start, it made it fast again because it wasn&#8217;t spinning up 500 threads, but the &#8220;same&#8221; thread 500 times. I put quotes there because ThreadPool, behind the scenes, will reuse the thread. </p> <p> To me, sounds like Erlang is great for this IO communication, because it can send and receive massive amounts of messages. F# can do this too, but MailboxProcessor and Async only cover 2 of the advantages of how it can process insane amounts of messages. I think in the next articles I will start looking into creating separate standalone processes and distribution models from Erlang. Maybe F# has something? </p>