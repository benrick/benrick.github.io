---
layout: post
title: "Static Overload - Code Audits #6"
date: 2012-07-09 10:00:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Code Audits", "DaysOfCodeAudits"]
permalink: "/post/Static-Overload-Code-Audits-6/"
---
<!-- more -->



<p>Static methods are very useful and powerful tools when writing code. As I am sure many people have pointed out, these tools should be used sparingly and cautiously.</p>
<p>Statics are dangerous if they have dependencies. This is because they&rsquo;re hard to test. <a href="/post/Static-Mocking-with-JustMock" target="_blank">Or so I thought</a>. Keep in mind, that just because you <em>can</em> mock statics does not mean that you <em>should</em> be using a lot of statics.</p>
<h3>The Bad</h3>
<p>I saw a great case of this misuse of statics in some cross-cutting code. It would be a great place to use Aspect Oriented Programming, but was instead a mess of statics and dependencies.</p>
<p>This cross-cutting code was being used throughout the application. There was barely a section of the site that did not use this code. Not once in the code had anyone unit tested <em>any</em> of the code that used these methods. It wasn&rsquo;t being mocked, so there wasn&rsquo;t really a way to unit test anything using that code.</p>
<p>Starting things off is a class. As you can probably have guessed from this post&rsquo;s title, it has a static constructor. In the constructor, it accesses a database and creates an instance of the class. Each of the methods in this static class take in parameters and then write to the file system.</p>
<p>I was trying to write code in this code base, but I could not make any changes yet. I needed to get that monster abstracted so that I could work around it.</p>
<h3>The Better</h3>
<p>For cross-cutting concerns like this, it&rsquo;s common to use statics. That&rsquo;s OK. Not ideal, but OK. You just need to be careful. Try to limit the damage.</p>
<p>If done nicely, the Singleton isn&rsquo;t horrible. Just keep in mind that tests will need to mock out that singleton when you&rsquo;re using it.</p>
<p>For this class, I wrote a wrapper around it that implemented an interface. My code depended solely on that interface, and I mocked the interface in my tests. This let me minimize the impact of the change. In the long run, It will be important to make sure that the wrapper gets used throughout the codebase. Anywhere the static was used, it should not depend on the wrapper. This is a quick, easy solution that <a href="http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule" target="_blank">slowly improves the code</a>.</p>
<p>In my opinion, that&rsquo;s the best way to clean up any code base. Just fix a piece at a time. Make sure that when you touch any other part of the code that you use that same wrapper and eventually things will start looking a lot better.</p>
<h3>More Code Audit Nuggets</h3>
<p>Keep watching for more interesting nuggets of stuff that I&rsquo;ve seen in codebases.</p>
