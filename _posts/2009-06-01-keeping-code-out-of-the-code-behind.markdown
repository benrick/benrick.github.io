---
layout: post
title: "Keeping Code Out of the Code Behind"
date: 2009-06-01 13:52:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Keeping-Code-Out-of-the-Code-Behind", "/post/keeping-code-out-of-the-code-behind"]
---
<!-- more -->

<p>In ASP.NET development (and yes even in MVC) each page is able to have associated code. This is traditionally (before MVC) how someone would add code to a page. This was much nicer than what was seen a lot on the classic ASP days when a lot of code would be littered between HTML controls.</p>
<p>However, when one is introducing code into the code behind great care must be taken. This is because the code behind is really not the location where most logic goes. If we take a moment to think about what the ".aspx" file is, we will probably come up with something along the lines of, "the file where we decide how we're going to display things to the user." So this is about display issues.</p>
<p>Should it know anything about a database?</p>
<p><em>NO!</em></p>
<p>Should it know that there is any form of persistent storage?</p>
<p><em>Probably not.</em></p>
<p>So what should it know about?</p>
<p><em>It needs to know how to display things to a user and that is it.</em></p>
<p>So what do I do once I've got code in the code behind that is business logic?</p>
<p><em>Step 1 is to try to get it refactored into the correct class. Create new classes to handle the business logic. Your pages will call these classes to do the required work.</em></p>
<p><em>If you don't know where to put something yet there is an intermediate step better than having it in the code behind. You can make pseudo-MVC by creating another class. So create a class with the same name as the page but add "Controller" onto the it as a suffix. Then put the logic in there. This will give you a bit of seam which should allow you to test the code.</em></p>
<p>Keep in mind that the MVC pattern is very cool. ASP.NET is very cool, but it is a fairly old pattern. The idea of it is just separating things. We can do the same thing with ASP.NET if we are careful not to clutter things. We can achieve similar results. Sure it isn't as nice and pretty as MVC, but it gives us seams while separating the concerns of our code so that it is maintainable.</p>
