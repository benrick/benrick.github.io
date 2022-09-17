---
layout: post
title: "Where Should Test Classes Go?"
date: 2008-11-25 22:35:00 -0500
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Where-Should-Test-Classes-Go/"
---
<!-- more -->



<p><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/WhereShouldTestClassesGo_13DBE/LegacyCodeBook_3.jpg" border="0" alt="LegacyCodeBook" width="240" height="240" align="right" /> In <a href="http://www.amazon.com/Working-Effectively-Legacy-Robert-Martin/dp/0131177052" target="_blank">Working Effectively With Legacy Code</a>, the author talks about where to place test classes in your applications structure. He mentions that you should place test classes along side production code in the structure of your application. Why? Well he says that it is good because it helps you navigate between the test classes and the production code easily.</p>
<p>I somewhat agree with him when he says this, because a lot of time is wasted moving between classes. I admit I am one of the people who tries not to mix too much test and production code. I like to keep anything test related at arms length. Why do I do this? Because I believe that everything becomes cleaner and easier to observe when it is separated. I believe there is some reason to keep things aesthetically pleasing, and I certainly believe that keeping them separate will make the system appear a lot less daunting.</p>
<h3>Navigating Between Test and Production Code</h3>
<p>So I've explained what I like about keeping the two together, but I still haven't made an argument for why I don't need the "navigation" benefits of keeping the two together. The way I handle this is through superior add-ins to my IDE. I use Resharper to give me better navigation. Lately I've become quite fond of this application. If nothing else just for the ability to navigate to classes and files in the solution based on the name alone.</p>
<p><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/WhereShouldTestClassesGo_13DBE/GoToType1_3.png" border="0" alt="GoToType1" width="482" height="274" /></p>
<p>This is incredibly powerful, and it is a quick keyboard shortcut away. It lets you navigate quickly and easily. I like it because it lets me organize how I want to, and I don't need to worry about moving from one assembly to another even. I keep my unit tests in a separate project from any production code. Since I can still navigate quickly, I get all the benefits of both methods.</p>
<p>I think there are a lot of great suggestions people can make for how to code, but at the end of the day you need to make your own choice. Consider people's suggestions, understand why they make them, and certainly adjust them to your own uses.</p>
<p>My opinion is that test classes should go in a separate location. It keeps the production app less cluttered. The application will not deploy test code. If they're separated there will never be any confusion. It would just be terrible if you had a class that actually needed to have the word "test" in the name.</p>
