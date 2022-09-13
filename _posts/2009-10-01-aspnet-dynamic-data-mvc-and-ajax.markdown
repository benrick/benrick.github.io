---
layout: post
title: "ASP.NET Dynamic Data, MVC, and AJAX"
date: 2009-10-01 14:15:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/ASPNET-Dynamic-Data-MVC-and-AJAX", "/post/aspnet-dynamic-data-mvc-and-ajax"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>I&rsquo;ve been having an interesting conversation with Peter Blum about the different directions in which ASP.NET is currently developing. He has some very interesting points that he is making about this topic. So he asked me if I use dynamic data, which is of course how all of this conversation started. I informed him that most of my exposure to ASP.NET Dynamic Data has just been playing around with it. I really haven&rsquo;t done any applications using it. (I of course don&rsquo;t consider little test applications and demos to be real applications.)</p>
<p>I also admitted that I&rsquo;ve been heavily involved with MVC since the early beta versions of it. I didn&rsquo;t mention at the time that I also started using AJAX very early on as well. I did a lot with &ldquo;Atlas&rdquo; as it was called at the time. His responding comment was quite interesting.</p>
<blockquote>
<p>the Insiders are so heavily into MVC that we don&rsquo;t have enough people who push Microsoft to improve the webforms technology</p>
</blockquote>
<p>I really think that he makes a great point here since MVC got here we really don&rsquo;t hear too many of the prominent voices talking about improvements that can be made to ASP.NET Web Forms. Yes, I know there are those who do not like MVC. I read some of their blogs. Some of their reasons are well thought out and very relevant. What I am seeing less often is people commenting on the things that can <em>make web forms better</em>.</p>
<p>Something I&rsquo;ve said many times since MVC came around is that it is great <em>for certain circumstances</em>. If you&rsquo;re in one of them, use MVC. If your task requires Web Forms, then use them. Heck, if you need classic ASP, go for it. Using the right tool for the job is extremely important. Just because you&rsquo;ve mastered the hammer and the screwdriver doesn&rsquo;t mean you should use them to dig a hole.</p>
<p>A trend that Peter also noted in our conversation is that Dynamic Data came around and there was a little bit of hype for it, but the hype largely died out. MVC, however, has had continual hype, growth, and attention since its mention. AJAX also had a large amount of support and a great following from MVPs, insiders, and influential people.</p>
<p>The thing with Dynamic Data though is that in concept it is a very cool idea and has the potential to be great. It, like all technology, needs to have feedback from the community. It is up to the developers to push Microsoft into developing the technology in the correct direction. I think this is one of the reasons that Peter has been working so hard on Dynamic Data.</p>
<p>With the early beta versions of ASP.NET MVC some of the &ldquo;testability&rdquo; was really not there. People trying to use it had to use workarounds to get things to work. For example controllers used to call a method to show the view. They didn&rsquo;t return ActionResults as they do now. The problem is that it was hard to see what was called so you couldn&rsquo;t really test it. So I created &ldquo;fake&rdquo; controllers to do my testing since the controllers were inadequate at the time. Developers using and giving feedback about what needed to change is what made that project a success.</p>
<p>Not sure if we can revitalize the interest in Dynamic Data and get the ball rolling in the right direction for it, but I can say that I&rsquo;ve heard very little about it lately. So how about it? Willing to try out Dynamic Data and see how it can be made better?</p>
<p>Peter made <a href="http://www.peterblum.com/DES/DynamicData.aspx" target="_blank">DES Dynamic Data</a>, which is supposed to enhance a lot of the aspects of ASP.NET Dynamic Data perhaps I&rsquo;ll try it out and see if it makes Dynamic Data spectacular.</p>
