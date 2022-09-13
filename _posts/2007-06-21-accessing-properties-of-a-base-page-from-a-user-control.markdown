---
layout: post
title: "Accessing Properties of a Base Page from a User Control"
date: 2007-06-21 17:42:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Accessing-Properties-of-a-Base-Page-from-a-User-Control", "/post/accessing-properties-of-a-base-page-from-a-user-control"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>Earlier today I was helping someone who was working with a user control. That control was on an ASP.NET page which was inheriting from a base page. From the user control he could not access the properties of the base page. He mentioned that he was getting an error message which said that the property did not exist in the current context.</p>
<p>I showed him that the reason he was having the problem is because the code in the user control came from the page before, and thus he would need to get the properties from there, but he was also going to need to cast the Page as the base Page in order to get to the property.</p>
<blockquote style="margin-right:0px;" dir="ltr">
<p>int myImportantValue = ((MyBasePage)Page).ImportantProperty;</p>
</blockquote>
<p dir="ltr">This will retrieve the value from the property of the base page. It is a fairly simple task. Perhaps next I will show how to do a similar task with a masterpage.</p>
<p dir="ltr">I've now added that blog post about <a href="http://brendan.enrick.com/post/Accessing-Master-Page-Properties-from-a-content-page.aspx" target="_blank">Accessing a Property of a MasterPage from a Content Page</a>.&nbsp;</p>
