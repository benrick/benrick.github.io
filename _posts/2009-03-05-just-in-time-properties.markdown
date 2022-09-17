---
layout: post
title: "Just In Time Properties"
date: 2009-03-05 20:07:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Just-In-Time-Properties/"
---
<!-- more -->



<p>Properties with backing fields can easily be null. I often see properties which check the backing field to see if it is null. This is commonly done with an if statement with one line of initialization. One way to get around this is to use the coalescing operator in C#. If we use this in combination with an expressions, which might be a method, we are able to easily handle this property with one line.</p>
<p>Here is an example of what I am talking about.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;"><span style="color: #0000ff;">private</span> SomeType _someObject;
<span style="color: #0000ff;">public</span> SomeType SomeObject 
{ 
    get 
    { 
        <span style="color: #0000ff;">return</span> _someObject ?? (_someObject = giveMeSomeObject()); 
    } 
}</pre>
</div>
<p>Notice how short and concise this is. I am able to with one line which is very clear handle this common scenario. Sure it doesn't always match this exactly, but I see plenty of properties people write where they do something similar.</p>
<p>I think that is very elegant and a lot nicer than doing this older style.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;"><span style="color: #0000ff;">private</span> SomeType _someObject;
<span style="color: #0000ff;">public</span> SomeType SomeObject 
{ 
    get 
    { 
        <span style="color: #0000ff;">if</span> (_someObject == <span style="color: #0000ff;">null</span>)
        {
            _someObject = giveMeSomeObject(); 
        }
        <span style="color: #0000ff;">return</span> _someObject;
    } 
}</pre>
</div>
