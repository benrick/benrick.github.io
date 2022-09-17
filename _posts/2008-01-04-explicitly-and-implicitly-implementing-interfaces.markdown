---
layout: post
title: "Explicitly and Implicitly Implementing Interfaces"
date: 2008-01-04 21:26:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Explicitly-and-Implicitly-Implementing-Interfaces/"
---
<!-- more -->



<p>I read an interesting blog post from <a href="http://aspadvice.com/blogs/joydip/default.aspx" target="_blank">Joydip Kanjilal</a> where he described <a href="http://aspadvice.com/blogs/joydip/archive/2008/01/04/Put-your-interfaces-to-best-use_2100_.aspx" target="_blank">an interesting little trick with interfaces</a>. I, being a bit of a fan of interfaces, read the post and thought I'd throw my $0.02 in also. I couldn't pass up an opportunity to talk about interfaces. He first shows simply how to create an interface and how to implement the interface implicitly. The difference between implicitly and explicitly writing this code is what creates the different circumstances Joydip shows in his demonstration.</p>
<p>I'll start where he did with an interface. I'll name my interface <em>IBloggable</em> and I'll have a class <em>PostContent</em> which implements the interface.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">interface</span> IBloggable
{
    <span style="color: #0000ff;">void</span> SendToBlog();
}

<span style="color: #0000ff;">public</span> <span style="color: #0000ff;">class</span> PostContent : IBloggable
{
    <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> SendToBlog()
    {
        <span style="color: #008000;">// Send this content to a blog</span>
    }
}</pre>
</div>
<p>Ok so this is the implicit implementation of the interface. Basically all I mean when I say explicitly and implicitly is whether or not you're going to define everything. If I define something explicitly I have defined everything and made it perfectly clear. I have included every detail required for precise interpretation. Notice above I have not specified to which class that method applies. So here I will now define the same thing explicitly and make sure that the <em>SendToBlog</em> method specifies to what it belongs.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">class</span> PostContent
{
    <span style="color: #0000ff;">void</span> IBloggable.SendToBlog()
    {
        <span style="color: #008000;">// Send to blog only for the interface not for implementing classes</span>
    }
}</pre>
</div>
<p>As Joydip pointed out so well, the first one will work in either of these circumstances, but our explicitly defined method will only work in the first example.</p>
<p><strong>Example 1:</strong></p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">IBloggable b = <span style="color: #0000ff;">new</span> PostContent();</pre>
</div>
<p><strong>Example 2:</strong></p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">PostContent b = <span style="color: #0000ff;">new</span> PostContent();</pre>
</div>
<p>From this we can note a couple of other interesting points here.</p>
<p>If we implement interface methods implicitly, we are able to use the method with objects of the interface type or of the implementing class type. If we are implementing explicitly, the method will only work on the interface. The great benefit of only allowing instances of the interface to use the method is that it encourages you to write more dynamic and maintainable code since you'll be using the interface everywhere you'll be able to switch your implementing classes quickly and easily.</p>
<p>This is one of many great ways to write better code. I always explicitly implement my interfaces. I've not had it bite me yet, so if anyone knows a reason to <em>not</em> explicitly define this code, please let me know.</p>
<p>One nice feature in Visual Studio which makes this nice and easy. Once you specify the interface you want your class to implement you are able to right click on it and choose <em>Implement Interface &gt; Implement Interface Explicitly</em> and it will create the stubs for everything required in order to implement the interface. It will even place it all in a nice code region for you. Observe the code it generates for us in this instance.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">class</span> PostContent : IBloggable
{
    <span style="color: #cc6633;">#region</span> IBloggable Members

    <span style="color: #0000ff;">void</span> IBloggable.SendToBlog()
    {
        <span style="color: #0000ff;">throw</span> <span style="color: #0000ff;">new</span> Exception(<span style="color: #006080;">"The method or operation is not implemented."</span>);
    }

    <span style="color: #cc6633;">#endregion</span>
}</pre>
</div>
<p>Happy coding.</p>
