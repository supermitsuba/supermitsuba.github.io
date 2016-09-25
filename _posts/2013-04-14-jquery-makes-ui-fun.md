---
id: 63
title: JQuery makes UI fun
date: 2013-04-14T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/JQuery_makes_UI_fun
permalink: /2013/04/14/jquery-makes-ui-fun/
categories:
  - HTML
  - javascript
  - web
tags:
  - javascript
  - jquery ui
  - web
---
 <p> Just recently I have been whipping up a UI with drag and drop. Windows forms and WPF are sort of a pain for a simple drag and drop scenario. Then add in a sortable UI ability and it makes me cry hurt. So, in comes in JQuery UI. This library rocks, and let me show you why! </p> <p> So, first question: How do I make these things dragable? Here is how: </p> <pre class="formatCode"> <link href="http://code.jquery.com/ui/1.10.2/themes/smoothness/jquery-ui.css" rel="stylesheet" type="text/css" /> $('.dragableItem').draggable(); </pre> <div> <link href="http://code.jquery.com/ui/1.10.2/themes/smoothness/jquery-ui.css" rel="stylesheet" type="text/css" /> <div class="dragableItem" style="width:200px;height:200px;border-style:solid;border-width:5px;background-color:red;"> my draggable box </div> </div> <h3> Draggable Demo: </h3> <p> Super easy, just select your element and call draggable. Also, make sure to include the jquery library. Now along with draggable, why not add dropable? Like so: </p> <pre class="formatCode"> $('.droppable').droppable( { activeClass: "ui-state-default", hoverClass: "ui-state-hover", accept: ":not(.ui-sortable-helper)", drop: function (event, ui) { alert('Dropped here.'); } } ); </pre> <h3> Dropable Demo: </h3> <div> <div class="droppable" style="width:200px;height:200px;border-style:solid;border-width:5px;background-color:blue;"> my dropable box </div> <div> <p> Awesome, just got drag and drop in a few pieces of code. </p> <p> Ok, now lastly, let&#8217;s throw together some sortable stuff: </p> <pre class="formatCode"> $('.sortable').sortable({items:'li'}); <ol class='.sortable'> <li> task 1 </li> <li> task 2 </li> <li> task 3 </li> <li> task 4 </li> </ol> </pre> <h3> Sortable Demo: </h3> <div> <ol class='sortable'> <li> task 1 </li> <li> task 2 </li> <li> task 3 </li> <li> task 4 </li> </ol> </div> <p> Bam, we got some advanced UI features, and done in less than 10 lines of code. Try it out! </p>