---
id: 47
title: What is the Right Amount of Unit Tests
date: 2013-09-01T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/What_is_the_Right_Amount_of_Unit_Tests
permalink: /2013/09/01/what-is-the-right-amount-of-unit-tests/
categories:
  - unit testing
tags:
  - unit testing
---
 <p> For a while now, I have been asking, &#8220;What is the right amount of unit tests?&#8221; There are some debates about 200 tests covering 20% is better than covering 75%, but what does that really mean? I will explore some of that now. </p> <p> I have been looking at some articles from <a href="http://martinfowler.com/bliki/TestCoverage.html">Uncle Bob, Martin Fowler</a> for some guidance. He makes mention that high unit test coverage doesn&#8217;t provide a good indication that you have tested your application. A lower test coverage percentage is better than a higher one, if the number of tests is equal. But I have been thinking, well what is something that can be measured then? </p> <p> It hit me like a brick, well of course the answer is Cyclomatic Complexity. It makes sense, what are you testing? The different choice your code goes through is exactly what you should be making tests about. Martin Fowler makes mention that if you test a certain part of your code too much, then it makes refactoring a chore. This is why you need to test based on Cyclomatic Complexity, so you don&#8217;t test more than what is necessary. </p> <p> The only other parts that don&#8217;t fit into this is testing throwing exceptions. These are the added logic that needs to be accounted for, after testing Cyclomatic complexity. But otherwise, use the ratio of Cyclomatic complexity with the test coverage and unit tests you create. This will give you an even better idea of whether your unit tests are doing what you want. </p> <p> Note, testing logging sucks and other things that &#8220;don&#8217;t really matter for business rules&#8221;. This should also be taken into account with your test cases. </p>