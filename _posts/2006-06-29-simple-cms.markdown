---
layout: post
title: "Simple CMS"
date: 2006-06-29 20:29:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Simple-CMS/"
---
<!-- more -->



<p>&nbsp;&nbsp;&nbsp; Lately I have been working on a simple content management system. This CMS will not be like a lot of what is currently available. The software applications that currently exist tend to be applications which <em>are</em> the site. Simple CMS will plug into an existing web page. This is beneficial because it will allow people who have one or more web sites to quickly and easily add content to that site.</p>
<p>&nbsp;&nbsp;&nbsp; So far I have been able to keep the install down to one executed SQL script, a dll file, and some copying and pasting into a web.config. This may be changing a bit as I add more to the functionality of the system.</p>
<p>&nbsp;&nbsp;&nbsp; I have been working with the httphandlerfactory class. I have my SimpleCms handler factory inherit from that class, and I use to handle the content which the system creates. Creating these pages often gets complicated, because I have to find ways to get the controls to render correctly. Sometimes I cannot use the controls I want to use because I cannot get them to render. I am working still to get them working, but for the time being I want to have a working CMS.</p>
<p>&nbsp;&nbsp;&nbsp; Inheriting from System.Web.UI.Page, I create my base pages for the system, and from there I have a couple of custom administrative pages built into the system. This is the interface which users connect to to manage the content. Since these pages are classes the user is able to change the location with which to connect to them.</p>
<p>&nbsp;&nbsp;&nbsp; Soon I will be passing this assembly to Zach Bussinger, who is going to try to implement and use this. I like to think that he is a test subject or guinea pig. If he can't get it working I think I need to go back to the drawing board, but if he can then it should be usable. He will also probably let me know what kinds of problems he finds in the application that I did not notice.</p>
<p>&nbsp;&nbsp;&nbsp; Once I have a version of the application to release I will make sure to blog more about it. I will probably talk more about how to use it and its features when I am farther along with the project.</p>
