---
layout: post
title: "Why I Prefer Web Application Projects"
date: 2009-10-13 10:20:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Why-I-Prefer-Web-Application-Projects", "/post/why-i-prefer-web-application-projects"]
---
<!-- more -->

<p>Over the summer, Nimble Pros brought on some new interns. We of course brought them up to speed on how we do things here. We like the integration process of bringing new employees into the mix immediately involving them in the process the entire team is involved with. To help get them up to speed we use a combination of pair-programming, book and article reading, and formal instruction.</p>
<p>As I am sure anyone who uses Visual Studio for web development knows, there are two main ways to go about creating the site that you&rsquo;re going to develop. There is the web application project (WAP) and the web site (ignoring MVC of course).</p>
<p>Back in the days of ASP.NET 1 there was only one way of doing things, web application projects. ASP.NET 2 got rid of WAPs and replaced them with web sites. Not entirely sure why, but it did not take long before Microsoft added Web Application Projects back into the mix. These were able to be installed and added into Visual Studio so they could be used again.</p>
<p>I of course switched to these as soon as they were readily available. The title of this post kind of gives that away. I switched for a few reasons including the dueling assemblies issue which can occur with web sites. I have written about <a href="http://brendan.enrick.com/post/2009/05/06/Web-Application-Projects-are-better-than-Web-Sites.aspx" target="_blank">dueling assemblies and some of the differences between these methods of developing sites</a> before.</p>
<p>The main reason why I prefer having a project is that I like being in control. Now you might wonder how I can have more control with a project file. It might seem that the less controlling approach would give me more control, but it is not the case. The loose collection of files, lovingly referred to as a web site is hard to control. I can&rsquo;t say what is included I can&rsquo;t say what is excluded. My only control is the relative locations of files. Inclusion of a library? Oh that is a refresh file in the bin folder.</p>
<p>Sure I can get some control in a web site&rsquo;s loose structure, but I feel that I get so much more control from the project file. I have something obvious to point MSBuild to. I have settings and targets I can manipulate in the file. I have direct control of which files are in the project. Heck I can control which version of a dll I am using which means no more dueling assemblies. Hooray!</p>
<p>Perhaps you disagree. I prefer the WAP to the web site. Do you have any good reason to think otherwise?</p>
