---
layout: post
title: "Everyone Should Have a Continuous Integration Server"
date: 2009-06-11 17:44:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Everyone-Should-Have-a-Continuous-Integration-Server/"
---
<!-- more -->

<p><strong>Have you ever heard another developer say, "it works on <em>my</em> machine"?</strong> Well I am sure a lot of people have heard that common phrase. Heck I've used it, but a lot of the time I will point out that it also works on the <em>build server</em>. That last part is what really counts in my opinion.</p>
<p>Any and all code you write should be checked into a source control repository. I think most people agree with that statement. Another very important thing is that your code actually <em>work</em> after being checked out from the repository. I wrote a blog post a while back about <a href="http://brendan.enrick.com/post/2009/02/12/Organizing-Software-Projects.aspx" target="_blank">how to structure software projects</a>.</p>
<blockquote>
<p>One of the most important aspects of a well-organized project in my opinion, is the ability for a new developer on a project to be able to sit down and have a working solution as soon as they get the latest version of the application from the source control repository. Not only should that person be able to have a working solution, but that working copy should assist the developer in setting up the local environment. The solution should also be in a state which allows all of the project's tests to run without the user having to jump through a bunch of hoops.</p>
</blockquote>
<p>I feel strongly that working on a project should be as simple as a checkout and a few more clicks to see the app running. Having a build server is a great way to maintain this on a project. Everything you need to be able to run your app needs to be in source control. This will be how the build server will get the application, so if it isn't in there, the server will not build it.</p>
<p>The build server is the ultimate answer to the question of, "does this code work on another machine?" You'll keep your code working everywhere, and you make sure that all of the pieces are integrated and working together effectively.</p>
<p><strong>Have you ever had a developer commit their changes at the end of the day and commit code that breaks the build for everyone else?</strong> It is a lot harder to check in broken code without realizing it if the build server informs you right after checking in. Sometimes it is the compilation which fails and other times there are tests failing. It doesn't matter how it was broken, but it is broken now. Luckily you've got a build server to save you.</p>
<p>With a build server in place, everyone will know when the build breaks. If the offending developer is not around to fix it, you can always revert the changes until such time that the offender is available to fix the issue. Everyone continues on, because they knew of the issue and corrected it by reverting immediately. No one continued on thinking that broken code was really working code.</p>
