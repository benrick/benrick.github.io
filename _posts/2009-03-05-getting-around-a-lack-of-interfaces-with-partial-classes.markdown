---
layout: post
title: "Getting Around a Lack of Interfaces With Partial Classes"
date: 2009-03-05 16:58:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Getting-Around-a-Lack-of-Interfaces-With-Partial-Classes/"
---
<!-- more -->

<p>One pain point which comes along often when working with others' libraries are the classes that are not open and implementing interfaces. A lot of the classes we developers use every day implement no interfaces. Since the class is out of my control, I obviously cannot give it an interface, so I need some other way to work with it. This creates a problem when we need to mock out the class. There are ways in which we can get around this though.</p>
<h4>Wrapping Classes</h4>
<p>In my opinion, the most dependable workaround to be able to mock out and test a class is creating an interface-implementing wrapper around the class we want to mock and using that instead. This one works very well, but it forces you to create an interface and a class even though there is already a class in existence.</p>
<h3>Partial Class Interface</h3>
<p>As the name of this post says, partial classes can be very important when presented with this problem. If a class is not implementing an interface, but it is a partial class, you can give it an interface it is already implement.</p>
<p><strong><em>If a class is partial you can give it an interface which defines the methods it already implements.</em></strong></p>
<p>So now I am going to present an example. For this example, we will have a class called "BrendanMailer". This class is not implementing an interface, which means that if we want to remove this dependency we need to come up with some solution that lets us program against an interface.</p>
<div>
<pre style="line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: consolas, 'Courier New', courier, monospace; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">partial</span> <span style="color: #0000ff">class</span> BrendanMailer
{
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> SendEmail()
    {
    }

    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> SomeNonImportantMethod()
    {
    }
}</pre>
</div>
<p>For this we could obviously use the wrapper method, but we can also do something a lot easier. Thanks to the smart creator of that class, there is a partial keyword in there. This allows us to leverage a very powerful trick, because we can now create our own interface. The interface can include only the methods we want it to, which is in some ways better than if the interface had been predefined.</p>
<div>
<pre style="line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: consolas, 'Courier New', courier, monospace; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">interface</span> IBrendanMailer
{
    <span style="color: #0000ff">void</span> SendEmail();
}</pre>
</div>
<p>So now I have a custom interface to work with and program against. I now just add that into another part of this partial class and tell that one I am implementing the interface. I don't have to implement the methods, because they already are implemented in the original part of this partial.</p>
<div>
<pre style="line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: consolas, 'Courier New', courier, monospace; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">partial</span> <span style="color: #0000ff">class</span> BrendanMailer : IBrendanMailer
{
}</pre>
</div>
<p>In my production code I will inject the BrendanMailer class, and in the tests I will mock it out or use a fake or something. This is very powerful and doesn't clutter much at all, because I can hide this partial away in a folder in my project and ignore it for a long time.</p>
