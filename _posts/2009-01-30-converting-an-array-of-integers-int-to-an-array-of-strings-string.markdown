---
layout: post
title: "Converting an Array of Integers int[] to an Array of Strings string[]"
date: 2009-01-30 09:56:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Converting-an-Array-of-Integers-int-to-an-Array-of-Strings-string/"
---
<!-- more -->



<p>I was working on a code snippet I plan to put into a blog post, and while writing it I needed to convert and array of integers to an array of strings. I try to think of a quick easy way to do this and none comes to mind. Well, I of course know that I could just loop through them and convert them from ints to strings, but that is really lame especially when I want the code to be small so I can put it in a blog post.</p>
<p>So there are a few options that present themselves when you are looking for a method to help you out.</p>
<ul>
<li>Write your own method to solve the problem. (I try to only do this as a last resort. I try to use existing code when possible.)</li>
<li>Ask Google (or any other search engine) for answers posted on forums, blogs, articles, documentation, etc.</li>
<li>Go ask/search on a forum or a <a href="http://stackoverflow.com/" target="_blank">Question and Answer site</a>.</li>
<li>Use intellisense and check some related classes which may hold the answer.</li>
</ul>
<p>In this instance I used the last one. I checked out some classes using intellisense to see what methods were available. I was working with arrays, so the one I checked is the <em>Array</em> class. Array.ConvertAll is what I needed.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;">var intArray = <span style="color: #0000ff;">new</span>[] {1, 2, 3, 4, 5};
<span style="color: #0000ff;">string</span>[] stringArray = Array.ConvertAll(intArray, i =&gt; i.ToString());
</pre>
</div>
<p>That is roughly how I am using it in my code. Notice the nice lambda way of handling the individual object conversion. You can also solve the problem using a full-fledged method call. I just chose this to keep things more compact.</p>
<p>Here is an example using a method to hide the lambda and do the conversion.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;"><span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Main()
{
    var intArray = <span style="color: #0000ff;">new</span>[] {1, 2, 3, 4, 5};
    <span style="color: #0000ff;">string</span>[] stringArray = Array.ConvertAll(intArray, IntToStringConverter());
}

<span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> Converter&lt;<span style="color: #0000ff;">int</span>, <span style="color: #0000ff;">string</span>&gt; IntToStringConverter()
{
    <span style="color: #0000ff;">return</span> i =&gt; i.ToString();
}</pre>
</div>
<p>As usual there are still many other ways to do this, but I'll show you one that just has way too much unnecessary code.</p>
<p>I don't recommend using this example since it really just specifies way more than it needs to. I am just including this to illustrate the many ways to have solved this problem using this same method.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;"><span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Main()
{
    var intArray = <span style="color: #0000ff;">new</span>[] {1, 2, 3, 4, 5};
    <span style="color: #0000ff;">string</span>[] stringArray = Array.ConvertAll&lt;<span style="color: #0000ff;">int</span>, <span style="color: #0000ff;">string</span>&gt;(intArray, 
        <span style="color: #0000ff;">new</span> Converter&lt;<span style="color: #0000ff;">int</span>, <span style="color: #0000ff;">string</span>&gt;(IntToStringConverter));
}

<span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">string</span> IntToStringConverter(<span style="color: #0000ff;">int</span> n)
{
    <span style="color: #0000ff;">return</span> n.ToString();
}</pre>
</div>
<p>Why don't I really like that one? Well to be honest I intentionally made it bad. The "<em>new Converter&lt;int, string&gt;()</em>" part is completely useless. You can remove it completely and the code still works, because we specified already that we are doing int to string. We alternatively could have removed the first <em>&lt;int,string&gt;.</em></p>
<p>Although if I were using an older version of C# I would be forced to use the last one, or I could also use a combination of the second and third one.</p>
<p>Well, we're out of time here today. I hope you've enjoyed this edition of <strong>Finding Stuff Using Intellisense</strong>. This is your host, Brendan Enrick. We've been glad to have you with us today. Join us next time when we....&nbsp; <strong>Find Stuff Using Intellisense</strong>. {queue the ending theme music}</p>
