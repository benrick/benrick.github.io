---
layout: post
title: "Parameter Order Should Be Consistent"
date: 2009-01-27 13:10:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Parameter-Order-Should-Be-Consistent", "/post/parameter-order-should-be-consistent"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>I was looking at a piece of code recently and noticed that someone was checking for a null parameter and throwing an ArgumentException, so I figured since ArgumentNullException inherits from ArgumentException I would just replace it with the more specific exception. Little did I know that Microsoft has a wee little bit of a problem with consistency on these.</p>
<p>With ArgumentExceptions it is important to have a message as well as specify which parameter is causing the trouble, so there are 2 string parameters in the ArgumentException constructor. What you might not know if you haven't switched one to the other is that <em>they changed the order of those parameters</em>. What I mean is that you call them like this.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> ArgumentException(<span style="color: #006080">"The Message"</span>, <span style="color: #006080">"paramName"</span>);
<span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> ArgumentNullException(<span style="color: #006080">"paramName"</span>, <span style="color: #006080">"The Message"</span>);
<span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> ArgumentOutOfRangeException(<span style="color: #006080">"paramName"</span>, <span style="color: #006080">"The Message"</span>);
</pre>
</div>
<p>How can they possibly switch those?!?! If I am not mistaken the lower two exceptions actually inherit from the first one, so it is quite surprising that the ordering was not maintained in the second two. I need to keep an eye out for other such inconsistencies while I am working. They obviously can't easily fix it now, because too much code depends on the current ordering. I try to maintain consistence parameter ordering, but I am also not working on a framework.</p>
