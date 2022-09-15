---
layout: post
title: "Testing Private Methods"
date: 2008-12-02 18:07:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Testing-Private-Methods/"
---
<!-- more -->

<p>In a previous post about <a href="/post/2008/11/25/Keeping-Large-Classes-in-Line.aspx" target="_blank">cutting large classes down in size</a> I mentioned that</p>
<blockquote>
<p>Sometimes there are methods kept private in a class. Some calculations are kept private because nothing should be calling those methods on this class. This is a good hint that the method belongs somewhere else. If the method is kept private because it doesn't make sense for a user of this class to use it, it belongs somewhere else.</p>
</blockquote>
<p>Private methods are a common occurrence in classes. Sometimes they should be moved into another class, because they were only private because they didn't make sense in that class. Other times they are part of the internal workings of the class. At the end of the day it is always up to the developer how he is going to structure his code.</p>
<p>If you don't want to move the method and don't want to make it public you still have a couple of options to test it.</p>
<ul>
<li>You can sometimes test a method through the public methods that call it. (Can be difficult sometimes because it is harder to control what is being passed to the method.)</li>
<li>You can write a public method which passes through to it, and prefix the name with "Test". (This is a bit hacky and should only ever be done with internal code that will not ever be in an API.)</li>
<li>You can change the method to protected and write a Test version of the class that inherits, and then exposes the method publicly on the test class. (This option works well because the test class can be kept with the tests so it doesn't dirty the production code. Only do this if you will not be subclassing this class already.)</li>
</ul>
<p>Some people discourage testing private methods, because there really shouldn't be much logic in private methods that really needs to be tested. If it really needs tests it probably belongs in another class. My opinion is that if people are going to keep the code in the private method anyway, they might as well at least be testing it.</p>
<p>Structure your code how you like. Just don't let your classes get out of hand. If it becomes an issue then refactor it.</p>
<p>Friends don't let friends perform premature optimization.</p>
<p><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/TestingPrivateMethods_FA89/PrematureOptimization_3.jpg" border="0" alt="PrematureOptimization" width="291" height="258" /></p>
<p>As Donald Knuth said, "We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%."</p>
<p>I think it is safe to say this should apply to refactoring as well. Don't go on refactoring binges. Only refactor code you're currently working with.</p>
