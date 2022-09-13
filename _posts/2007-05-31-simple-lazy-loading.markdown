---
layout: post
title: "Simple Lazy Loading"
date: 2007-05-31 16:06:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Simple-Lazy-Loading"
---
<!-- more -->

<p>Lately, I&rsquo;ve noticed a lot of people who are not careful about how they load objects. Managing objects is a fundamentally important part of software development.</p>
<p>Lets say for example I have an integer in the query string, and I need to use this number in a few places on my page. Well it is obviously inefficient and an ugly process to check the query string and parse the value into an integer every time I want to access that number. I could also at the beginning just grab the number, but this would become a problem if I rearranged things. There is also a chance the execution will not require even checking the query string, and then I will have loaded that value for no reason.</p>
<p>This is a very simple and easy way of retrieving an number from a query string.</p>
<p>private&nbsp;int _pageId = 0;<br /> private&nbsp;int PageId<br /> {<br /> &nbsp;&nbsp;&nbsp; get<br /> &nbsp;&nbsp;&nbsp; {<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if (_pageId == 0)<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; int myInt;<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;int.TryParse(Request.QueryString[&rdquo;pageId&rdquo;], out myInt);<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_pageId = myInt;<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return _pageId;<br /> &nbsp;&nbsp;&nbsp; }<br /> }</p>
<p>With this I no longer have to parse the query string or have the ugly Request.QueryString all through my code. One nice thing is that once I have successfully loaded a valid pageId it will not reference the query string again. As you can probably see this is also helpful when making a database call or any other time consuming work to get some data.</p>
<p>This is very useful for more complex data structures. When the object being loaded is large we want to avoid loading it if we do not have to and also loading it more than once. This is what we can achieve here. In that case you would compare the value to null instead of 0. This will let you know if it has yet been loaded.</p>
