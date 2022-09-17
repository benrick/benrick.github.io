---
layout: post
title: "Infinite Loop in a Property"
date: 2007-07-24 22:18:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Infinite-Loop-in-a-Property/"
---
<!-- more -->



<p>Earlier today I was trying to debug a Stack Overflow Exception I was receiving. While debugging I was stepping into the function where the problem was occurring. I could not seem to find the problem. A line of code was calling a function and passing it a few properties as parameters and the value returned by the function was being stored in another property. Without really paying attention to which properties I was stepping into I just clicked through them and then it would throw the exception. I was quite confused and did not even think that it could be a problem with the properties, because I had stepped through them. Well, I as with many other people are annoyed when I am debugging and it steps into a property with no extra logic. Sometimes when I create a property I remember to add the DebuggerStepThrough property. If you don't know what that is I recommend you learn what it is and use it.</p>
<p>When a property has no extra logic in it I obviously don't care to step through its execution it is not the problem.... except when it is.</p>
<p>Someone added a property to a class recently and remembered to add the DebuggerStepThrough property to it. The problem is that this simple property created an infinite loop, which I did not even think to check because some of the properties I was stepping into. Only one did I not step into and it had the problem. It had the following problem.</p>
<p><br /> private int _x;<br /> [DebuggerStepThrough]<br /> public int X<br /> {<br /> &nbsp;&nbsp;&nbsp; get<br /> &nbsp;&nbsp;&nbsp; {<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return _x;<br /> &nbsp;&nbsp;&nbsp; }<br /> &nbsp;&nbsp;&nbsp; set<br /> &nbsp;&nbsp;&nbsp; {<br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:red;">X</span> = value;<br /> &nbsp;&nbsp;&nbsp; }<br /> }</p>
<p>When I tried to set the value I jumped into a recursive loop which the debugger stepped through so it did not even let me see the problem when I was trying to debug. Gotta make sure that doesn't happen. Kind of bad when a property calls itself instead of setting the private member it is supposed to access.</p>
