---
layout: post
title: "Choosing A Dependency Injection Pattern"
date: 2009-05-19 11:02:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Choosing-A-Dependency-Injection-Pattern/"
---
<!-- more -->



<p>There are a few patterns you can follow when writing code which injects dependencies; constructor, property, and method injection. Which way is the best one to use? I don't really know for certain, but I can talk a little bit about the differences and some of the benefits of each. I am sure this behaves as most situations do with certain ones perform better in certain situations.</p>
<h4>Constructor Injection</h4>
<p>In this form of injection we pass the dependency into the object using its constructor. Before creating an instance of our object we have to get instances of all of the dependent objects required by the class and pass them in.</p>
<p>I really like this form of injection because it defines up from what is required to use the object. The constructor is saying up front, "these are what I need in order for you to create an instance of me, so if you don't have them bugger off".</p>
<div>
<pre style="line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: consolas, 'Courier New', courier, monospace; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> Car
{
    <span style="color: #0000ff">private</span> ITransmission _trans;
    
    <span style="color: #008000">// Constructor Injection</span>
    <span style="color: #0000ff">public</span> car(ITransmission trans)
    {
        _trans = trans;
    }
}</pre>
</div>
<h4>Property Injection</h4>
<p>This pattern allows you to set the dependency after the instance of your object has been created. I shy away from this type simply because it concerns me that objects might not have their dependencies set if they're not required by the constructor.</p>
<p>I like using property injection in certain circumstances. I like using them in combination with constructor injection. I use them this way in instances where the dependent object might need to change.</p>
<div>
<pre style="line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: consolas, 'Courier New', courier, monospace; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> Car
{
    <span style="color: #008000">// Property Injection</span>
    <span style="color: #0000ff">private</span> ITransmission _trans;
    <span style="color: #0000ff">public</span> ITransmission Transmission
    {
        get { <span style="color: #0000ff">return</span> _trans; }
        set { _trans = <span style="color: #0000ff">value</span>; }
    }
}</pre>
</div>
<h4>Method Injection</h4>
<p>If a dependency is really only needed by one method it is nice to put it in the method signature. This lets everyone know the method requires it. If we were using property injection we might have needed to know in advance to set the property. This type allows you to have one less property to set or one less parameter in the constructor.</p>
<p>Also if a method sometimes needs different instances of the dependency this is the way to go.</p>
<div>
<pre style="line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: consolas, 'Courier New', courier, monospace; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> Car
{    
    <span style="color: #008000">// Method Injection</span>
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">void</span> Shift(ITransmission trans, ShiftDirection direction)
    {
        <span style="color: #008000">// do stuff here</span>
    }
}</pre>
</div>
<h3>Putting Them Together</h3>
<p>As I said moments ago, I try to use these techniques collectively. It allows me to leverage the benefits of each. I think as a general rule you should try to tend towards one of them. I've seen people make great use of each of them.</p>
<p>If you can keep your dependencies to a minimum and localized to certain methods then method injection works pretty well. Property injection requires that you be more careful to make sure the dependencies are being set, but can eliminate a lot of clutter which can be found with method and constructor injection. Constructor injection is nice because it documents up front in the method signature what dependencies exist in the class.</p>
