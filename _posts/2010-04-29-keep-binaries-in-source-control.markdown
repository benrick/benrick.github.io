---
layout: post
title: "Keep Binaries in Source Control"
date: 2010-04-29 17:14:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Keep-Binaries-in-Source-Control", "/post/keep-binaries-in-source-control"]
---
<!-- more -->

<p>No, not all of them. Just the ones required for your build process. Doing this will make your life a lot easier. You want to reference all of your assemblies locally and keep them in source control. You also want all of your testing executables kept there. If you have anything extra your build process depends on make sure you include that as well. A great example is a post I did about <a href="http://brendan.enrick.com/post/2009/09/15/Build-OpenAccess-Project-Using-MSBuild-on-a-Machine-Without-OpenAccess-Installed.aspx" target="_blank">building a library which uses OpenAccess on a build server</a>. The build server of course doesn&rsquo;t have OpenAccess installed. That would be crazy.</p>
<p>You get a lot of great benefits out of keeping these files local and in source control. Since libraries change infrequently, they will not require much source control storage space. This also means that when updating from source control you will rarely have to wait for an update. If you do have to wait you probably needed it anyway, and would have just been waiting on an Internet download instead.</p>
<h3>Build Server Benefits</h3>
<p>If you have a build server this will allow you to build your application without having to install your tools and libraries on the server. When the server gets the latest version of your project from your source control server, it will already have the current versions of all of your tools and libraries. This keeps things simple and easy to work with.</p>
<p>If you don&rsquo;t go this route you will have to install everything on the build server and make sure that all of the paths still match. Ever dealt with the Program Files (x86) folder?</p>
<h3>New Computer Benefits</h3>
<p>Have a new developer joining the project or just a fresh install of Windows on your computer? Great! Now just go and find the 10 different libraries and tools that are required to build this project. Once you have those make sure that they&rsquo;re in the correct folders&hellip; Wouldn&rsquo;t that be annoying?</p>
<p>If you keep those tools in source control and always reference with relative paths, no one will have to hunt for all of the tools required for the build. If you were referencing libraries in their install locations you would have all kinds of problems if something installed in a bad place. For example I&rsquo;ve seen libraries try to install in a user-specific directory. Yes, that is a worst case example, but it can happen.</p>
<p>Keep everything relative and you can move your code anywhere. I want to be able to copy everything in source control onto a freshly installed copy of Windows and have it build. If I can do that, I know the project has a good structure.</p>
<h3>Old Versions of the Project</h3>
<p>Ever want to go back to an old version of your project and look at something? I bet you had some trouble building if you&rsquo;ve changed the versions of any libraries you&rsquo;re using. If the specific version you need is with that code you never have to worry. At any snapshot in time the repository has the correct build scripts, libraries, tools, utilities, and source code. You&rsquo;re all set to go back to any point in the history of the application and take a look.</p>
<p>You might be saying, &ldquo;what if I have changed versions of my IDE?&rdquo; It shouldn&rsquo;t matter. If you&rsquo;ve got build scripts in place you can use those to get that app running.</p>
<p>Some people try to keep track of which versions of which tools are used for which release of an application, but if you&rsquo;ve got them in source control you don&rsquo;t have to worry about it. Just get the version you want, and the required files come with it.</p>
<p>Now that&rsquo;s what I call a clean, self-contained build.</p>
