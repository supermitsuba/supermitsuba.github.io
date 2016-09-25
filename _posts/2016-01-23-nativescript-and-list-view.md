---
id: 10
title: Nativescript and List View
date: 2016-01-23T00:00:00+00:00
author: Jorden
layout: post
guid: http://www.fbombcode.com/title/Nativescript_and_List_View
permalink: /2016/01/23/nativescript-and-list-view/
categories:
  - javascript
  - mobile
tags:
  - javascript
  - nativescript
---
<div>
  <p>
    I have taken a long break from writing. Not that I didn&#8217;t have anything to write, but just needed to break. Now that I am back to writing, the article I have for today is about NativeScript. NativeScript is a Abstraction to allow you to write javascript and have that code compile down to an IOS device. What I have been working on how to use a List View.
  </p>
  
  <p>
    I have been working on making my blog into a mobile app. Nothing I am publishing, but it would be cool to see how it could be done. What would be awesome is if I could write it once and have it work on IOS and Android. So, that is where NativeScript came in. It has been really easy to work with the UI tools, because they are all XML based. For Example:
  </p>
  
  <pre class="formatCode"><span class="tag">&lt;Page</span><span class="pln"> </span><span class="atn">xmlns</span><span class="pun">=</span><span class="atv">"http://schemas.nativescript.org/tns.xsd"</span><span class="pln"> </span><span class="atn">loaded</span><span class="pun">=</span><span class="atv">"latestPageLoaded"</span><span class="tag">&gt;</span><span class="pln">
  </span><span class="tag">&lt;DockLayout</span><span class="pln"> </span><span class="atn">stretchLastChild</span><span class="pun">=</span><span class="atv">"true"</span><span class="tag">&gt;</span><span class="pln">
    </span><span class="tag">&lt;ListView</span><span class="pln"> </span><span class="atn">dock</span><span class="pun">=</span><span class="atv">"top"</span><span class="pln"> </span><span class="atn">items</span><span class="pun">=</span><span class="atv">"{{articles}}"</span><span class="pln"> </span><span class="atn">itemTap</span><span class="pun">=</span><span class="atv">"detail"</span><span class="tag">&gt;</span><span class="pln">
	    </span><span class="tag">&lt;ListView.itemTemplate&gt;</span><span class="pln">
            </span><span class="tag">&lt;GridLayout</span><span class="pln"> </span><span class="atn">columns</span><span class="pun">=</span><span class="atv">"*, auto"</span><span class="pln"> </span><span class="atn">rows</span><span class="pun">=</span><span class="atv">"auto, *"</span><span class="pln"> </span><span class="tag">&gt;</span><span class="pln">
               </span><span class="tag">&lt;Button</span><span class="pln">   </span><span class="atn">row</span><span class="pun">=</span><span class="atv">"0"</span><span class="pln"> </span><span class="atn">col</span><span class="pun">=</span><span class="atv">"1"</span><span class="pln"> </span><span class="atn">text</span><span class="pun">=</span><span class="atv">"+"</span><span class="pln"> </span><span class="atn">tap</span><span class="pun">=</span><span class="atv">"hideSummary"</span><span class="pln"> </span><span class="atn">visibility</span><span class="pun">=</span><span class="atv">"{{ showDetails ? 'visible' : 'collapsed' }}"</span><span class="pln"> </span><span class="tag">/&gt;</span><span class="pln">
  	           </span><span class="tag">&lt;Label</span><span class="pln">    </span><span class="atn">row</span><span class="pun">=</span><span class="atv">"0"</span><span class="pln"> </span><span class="atn">col</span><span class="pun">=</span><span class="atv">"0"</span><span class="pln"> </span><span class="atn">text</span><span class="pun">=</span><span class="atv">"{{Title}}"</span><span class="pln"> </span><span class="atn">height</span><span class="pun">=</span><span class="atv">"50"</span><span class="pln"> </span><span class="tag">/&gt;</span><span class="pln">
               </span><span class="tag">&lt;TextView</span><span class="pln"> </span><span class="atn">row</span><span class="pun">=</span><span class="atv">"1"</span><span class="pln"> </span><span class="atn">col</span><span class="pun">=</span><span class="atv">"0"</span><span class="pln"> </span><span class="atn">colSpan</span><span class="pun">=</span><span class="atv">"2"</span><span class="pln"> </span><span class="atn">text</span><span class="pun">=</span><span class="atv">"{{Summary}}"</span><span class="pln">
                         </span><span class="atn">wordWrap</span><span class="pun">=</span><span class="atv">"true"</span><span class="pln"> </span><span class="atn">id</span><span class="pun">=</span><span class="atv">"summary"</span><span class="pln"> </span><span class="atn">visibility</span><span class="pun">=</span><span class="atv">"{{ showDetails ? 'visible' : 'collapsed' }}"</span><span class="pln"> </span><span class="tag">/&gt;</span><span class="pln">
            </span><span class="tag">&lt;/GridLayout&gt;</span><span class="pln">
	    </span><span class="tag">&lt;/ListView.itemTemplate&gt;</span><span class="pln">
    </span><span class="tag">&lt;/ListView&gt;</span><span class="pln">
  </span><span class="tag">&lt;/DockLayout&gt;</span><span class="pln">
