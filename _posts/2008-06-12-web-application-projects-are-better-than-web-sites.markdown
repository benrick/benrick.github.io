---
layout: post
title: "Web Application Projects are better than Web Sites"
date: 2008-06-12 22:56:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Web-Application-Projects-are-better-than-Web-Sites/"
---
<!-- more -->



<p>Recently I was explaining the difference between the web application project and the web site to the budding developers I've been working with. I suffered greatly while using web sites instead of web application projects. I remember having a great deal of pain while my <a href="http://weblogs.asp.net/scottgu/archive/2006/07/30/Common-Gotcha_3A00_-Slow-VS-2005-Web-Site-Build-Performance-Because-of-_1C20_Dueling-Assembly-References_1D20_.aspx" target="_blank">assemblies dueled</a> each other. Scott Guthrie posted about the dueling assembly problem.</p>
<blockquote>
<p><strong>Dueling Assembly Reference Problem</strong></p>
<p>The problem I refer to as a &ldquo;dueling reference&rdquo; occurs when you setup multiple file-based references to assemblies from a VS 2005 Web Site Project that are each updated dynamically (using .refresh files), and which in turn have dependencies on <span style="text-decoration: underline;">different versions</span> of a common shared assembly library.</p>
</blockquote>
<p>This one reason was more than enough in my opinion to switch to web application. It took some sites which could take upwards of five to ten minutes to compile and made them take ten seconds. I can't ask for much better improvement there.</p>
<p>Another great benefit of using Web Application Projects instead of using the Web Site is that there is a project file managing what is and is not included. On a few of the projects I've worked on in the past we have had some trouble with source control and web sites. It is much easier if you can just define what is and is not included in the web site. With the classic web sites, it was a loose system. The site was defined as a folder in the file system. With the web application project your site is defined using a project file which dictates which files will and will not be included.</p>
<p>On really annoying part of web sites are the refresh files used for adding assemblies into the bin folder. There are files which say where the assembly can be obtained. If you're working with source control you need to have these files in source control. The problem is that you need to not have the actual binaries in that location in source control or the refresh files will not work correctly. This creates some huge headaches because Visual Studio wants to check in these files (assemblies) being included by the refresh files. Ouch.</p>
<p>The feel of web applications is more consistent with everything else in Visual Studio. This consistency is nice, since there now is "Open Web Site" and "Open Project". It is quite annoying to have two different things to work with. If they were both just project that would make it so much simpler.</p>
<p>Far too many people are still using the sites, so I doubt that Microsoft will remove them from future versions of Visual Studio anytime soon. It doesn't really hurt me to have them, but I pretty much exclusively use Web Application Projects over Web Sites. I even do this for small little one shot sites. I've just grown to like them so much that I cannot turn back.</p>
<p>If I have to deal with refresh files again, I'll just go crazy.</p>
