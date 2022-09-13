---
layout: post
title: "Constructors Should Be Simple and Stupid"
date: 2009-08-06 10:43:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Constructors-Should-Be-Simple-and-Stupid"
---
<!-- more -->

<p>There are plenty of commonly known and upheld ideas about how software <em>should</em> be written. There are rules and guidelines professed by many developers which recommend following this design principle or that one. Some are more important than others. Some are easier to find and correct than others.</p>
<p>One such rule that I believe is important to follow is that all constructors remain simple and stupid. This is about as advanced as I believe a constructor should even be.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="border-style: none; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;"><span style="color: #0000ff;">public</span> SomeObject(<span style="color: #0000ff;">int</span> someValue, <span style="color: #0000ff;">int</span> someOtherValue, </pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    ISomeKindOfInterface someKindOfInstance)</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">{</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    _someValue = someValue;</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    _someOtherValue = someOtherValue;</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    _someKindOfInstance = someKindOfInstance</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">}</pre>
<!--CRLF--></div>
</div>
<p>These are merely assignment statements which use the local variables (parameters). We never ever want to call methods in our constructors. This includes calling constructors inside of our constructor. There are very good reasons for this which I will explain in detail.</p>
<h3>&nbsp;</h3>
<p>&nbsp;</p>
<h3>Reasoning for keeping constructors simple</h3>
<p><strong>It is difficult to test classes which do work in their constructors.</strong> When work is done in the constructor it becomes more difficult to manage the object. This is because the mere creation of an instance causes something to happen. This is difficult to handle in unit-testing because you’re trying to keep control of all aspects of the code while testing. Control is required in order to test effectively, because you need to be able to expect certain behavior to exist based on carefully controlled circumstances.</p>
<p><strong>Otherwise dependencies are hidden.</strong> When we instantiate variables inside of a constructor we are “taking a dependency” on the object we are creating. By depending on that code we are limiting ourselves greatly because we are not able to inject anything else. We are not coding against an interface we are working with a concrete class that will be difficult to change or remove.</p>
<p>When we go to test it will be difficult to do so because of these dependencies which have been hidden away in our constructor. Classes should be honest with you. They should tell you up front what else they are dependent on. This honesty is given by having constructors which are open and giving information freely by asking for the dependent objects through constructor parameters.</p>
<p><strong>Otherwise we are adding an extra responsibility.</strong> The Single Responsibility Principle is another commonly held principle that states than any object should have one responsibility. This is powerful because it means that any object should have <em>only one reason to change</em>. When we add code to the constructor we have given the object the responsibility for <em>knowing how to construct the object graph for this type of object.</em> If the object is complicated to construct then there should be something else with that responsibility.</p>
<h3>What to look for</h3>
<p>Keep your eye out for any and all method calls. If any code other than a field or property is being called from within a constructor this is bad.</p>
<p>Instantiation of other objects is a sure sign of a dependency. This goes for anywhere not just in constructors. If you have the “new” keyword it means you’re dependent on the object being created.</p>
<p>Any “logic” in the constructor. If there are conditional statements then you probably have something to fix.</p>
<p>More than a handful of lines is probably too many as well, and is a sign that the constructor is doing more than it should.</p>
<h4>&nbsp;</h4>
<h3>Example bad code</h3>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="border-style: none; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;"><span style="color: #0000ff;">public</span> SomeObject(<span style="color: #0000ff;">int</span> someValue)</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">{</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    _myKindOfTown = <span style="color: #0000ff;">new</span> Chicago();</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">&nbsp;</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    <span style="color: #0000ff;">if</span> (someValue &gt; 5)</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    {</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">        _myKindOfTown.HandleMyKindOfRazzmatazz();</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    }</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">}</pre>
<!--CRLF--></div>
</div>
<h3>How to solve the problem</h3>
<h4>Removing the Object Initialization</h4>
<p>One of the easiest ways to improve things is to get rid of the object initialization from the constructor. Passing the values for these objects as parameters is how we get around the issue of initialization. This makes it so that we do not do the work in the constructor.</p>
<p>In some cases we know we will not use that object, for example in our tests, so we can pass in a <a href="http://en.wikipedia.org/wiki/Null_Object_pattern">NullObject</a>.</p>
<p>This process is called <em>Dependency Injection</em>, and it allows us to “inject” our dependencies into our objects.</p>
<h4>Create a class to handle the construction</h4>
<p>If your object has some complicated requirements involved in the construction that need to happen every time the object is created, you should think about creating an object whose sole responsibility is to create these other objects. As we said earlier a complicated initialization task is another responsibility, so we can have an object who owns that responsibility.</p>
<p>These are often <a href="http://en.wikipedia.org/wiki/Factory_pattern">Factory</a> classes who know how to build other objects.</p>
<h4>Fixed Code</h4>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="border-style: none; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;"><span style="color: #008000;">// Object creation method in another class</span></pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;"><span style="color: #0000ff;">public</span> SomeObject CreateSomeObject(<span style="color: #0000ff;">int</span> someValue)</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">{</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    ITown chicago = <span style="color: #0000ff;">new</span> Chicago();</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    <span style="color: #0000ff;">if</span> (someValue &gt; 5)</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    {</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">        chicago.HandleMyKindOfRazzmatazz();</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    }</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    <span style="color: #0000ff;">return</span> <span style="color: #0000ff;">new</span> SomeObject(chicago);</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">}</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">&nbsp;</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">&nbsp;</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;"><span style="color: #008000;">// ctor for SomeObject</span></pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;"><span style="color: #0000ff;">public</span> SomeObject(ITown myKindOfTown)</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">{</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">    _myKindOfTown = myKindOfTown</pre>
<!--CRLF-->
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; text-align: left; line-height: 12pt; background-color: white; width: 100%; font-family: 'Courier New',courier,monospace; direction: ltr; color: black; font-size: 8pt;">}</pre>
<!--CRLF--></div>
</div>
