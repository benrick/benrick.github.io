---
layout: post
title: "Using CodeRush™ with Refactor!™ Pro After Losing to a Model"
date: 2007-11-29 16:53:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Using-CodeRushe284a2-with-Refactor!e284a2-Pro-After-Losing-to-a-Model/"
---
<!-- more -->

<p>Recently I've started using CodeRush&trade; with Refactor!&trade; Pro after being defeated in a programming competition at DevConnections by Sarah (a hired model) at the <a href="http://www.devexpress.com/" target="_blank">DevExpress</a> booth. There should be two recordings of my painful defeat. <a href="http://aspadvice.com/blogs/ssmith/" target="_blank">Steve Smith</a> made one and <a href="http://www.intellectualhedonism.com/" target="_blank">Carl Franklin</a> made the other recording of my battle. Just for the record Steve faced her days earlier when she was still learning and he also lost.</p>
<p>Overall I've found the tools to be extremely useful. They make a lot of tasks quick and painless. Classes, methods, and properties are extremely quick to write now. Refactoring catches me off guard sometimes, but I am often pleasantly surprised.</p>
<p>For simplicity I was calling a method inside of a foreach loop. I did this because I didn't need the collection except that I was performing an action on each of the returned elements in the collection. When I realized that I needed to perform an extra action with that collection I decided I would move it from the foreach loop.</p>
<p>At first I had a foreach loop similar to this one.</p>
<p><img src="http://static.flickr.com/2232/2073316451_2192c2e7d5.jpg" border="0" alt="RefactorForEach" /></p>
<p>As you can see my foreach loop is using a MembershipUserCollection returned from a function and is going to loop through each MembershipUser. It is at this point I decide to refactor and pull the GetUsers method out of there and I am going to make a variable to store this collection. I highlight then cut the method and paste in in the line above and this is what I get.</p>
<p><img src="http://static.flickr.com/2391/2074108176_d1bd921e78.jpg" border="0" alt="RefactorForEachCollection" /></p>
<p>It knew what I was trying to do! It created the collection and even inserted the variable into the foreach loop for me. When I then rename the variable it also changed it in the foreach loop for me which was quite nice. I didn't even have to check and see what type of collection it was returning before creating the variable. That might have been a generic list, but it didn't matter because the tool figured it out for me and filled in the rest. I was amazed.</p>
<p>There is one annoyance that bugs me though. I have habits I've gotten in to while writing code. I don't like hitting ctrl+space to bring up intellisense. I prefer removing a comma or a parenthesis and typing it again. This works very well without having any extra tools installed. It also works well most of the time. I've only run into a problem a few times.</p>
<p>I start out with code that looks like this. There is a long function call so I keep the parameters below the function.</p>
<p><img src="http://static.flickr.com/2011/2073367585_bd55944b1d.jpg" border="0" alt="DXLongFunctionName" /></p>
<p>Now I want to get intellisense back just to confirm the first parameter or maybe to see the overloads for this function so I delete the "(" and put it back in place and I get the following.</p>
<p><a title="DXLongFunctionNameExtraParen" href="http://www.flickr.com/photos/67369333@N00/2073367633/"><img src="http://static.flickr.com/2336/2073367633_3db96280ff.jpg" border="0" alt="DXLongFunctionNameExtraParen" /></a></p>
<p>Now it has added in an extra ")" that I did not want. I wish it could have seen that my function was complete and I was at the start. Sure that might have been convenient if my code wasn't already written, but in this instance it got annoying. Visual Studio got confused and gave me nice red squiggly lines. DOH! Not too terrible. Most of the time the tools work well there are just a few quirks like this that get me sometimes. Perhaps this blog post will help get the ball rolling to make this product smarter and better able to see what I'm doing. Overall I think the tool is excellent.</p>
<p>If you're interested in buying any cool software from Dev Express I recommend you check out <a href="http://aspadvice.com/blogs/ssmith/archive/2007/11/04/DevExpress-TechSummit.aspx" target="_blank">Steve Smith's Dev Express Tech Summit blog post</a>. He mentions a good discount code there that will get you 10%. His coupon code is <strong>SMITH07</strong> you can use it to save 10% when you <a href="https://www.devexpress.com/ClientCenter/Order/Default.aspx?group=.NET" target="_blank">buy great programming tools from DevExpress</a>.</p>
<p>Happy coding!</p>
