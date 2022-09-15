---
layout: post
title: "Return Within a C# Using Statement"
date: 2008-05-22 14:38:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Return-Within-a-C-Using-Statement/"
---
<!-- more -->

<p>While writing some code earlier today I needed to return from within a using statement. Doing these sorts of things always makes me appreciate the using statement and how wonderful it really is, so I decided to write about it here. As many of you know the using statement in C# is a good tool for managing types which will be accessing unmanaged resources. Some examples of these are SqlConnections, FileReaders, and plenty of other similar types. The key to these is that they all implement the IDisposable interface. This means that they all need to be cleaned up carefully after using them.</p>
<p>The using statement is great because it guarantees that the declared object is disposed no matter how the execution completes. Whether you reach the end curly brace marking the end of the using statement, throw and exception, or return from a function, the using statement will call the dispose method and clean up the object.</p>
<p>This was important in my code because I was able to return directly from within the using statement without worrying about whether or not eh dispose method will fire. Whenever I use an object which accesses unmanaged resources I always always always put it in a using statement.</p>
<p>It is very important to use a using statement, because it will give you this guarantee that the object will be disposed of correctly. The object's scope will be for the extent of the using statement, and during the scope of the object it will be read-only if defined in the using statement. This is also very nice, because it will prevent this important object which manages the unmanaged from being modified or reassigned.</p>
<p>This is safe to do, because of how great the using statement is. No matter which return we hit we know the XmlReader will be disposed of correctly.</p>
<div>
<div style="border-style: none; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;"><span style="color: #0000ff;">using</span> (XmlReader reader = XmlReader.Create(xmlPath))</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">{</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">    <span style="color: #008000;">// ... Do some work...</span></pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">    <span style="color: #0000ff;">if</span> (someCase)</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">        <span style="color: #0000ff;">return</span> 0;</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">    <span style="color: #008000;">// ... Do some work...</span></pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">    <span style="color: #0000ff;">if</span> (someOtherCase)</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">        <span style="color: #0000ff;">return</span> 1;</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">}</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">return</span> -1;</pre>
</div>
</div>
<p>Happy coding. Enjoy this powerful tool.</p>
<p><strong>Update: I've posted a follow up to this post with a code sample. It shows that you can <a href="/home/returning-from-inside-a-using-statement/">return from inside of a using statement in C#</a>.</strong></p>
