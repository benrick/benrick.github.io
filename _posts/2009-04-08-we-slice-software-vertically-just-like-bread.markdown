---
layout: post
title: "We Slice Software Vertically Just Like Bread"
date: 2009-04-08 10:42:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/We-Slice-Software-Vertically-Just-Like-Bread/"
---
<!-- more -->



<p><img style="border-bottom: 0px; border-left: 0px; border-top: 0px; border-right: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/WeSliceSoftwareVerticallyJustLikeBread_8737/Bread_3.jpg" border="0" alt="Bread" width="240" height="179" align="right" /> When working on a feature or some other aspect of a software project, it is important to figure out what piece you want to do at any given time. There are two primary routes you could take. Perhaps you want to go and create the whole UI, but have nothing wired up. Maybe you want to go and write all the business logic first, and you might want to go create the data layer and underlying infrastructure. If you do one of those then I will call you crazy.</p>
<p>I believe in vertically slicing an application. You never know at the beginning of a project what scope creep is going to occur, and you also don't know which aspects of your initial design will be completely unnecessary. One of the main reasons why so many people are against "big design up front" is because we don't know what we're going to need in the end.</p>
<p>If we're working in vertical slices, we can complete an entire piece of functionality that we know we need. This is why we work with vertical slices. We can stop at any time, and there are no unused pieces. Everything we've completed is there and working.</p>
<p>If we ignore how references in our application might be set up and just look at the structure of an application with a very simplistic view, we might say that there is a UI that calls some form of business logic which in some way talks to some kind of data.</p>
<p><strong><span style="text-decoration: underline;">Basic Structure of a Project</span></strong></p>
<p><a href="/files/media/image/WindowsLiveWriter/WeSliceSoftwareVerticallyJustLikeBread_8737/ThreeLayers_4.jpg"><img style="border-bottom: 0px; border-left: 0px; border-top: 0px; border-right: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/WeSliceSoftwareVerticallyJustLikeBread_8737/ThreeLayers_thumb_1.jpg" border="0" alt="ThreeLayers" width="240" height="225" /></a></p>
<p>Say for example that we are going to work with a horizontal slice. Yes, plenty of people do this. I tried working on an application this way many years ago. So perhaps we are thinking, "hey, why don't we get the database and the data layer hashed out at the beginning then we can just write all the code on top of it later." After working on this for a while we might end up with something like this. The blue is the completed work.</p>
<p><strong><span style="text-decoration: underline;">Work Done Horizontally</span></strong></p>
<p><a href="/files/media/image/WindowsLiveWriter/WeSliceSoftwareVerticallyJustLikeBread_8737/HorizontalWork_4.jpg"><img style="border-bottom: 0px; border-left: 0px; border-top: 0px; border-right: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/WeSliceSoftwareVerticallyJustLikeBread_8737/HorizontalWork_thumb_1.jpg" border="0" alt="HorizontalWork" width="240" height="225" /></a></p>
<p>Now for some questions.</p>
<ul>
<li>How much can we show the customer? Nothing.</li>
<li>Are we sure we structured everything the way the customer wanted? No.</li>
<li>What if this is an open source project, maybe we want to encourage other developers to join the project. Are these developers able to see the structure of our application and how we want things to work? Well it looks like.... no.</li>
</ul>
<p>Now what if we had done the same amount of work vertically? We might end up with something like this.</p>
<p><strong><span style="text-decoration: underline;">Work Done Vertically</span></strong></p>
<p><a href="/files/media/image/WindowsLiveWriter/WeSliceSoftwareVerticallyJustLikeBread_8737/VerticalWork_2.jpg"><img style="border-bottom: 0px; border-left: 0px; border-top: 0px; border-right: 0px" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/WeSliceSoftwareVerticallyJustLikeBread_8737/VerticalWork_thumb.jpg" border="0" alt="VerticalWork" width="240" height="225" /></a></p>
<p>Now assume that this is the same amount of work as if we had worked horizontally. Sure we have a lot less breadth, but the depth of our work is far greater. Now if we ask those same questions.</p>
<ul>
<li>How much can we show the customer? Everything we've worked on.</li>
<li>Are we sure we structured everything the way the customer wanted? Yes, because the customer can see it and can tell us right now if we did something wrong. We are able to quickly respond to and fix the problem.</li>
<li>What if this is an open source project, maybe we want to encourage other developers to join the project. Are these developers able to see the structure of our application and how we want things to work? They can see everything we've done. Anyone hopping on this project would see the full structure and know how the layers are interrelated and would likely be able to add meaningful work to the project.</li>
</ul>
<h3>My Past Horizontal Mistake</h3>
<p>So I mentioned early in this article that I tried horizontally working on a project once.&nbsp; Yeah, that was a mistake. As you get to new aspects of a project a little thing called scope creep occurs. As you get to and think about new pieces of an application you realize new ways you can improve them, right? Well, this is another major problem with working horizontally. As I added new pieces, I came up with new stuff I wanted to do. New ways of doing things came to mind. Eventually I had scope creeped the data enough that I ended up giving up on the project.</p>
<p>I've recently started working on the project again, but this time I am of course working with vertical slices. I am going to make pieces just large enough to give me some value. That way at any point I could stop development and have a working tool. One which does something. Maybe not everything I want, but enough.</p>
<h3>A Skill to Learn</h3>
<p>Breaking tasks into thin vertical slices is difficult. Without advances in bread slicing technology, the processed, sliced bread from stores could never be so thin. It isn't easy to make thin slices, but the thinner the slice the better we are able to get the amount of bread we want. Perhaps we want 3 slices. Before we had these thin slices it might have been one and a half, but the thin slices make everything easier.</p>
<p>Some tasks look like they'll take weeks to complete. That my friend is not a task. We need to split that. There is probably some aspect of that which could be completed in a day. Maybe it wouldn't be in a shippable state, but there would be something that the customer could see. An initial bit working that is not the whole thing. This gives us two things. It shows the customer what we're working on, and it also gives them the chance to give us feedback. We can more easy adjust that small slice than if we had delivered the whole feature at once.</p>
<h4>A Slicing Example</h4>
<p>Assume we have a web site. We want to add user profiles to the site. Our customer comes along and says he wants the profile to have this information.</p>
<ul>
<li>Full Name</li>
<li>Nickname</li>
<li>Location</li>
<li>Age</li>
<li>Gender</li>
<li>List of current and previous occupations</li>
<li>List of educational institutions</li>
<li>List of favorite games</li>
<li>List of favorite movies</li>
<li>List of favorite books</li>
<li>List of favorite songs</li>
<li>List of favorite musicians</li>
<li>List of favorite places</li>
<li>List of friends</li>
</ul>
<p>If you went to do all of this at once it could take you a while. This is a good time to figure out some nice places to split things. An obvious split here is to do everything that is not complicated. For this we could say the top 5 ones we'll do. These don't have lists.</p>
<p><strong>Slice 1:</strong> Create Full Name, Nickname, Location, Age, and Gender as a profile and create a view and edit page for them.</p>
<p>That slice is very manageable, and when you're done you can show the customer and make sure that is what they were expecting. Perhaps they wanted Full Name to be 3 separate pieces: First, Middle, and Last. Since we haven't done much, this is easy to change right now.</p>
<p>Now we might say that the next slice is the next item on the list. Why? Because we want to get one of the lists in place and the functionality set up and to the customer for feedback.</p>
<p><strong>Slice 2:</strong> Add a list of current and previous occupations to the user profile.</p>
<p>Ok so we implement this basically as a list of strings. The user puts in the name of the occupation and adds more in the same way. We display this list of occupations on the profile page. Now when we show the customer this he says that he wants the list to intelligently suggest occupation names as the user types with previously used occupations. So now it is a bit more complicated, but we make the change. We then ask if the same will be done with the other lists, and the customer says "yes". Now we know how to do these next ones.</p>
<p>As we work through the next few slices, maybe the customer decides that we don't need both musicians and songs. The customer gets rid of musicians. Well we benefit here, because we hadn't put any work into that yet.</p>
<p>I really want to emphasize here that a slice should be small. Vertical slices are there so you always have a working product. At any moment you could stop. Maybe we stopped before doing the lists of things. <em>We had a working solution at that moment</em>. The other big reason we do vertical slices is so people can se what we've done and give us feedback. Customers might give you feedback on the UI, but until it is wired up and working the feedback isn't as useful.</p>
