---
layout: post
title: "Overusing Interfaces and Injection"
date: 2011-11-29 10:00:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Overusing-Interfaces-and-Injection", "/post/overusing-interfaces-and-injection"]
---
<!-- more -->

<p>In software development, it is very important to continually learn and experiment with new techniques for building great software. Our job is to learn and improve the quality of code that we build over time. It is through this progression of experimentation, failing, succeeding, observing, reading, listening, and teaching that we as developers improve. In this post, I am going to discuss one way in which we as developers have learned something great and have taken it to the point of failure. This will allow us to learn, resolve, create new techniques, and succeed in the future.</p>
<h3>What is Dependency Inversion?</h3>
<p>One of the most important SOLID principles for testing our applications is the Dependency Inversion principle. I am very glad to see many more codebases using this technique as time goes on, however, I am seeing nearly as many others getting caught up in an easy mistake of using too much injection and putting interfaces on <em>everything</em> regardless of necessity. Lets start by defining dependency inversion so we&rsquo;re all on the same page.</p>
<p>From Wikipedia:</p>
<blockquote>
<p>In object-oriented programming, the <a href="http://en.wikipedia.org/wiki/Dependency_inversion_principle" target="_blank">dependency inversion principle</a> refers to a specific form of decoupling where conventional dependency relationships established from high-level, policy-setting modules to low-level, dependency modules are inverted (i.e. reversed) for the purpose of rendering high-level modules independent of the low-level module implementation details. The principle states:</p>
<dl><dd><dl><dd><em>A. High-level modules should not depend on low-level modules. Both should depend on abstractions.</em></dd><dd><em>B. Abstractions should not depend upon details. Details should depend upon abstractions.</em></dd></dl></dd></dl></blockquote>
<p>Reading directly from this, we can see that it says we should be depending on abstractions and in doing so we take a much lighter dependency. A dependency on an abstraction is not a big deal. A dependency on a concrete class is a big deal.</p>
<p>Is what I just said always true? No, it depends on the abstraction and the concrete class. For example, I make an exception for simple classes provided through the framework or language my code is primarily based on. For instance, I have no problem saying that my method depends on being given a DateTime object since there is no real gain by abstracting that object since that is a part of the framework and I will always be injecting in an object of that type.</p>
<h3>When are interfaces and injection being overused?</h3>
<p>One example of over-architected injection that I see a lot comes from something that I&rsquo;ve taught many times when explaining SOLID. It&rsquo;s the classic example of a dependency that people don&rsquo;t realize they have.</p>
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">DateTime.Today</pre>
<br /></div>
<p>I assume most of my readers know that this is a dependency taken directly on the system clock. It&rsquo;s important to inject this dependency when your code behaves differently based on the value returned from that static method. When we extract that dependency, people have been taught (by many people including me) that a good way of testing this is to have some kind of IClock interface with an implementation of SystemClock accessing the computers clock by calling that static method we were just discussing.</p>
<p>Now when we write our method, we just give it a parameter of IClock. When we run our code in production, it&rsquo;s taking in the SystemClock object, and in our tests we&rsquo;re using a mock object. Great! We&rsquo;ve reversed the dependency! Is that really what we wanted though? It might have been, but in some cases we could have just passed in the DateTime instance object returned from that method. This would have reduced complexity in our code.</p>
<p>Because we used this interface instead of just depending on simple concrete classes, we&rsquo;ve actually made our code more difficult to use and maintain. Isn&rsquo;t that the whole reason we were following SOLID in the first place? Yes, yes it is. This is of course a simple example, but you can find larger examples of where you could test your code and build in a nice structure without having to create pointless interfaces. Heck even in this example, you might have a good reason to need that Interface, but I am sure that you could get away with using it less. Every time you add that layer, you add complexity. Sometimes adding it is OK, because it gives you a much needed seam, but I doubt you need it as often as you think.</p>
<p>Please make sure that you need the interfaces and layers of abstraction before creating them. I&rsquo;ve come across many codebases that become as complex or more simply by trying to do things &ldquo;the right way&rdquo;.</p>
<p><strong>The road to software development hell is paved with good intentions.</strong></p>
<p>&nbsp;</p>
<p>Don&rsquo;t like the way I phrased something? Think I overgeneralized? Did I make a mistake?</p>
<p>Call me out on it!</p>
<p>I appreciate the feedback.</p>
