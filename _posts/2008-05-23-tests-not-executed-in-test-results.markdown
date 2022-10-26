---
layout: post
title: "Tests Not Executed In Test Results"
date: 2008-05-23 21:42:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Tests-Not-Executed-In-Test-Results/"
---
<!-- more -->



<p>Earlier today, as I was working with the <a href="http://en.wikipedia.org/wiki/Mentorship#New-hire_mentorship" target="_blank">Prot&eacute;g&eacute;</a> I've been <a href="/post/Differences-Between-Structures-and-Classes-in-C/" target="_blank">referring</a> to <a href="/post/Visual-C-2008-Keyboard-Shortcut-Reference" target="_blank">previously</a>, we were debugging some code, and we ran into a little bug. Our tests results would not execute. We tried restarting Visual Studio and a lot of other stuff and it didn't fix it. We eventually just restarted the machine, and that fixed the problem. We figured that even though it wasn't the most graceful solution, it is one we knew would work.</p>
<p>This is the error message we were receiving. None of our tests were executing and it wasn't very clear about why. We did figure out that it had to do with the code coverage we had previously been running.</p>
<p><img src="http://static.flickr.com/3222/2516284177_4eedca3a71.jpg" border="0" alt="TestResultsNotExecuted" /></p>
<p>These guys managed to recreate the same error a little later, and they found a solution. Here is the solution to this problem.</p>
<p>What is going on is that we enabled code coverage and then we decided to start debugging.</p>
<p>So we started debugging and clicked "OK" through the message about how it was going to disable code coverage because you can't have it enabled while debugging.</p>
<p>Then we hit a break point and decided to stop debugging. All is seemingly still working correctly.</p>
<p>We attempt to run the tests again. This is where the %#$^ hits the fan. Suddenly we get that error message listed above and we have no idea why. It just doesn't want to let us execute the tests no matter what we tried.</p>
<p>Those budding <a href="http://en.wikipedia.org/wiki/Old_age" target="_blank">young</a> developers, as I said, found the error again and that time decided to pursue it further and discovered the root of the problem as well as how to fix it.</p>
<p>There is a process called <a href="http://msdn.microsoft.com/en-us/library/ms182404(VS.80).aspx" target="_blank">VSPerfMon</a> which is running in the background and is preventing the tests from being executed. It is the program which is running in the background to keep track of code coverage, and if you stopped the execution in the middle of a test it doesn't close correctly. If you kill that process you will once again be able to run your tests. To kill it you can get into the task manager select it from the processes list and end the process.</p>
<p>Have fun testing your code with tests that actually run.</p>
