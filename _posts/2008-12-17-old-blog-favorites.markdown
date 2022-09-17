---
layout: post
title: "Old Blog Favorites"
date: 2008-12-17 10:56:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Old-Blog-Favorites/"
---
<!-- more -->



<p>I am somewhat partial to a few of the posts from my previous blog. For some of these posts, I just like the post, some the content about which the post was written, and some were just popular posts.</p>
<p><strong>Installing SQL Server Management Studio with SQL Server: </strong>My most popular post is one written about a painful experience installing SQL Server's client tools. Sadly the popular post is out of date. My first post about the topic I found a solution that worked and managed to install the software. I late found out that there was a better way and I updated the post. The problem is that Google continued to send traffic to the old one. For my blog it was a pretty popular post. it has had over 25,000 views.</p>
<p>The original version - <a href="/post/2009/05/06/Installing-SQL-Server-Management-Studio-with-SQL-Server.aspx" target="_blank">Installing SQL Server Management Studio with SQL Server</a></p>
<p>The current version - <a href="/post/2009/05/06/SQL-Server-Client-Tools-Installation.aspx" target="_blank">SQL Server Client Tools Installation</a></p>
<p><strong>Visible Whitespace in Visual Studio:</strong> Another post written about a traumatic experience was when I accidentally used a keyboard shortcut and enabled visible white space. It caused a blue dot to show for every space character in visual studio. Wow was it hard to read my code with that on. Well I Googled for it, and at the time I didn't receive any results. There are some now my post is one of them. I also didn't notice the option to turn it off. I used an algorithm I like to call brute force to figure out the keyboard shortcut I typed. It was <strong>Ctrl + E + S</strong>. Comments let me know of a bunch of other ways to solve the problem for different configurations and versions of Visual Studio.</p>
<p><a href="/post/2009/05/06/Visible-Whitespace-in-Visual-Studio.aspx" target="_blank">Visible Whitespace in Visual Studio</a></p>
<p><strong>Return Within a C# Using Statement:</strong> IDisposable objects are nice to work with. I prefer not dealing with external resources, which is generally what you're doing with disposable objects, but having this interface makes it a little bit nicer. I wrote a post telling people it was safe to return from within the using statement, because the using statement will make sure that the object is disposed. In the lifetime of the post only one person actually challenged me on it and asked me to provide code showing that what I said is true. I of course responded to that comment and then posted a response on this blog. My response includes sample code showing that using statements make sure that the object is disposed.</p>
<p>If you like the second post make sure you thank Lambros Kaliakatsos for commenting on the first one.</p>
<p>The original post - <a href="/post/2009/05/06/Return-Within-a-C-Using-Statement.aspx" target="_blank">Return Within a C# using Statement</a></p>
<p>The follow up including sample code - <a href="/post/2008/11/21/Returning-From-Inside-a-Using-Statement.aspx" target="_blank">Returning From Inside a Using Statement</a></p>
<p><strong>Performance with DropDownLists and ViewState: </strong>One thing that it seems a lot of ASP.NET developers still don't understand very well is ViewState. Page lifecycle stuff seems to really be fueling the MVC craze these days. I wrote a post talking about how ViewState can hurt the performance of your applications if you let it get out of hand. The example I used is the drop down list, but it can certainly get a bit crazy from grids, repeaters, etc. I wrote an article basically saying that you should try to avoid ViewState if you're going to have too much of it. I later followed up with a post about how to use a DropDownList without ViewState. Some people are concerned that you will not be able to use the SelectedValue property, but you can if you wire it up correctly. It is all about understanding that painful Page Lifecycle.</p>
<p><a href="/post/2009/05/06/Performance-with-DropDownLists-and-ViewState.aspx" target="_blank">Performance with DropDownLists and ViewState</a></p>
<p><a href="/post/2009/05/06/Using-a-DropDownList-without-ViewState.aspx" target="_blank">Using a DropDownList without ViewState</a></p>
<p>There are plenty of other posts I like in there, but I think I've bored my readers enough for one day. I've got a couple of posts lined up which should be a little bit more interesting than this one, so keep reading. As always, have a great day.</p>
