---
layout: post
title: "Write a Test Before Fixing a Bug"
date: 2009-01-14 09:43:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Write-a-Test-Before-Fixing-a-Bug/"
---
<!-- more -->



<p>As I've said in previous posts, it is important to write tests for your code. A lot of the time I am talking about when refactoring code or when writing new code. Now I agree that bug fixing could be considered refactoring, but people seem to treat it differently. When fixing bugs they want to go in and quickly make the bug go away. That is a dangerous way to solve things, because it doesn't prevent the bug from returning.</p>
<p>If a bug exists in your system then there are test cases missing from the system. When you fix a bug, even if you do write a test case to handle the bug how do you know you've tested the right thing? If your test is not right it will not prevent the bug from <a href="http://en.wikipedia.org/wiki/Software_regression" target="_blank">returning</a>. I know of only one way to be fairly confident that a bug is tested well. <strong>The test <em>needs</em> to be written before the fix.</strong> If it isn't written first you will not know. If you follow the TDD practice of Red, Green, Refactor, the Red lets you know that you've found the bug. Then when you make it green you can have confidence that you've fixed the bug.</p>
<p><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/WriteaTestBeforeFixingaBug_7E71/RedGreenRefactor_3.png" border="0" alt="RedGreenRefactor" width="344" height="51" /></p>
<p>If you had not tested first you don't even know that your test is accurate. How do you know you actually found what is causing the bug? You can't really be sure with any confidence, because all you saw were green tests. Your test couldn't fail. Either the test didn't actually test the bug or because you fixed it. You hope the latter, but it could be the former.</p>
<p><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/WriteaTestBeforeFixingaBug_7E71/GreenGreenRefactor_3.png" border="0" alt="GreenGreenRefactor" width="357" height="51" /></p>
<p>This will not work. For other things I can agree with you that you can write code and then test it, but not for bugs. With bugs the test needs to be written first, so there is some confidence that the bug is being tested. Since code already exists the test needs to be in place first. This same practice should be adhered to when doing refactorings of working code as well. The point in that case is also to prevent software regressions caused by the refactoring. Tests help you hold existing functionality, and in the case of bug fixing they help to ensure that the bug has truly been fixed and tested to prevent a return.</p>
<p><strong>Software bugs are like bad musicians. If you don't actively prevent them, they will make a comeback.</strong></p>
<h3>Example</h3>
<p>As an example of this. We can assume that we have two classes. One of them is called <em>Student</em> and the other is called <em>Course</em>. To represent this example we are going to have some badly written code which is going to cause us to have a few nasty bugs (Badly written code makes for easier examples). From our knowledge&nbsp; of the domain, we know that students take a few courses at a time, so there is a collection of courses associated with a student.</p>
<p>Say our student has a property called <em>Courses</em> and that property holds the collection.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> Student
{
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">int</span> ID { get; set; }
    <span style="color: #0000ff">public</span> List&lt;Course&gt; Courses { get; set; }
}</pre>
</div>
<p>Now we say that somewhere we are caching the <em>Student</em> objects based on their IDs. We want to make sure that if the student object is changed that we expire the cache, so we will cache it with a SqlCacheDependency on the database table for the Student object.</p>
<p>Assume we have a "View my courses" page for the student to get information about the courses. For ease, it will obviously grab the student object out of cache and use its collection of courses to display the information if the information is already there.</p>
<p>What bug have we created here?</p>
<p>Well we've now made it so that if any of the courses change this change will not be reflected on the courses page of any student currently in the cache. There are literally probably a dozen ways of fixing this bug. Plenty of ways we could have prevented it, but then we wouldn't have this nice example now would we?</p>
<p>All I am saying is that some <a href="http://en.wikipedia.org/wiki/Unit_testing" target="_blank">unit tests</a> and <a href="http://en.wikipedia.org/wiki/Integration_testing" target="_blank">integration tests</a> be written for these before we fix the problem. This lets us be sure that we've fixed the problem correctly.</p>
<p>The first test I would write is one that loads a student object (making sure that is gets cached) and then separately loads one of the courses the student is in and alters that course. I would then make sure that the change to the course succeeded and then I would get the student again, (it would come out of cache this time) and I would verify that it had the change I made to the course. I would expect that the first time I run it that the test will fail. If it doesn't fail, or fails for a reason other than what I expected, I need to fix it so it fails the way I expect.</p>
<p>Once it is failing correctly I can adjust the code to make it work correctly. I would call this an issue violating the <a href="http://en.wikipedia.org/wiki/Single_responsibility_principle" target="_blank">single responsibility principle</a>, because the Student object in my opinion shouldn't be holding a local copy of the Courses. If it doesn't have that then it will not be able to cache it. I think that property should just be a getter calling through to some <em>Course-related</em> class which can cache it if it wants to. Even though these are obviously domain objects, we should try to keep them separated a little bit better, because keeping them too close can cause some annoying bugs.</p>
<p>As always, have a great day, and keep testing your code.</p>
