---
layout: post
title: "Long Code Lines in Articles and Tutorials"
date: 2008-07-28 15:30:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Long-Code-Lines-in-Articles-and-Tutorials/"
---
<!-- more -->

<p>While publishing articles for ASP Alliance I often take the time to fix long code lines I find in the articles. These bother me greatly, because they make web pages and thus the article ugly and difficult to read. I hate having to scroll horizontally to read a long line of code. It is annoying and takes more time. I don't get why people don't trim their code. I keep my code neatly trimmed when I'm writing articles, and also whenever it is code I am writing in general. I never want code lines to be too long. I have no problem scrolling vertically, but there should be some set limits on how long lines should ever be especially when the lines will be posted on the Internet.</p>
<p>Some of the ugliest sites I've ever seen are the ones where text has gotten too wide and has taken over the layout of a page. Widths have been stretched and the page extends beyond its intended positioning. I admit this has happened plenty of times on sites with which I am associated and I am ashamed. It would be nice if I could convince the rest of the development community of the importance of having code be easy to read. How can I possibly intend to help other people understand something through an article or tutorial when my code is difficult to read. I'm not helping their understanding at all by having them struggle to read the code let alone understand it.</p>
<p>I think overall the software development community could use a facelift. My site included. Sadly my skills in the area of design are quite lacking. Formatting text in a readable manner is about the extent of my skills, but I believe that is likely the most important task to complete.</p>
<p>Get rid of lines like this one.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">MyCompany.Controls.DropDownList commentselectionddl = SomeTemplatedControlOnThePage.FindControl(<span style="color:#006080;">"commentselectionddl"</span>) <span style="color:#0000ff;">as</span> MyCompany.Controls.DropDownList;</pre>
</div>
<p>Replace them with lines like this one.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">MyCompany.Controls.DropDownList commentselectionddl = 
    SomeTemplatedControlOnThePage.FindControl(<span style="color:#006080;">"commentselectionddl"</span>) <span style="color:#0000ff;">as</span> MyCompany.Controls.DropDownList;</pre>
</div>
<p>For the benefit of everyone involved in this wonderful community of developers, format your code. Make it more readable. Don't let lines trail off into the distance. Keep them short and concise. Use simple examples, and never make code more complicated just to show how smart you are. I've seen plenty of code where authors attempt to complicate their own code seemingly to make themselves appear smarter. Remember, when you write code you should not be writing for yourself. Write the code for someone else to learn. Write to help other people and make the community as a whole a better place. Sure it benefits you when you teach others, but remember that at the end of the day other people will be reading what you write.</p>
