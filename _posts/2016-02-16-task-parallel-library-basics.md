---
id: 9
title: Task Parallel Library Basics
date: 2016-02-16T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Task_Parallel_Library_Basics
permalink: /2016/02/16/task-parallel-library-basics/
categories:
  - .net
tags:
  - .net
  - threading
  - tpl
---
<div>
  <p>
    I was reviewing TPL in C# because I wanted a deeper understanding than my previous talks on the subject. I decided to look at it from a different view point, how does the internals work?
  </p>
  
  <p>
    If you read this <a href="https://msdn.microsoft.com/en-us/library/dd537609(v=vs.110).aspx">article</a>, it starts off saying that TPL is an abstraction around ThreadPool. The reason why we want an abstraction is to hide crazy logic from a user and make their lives easier. In the case of TPL, the logic that we are hiding is determining how to schedule in a ThreadPool. Most of the important logic that you would want to manage, that ThreadPools don&#8217;t provide directly are:
  </p>
  
  <ul>
    <li>
      1. Common API for multi-threaded, asynchronous, and parallel code
    </li>
    <li>
      2. Blocking vs Non-Blocking
    </li>
    <li>
      3. Cancellations
    </li>
    <li>
      4. Error Handling
    </li>
    <li>
      5. Scheduling
    </li>
  </ul>
  
  <h3>
    Common API
  </h3>
  
  <p>
    TPL provides a common API for asynchronous and multi-threading that makes it easy to manage our code. The unfortunate thing is that we can forget what type of &#8220;task&#8221; we are running. Here are some tips; 1. For asynchronous, or IO bound code, remember that the thread is not blocked, and is typically on the same thread as the calling code. If you call an asynchronous task, no other thread is created for your application and that thread it is using can be used to do other things, like how UI frameworks work for Windows Forms and WPF.
  </p>
  
  <p>
    2. For multi-threading, or CPU bound code, you are blocking a CPU for &#8220;crunching numbers&#8221;. This would lead to another thread running code. An example would be to do a merge sort, where you give half the list to one thread and half to another thread, join and then merge the results.
  </p>
  
  <p>
    The problem comes when you mix the 2 together, like running a multi-threaded code in a asynchronous task would result in NOTHING. Your code would run syncronious because async task would be executing code (blocking) and would have no input or output to defer for. The other way around would work. If you put asyncronious code on its own thread, it would eventually complete, but it would have a problem with the thread context. This is a common problem in UI frameworks, where you make a web api call on one thread and try to update the UI on the main thread. Very important not to confuse the 2 different types of calls.
  </p>
  
  <h3>
    Blocking vs Non-Blocking
  </h3>
  
  <p>
    So, you may want to know how to &#8220;block&#8221; or &#8220;non-block&#8221; depending on your code&#8217;s workflow. There are 2 different calls to note:
  </p>
  
  <ul>
    <li>
      1. Task.Delay
    </li>
    <li>
      2. Thread.Sleep
    </li>
  </ul>
  
  <p>
    Task.Delay will delay execution in asynchronous code. Thread.Sleep will pause the current thread. Using Thread.Sleep in async code will cause the main thread to halt. Vice versa Task.Delay will allow the thread to continue in the current thread without blocking. This becomes important when you call Task.Wait on the Task and see that it is still running code, even though it has a delay. Be very careful about which type you use, async or parallel.
  </p>
  
  <h3>
    Cancellations
  </h3>
  
  <p>
    Task cancellations are VERY important. Say you have a windows service, if you have multiple threads running, how do you stop the service and the work that those threads are working on? If you do not get it right, your service may hang until those threads are done, if they ever finish. What you can do is give each thread a stop service cancellation token. When a cancellation token use invoked, all the threads will automatically stop what they are doing, and report a status of &#8220;Canceled&#8221;. For a full list of all the states of a thread, check out old <a href="https://msdn.microsoft.com/en-us/library/system.threading.tasks.taskstatus(v=vs.110).aspx">MSDN</a>. To catch all the canceled threads, you could use ContinueWith and filter based on statuses of the thread to know where to route unprocessed requests and shut down.
  </p>
  
  <h3>
    Error Handling
  </h3>
  
  <p>
    Error handling doesnt bubble up in your code and cause unhandled exceptions. Instead, a status of &#8220;faulted&#8221; will appear in your ContinueWith. Here you can actually look at the thread for the Exception property and handle it appropriately. Another nice thing that TPL handles, vs ThreadPool.
  </p>
  
  <h3>
    Scheduling
  </h3>
  
  <p>
    The last topic that TPL does better than ThreadPool is Scheduling. Here, check out all the scheduling options you can have: <a href="https://msdn.microsoft.com/en-us/library/system.threading.tasks.taskcontinuationoptions(v=vs.110).aspx">https://msdn.microsoft.com/en-us/library/system.threading.tasks.taskcontinuationoptions(v=vs.110).aspx</a>. What is cool is that the schedulers will manage MOST scenarios no problem. Do you have a long running process (more than a few minutes)? Set the thread&#8217;s TaskContinuationOptions to LongRunning. Most of the other scheduler options have to do with how the ContinueWith operates. Do you want to run only if a Canceled task comes through, or faulted? Use OnlyOnCanceled or OnlyOnFaulted. Whatever you want TPL to do when and after a Task runs, this is how you specify it and it helps the optimizer behind the scenes handle your code.
  </p>
  
  <p>
    Hopefully explaining TPL this way helps make it clear what it does that is important and what we should keep in mind with Threads and Asyncrhonus work.
  </p>
</div>