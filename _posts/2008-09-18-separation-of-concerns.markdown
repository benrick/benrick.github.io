---
layout: post
title: "Separation of Concerns"
date: 2008-09-18 14:24:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Separation-of-Concerns/"
---
<!-- more -->



<p>Continuing on my previous post about <a href="/post/Separation-of-Code-Responsibilities.aspx" target="_blank">separation of code responsibilities</a> where I was mostly just discussing one aspect of <a href="http://www.amazon.com/Working-Effectively-Legacy-Robert-Martin/dp/0131177052" target="_blank">a book</a> I appreciate, I now want to comment on the concept of separation of concerns. While thinking about this idea I realized that I've been a follower of this idea longer than I previously thought. I admit it, I don't separate my code as well as I often could.&nbsp; I am sure that everyone reading this has heard that we should try to make things modular and that we should encapsulate pieces of our code. It is all part of what I consider to be classical education taught to programmers everywhere.</p>
<p>Separation helps for many reasons. It allows us to think about only the currently important section of code. We need not always be concerned with how everything else works. It is much easier to solve problems by implementing a solution that doesn't require at every step being concerned with the details. If I want to tell someone how to load boxes into a truck. I want to say something like this.</p>
<ol>
<li>Pick up a box</li>
<li>Place the box in the bed of the truck</li>
<li>Repeat previous steps until no boxes remain outside the truck</li>
</ol>
<p>I don't want to have to do something like this.</p>
<ol>
<li>Pick up a box<ol>
<li>Move next to a box</li>
<li>Bend knees so you're at about the same level as the box</li>
<li>Put hands on the box</li>
<li>Grip the box tightly</li>
<li>Lift up using your knees</li>
</ol></li>
<li>Place the box in the bed of the truck<ol>
<li>Move while still gripping the box</li>
<li>Walk over to the back of the truck</li>
<li>Move box away from body and toward the truck</li>
<li>Let bottom of box touch the truck bed</li>
<li>Release grip on the box</li>
<li>Move hands away from the box</li>
</ol></li>
<li>Repeat previous steps until no boxes remain outside the truck</li>
</ol>
<p>I prefer to be able to assume that the person I am talking to knows the simple things. If I have to get into this kind of detail anytime I tell someone how to do something I am going to forget details along the way. I'm going to say something incorrectly. I also may mess up the overall algorithm because I am too concerned with the details of the steps. With different pieces being separated it makes it much easier to solve problems. There are plenty of other reasons to separate what we create.</p>
<p><img src="http://static.flickr.com/3061/2866282774_306cbe9ecc.jpg" border="0" alt="SeparationOfConcerns" align="right" />Another reason that it is nice to have our work separate out nicely is that we are able to replace and adjust sections of our work without having to rip it all apart. If I have been having sections of code performing plenty of different tasks then I make it a lot harder to change it. When I go to make a change I am dealing with a lot more than I need to be, because a lot more stuff is there. The benefits of this are plenty and I am sure people can suggest plenty more. (I am also sure there are plenty of reasons to not have modular code.)</p>
<p>As I am sure is the case for many developers reading this, I spent a lot of time working with Linux machines. One thing I of course noticed with the classic applications found in the open source world is the tendency to have individual programs perform one task. The output of one program is often passed as input into the next program.</p>
<p>One line I heard often is, "Why does program <strong>xyz</strong> need to sort its output? Just send it through program <strong>abc</strong>, because it sorts already." At first I think the idea of having a program for sorting is kind of silly. Isn't it easy to sort? Couldn't all of these programs just sort? Well even sorting text can be fairly complicated. Which algorithm should you use? Should sorting be on the first character or the second? Maybe we want to sort based on the second column of data. I don't want to go into the code for a large number of programs just to update how it sorts.</p>
<p>Along with separation of concerns comes the also very important need to break dependencies. When we perform this separation we are breaking things into separate objects, libraries, and who knows what else. Some dependencies aren't a big deal. Most of my applications are fairly dependent on the .NET Framework, but I am not concerned with this. If I am stopping using the .NET Framework, I am probably switching languages or something and rewriting anyway.</p>
<p>While thinking about how to break up responsibilities among sections of code I've really been noticing how great an idea those separate programs have always been in the Linux world. I've noticed a trend away from it, but the core applications still tend to follow that old principle. Keep things small and performing only one task. Need something else? Let another program handle that task. As any code attempts to do more, it just becomes more difficult to work with.</p>
<p>The idealistic purpose of computers is to make our lives easier. Try not to let them do the opposite.</p>