</span><span class="tag">&lt;/Page&gt;</span></pre>
  
  <p>
    The neat thing about this is that it describes BOTH ios and Android. So, what does it do? It shows a list of articles. The biggest feature of this is that it will<br /> allow you to click a row and expand details on it. How that is accomplished is by looking at the ListView tag. There is an attribute called itemTap, this will trigger a function that will make the details show up.
  </p>
  
  <pre class="formatCode"><span class="pln">exports</span><span class="pun">.</span><span class="pln">detail </span><span class="pun">=</span><span class="pln"> </span><span class="kwd">function</span><span class="pun">(</span><span class="pln">args</span><span class="pun">)</span><span class="pln"> </span><span class="pun">{</span><span class="pln">
	</span><span class="kwd">var</span><span class="pln"> item </span><span class="pun">=</span><span class="pln"> args</span><span class="pun">.</span><span class="pln">view</span><span class="pun">;</span><span class="pln">
	</span><span class="kwd">var</span><span class="pln"> index </span><span class="pun">=</span><span class="pln"> args</span><span class="pun">.</span><span class="pln">index</span><span class="pun">;</span><span class="pln">
	articles</span><span class="pun">.</span><span class="pln">getItem</span><span class="pun">(</span><span class="pln">args</span><span class="pun">.</span><span class="pln">index</span><span class="pun">).</span><span class="pln">showDetails </span><span class="pun">=</span><span class="pln"> </span><span class="pun">!</span><span class="pln">articles</span><span class="pun">.</span><span class="pln">getItem</span><span class="pun">(</span><span class="pln">args</span><span class="pun">.</span><span class="pln">index</span><span class="pun">).</span><span class="pln">showDetails</span><span class="pun">;</span><span class="pln">
	item</span><span class="pun">.</span><span class="pln">parent</span><span class="pun">.</span><span class="pln">refresh</span><span class="pun">();</span><span class="pln">
</span><span class="pun">}</span></pre>
  
  <p>
    So this code shows that we get some information from the args. Args is an object that represents the tag object in code that called that function. In our case that would be the list view row object. We find out the index that was changed, but we dont modify the object, instead we modify what is called an observable. An observable keeps track when data is updated, then updates the UI. So in our case we have an array of articles that are observables. We would like to update the index in articles so that showDetails hides and shows certain controls. If we look back at the xml, it is the button and textview. That is because the button is to link to the full article, and the textview is to show the summary in the row, if the user clicks on it.
  </p>
  
  <p>
    The reason I talk about this is because originally, I wanted to have a link that would expand the row. Unfortunately, that link could easily know what index it was. The index is important because we have to update our observables, and not the object in the XML. After I learned that lesson, I remembered that I am in a MVVM type of environment and that means that articles observable is the way to not only load data, but also change the view (the view model). Anyways, if you want to see the code, I have it on Github at <a href="https://github.com/supermitsuba/node.blog.mobile">node.blog.mobile</a>
  </p>
</div>