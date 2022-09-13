---
layout: post
title: "String Formatting BoundFields in Silverlight"
date: 2009-09-29 12:19:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/String-Formatting-BoundFields-in-Silverlight", "/post/string-formatting-boundfields-in-silverlight"]
---
<!-- more -->

<p>Hi my name is Brendan E. While working with a Bindable Silverlight control I ran into a little bit of trouble because I have a dependence commonly found among Visual Studio developers. I am addicted to intellisense. When a property isn&rsquo;t in intellisense I make the failing assumption that it does not exist.</p>
<p>So even though I have posted specifically about how we <a href="http://brendan.enrick.com/post/2009/01/26/ASPNET-Supports-Valid-HTML-Attributes-in-its-Tags.aspx" target="_blank">developers should be smart enough to know that we can&rsquo;t always trust intellisense</a>, I still make the mistake of trusting it.</p>
<p>I am binding to a control and it slipped my mind to use the <em>DataFormatString</em> property, because it didn&rsquo;t show up in intellisense for me. So of course I look around for what else I might use. I bing a few times about what I am trying to do. When I find the answer I feel like an idiot once again. This must be how all addicts feel. I just need my intellisense.</p>
<p>So I was trying to format my bound field as a percentage. To do that I just needed to add the following code.</p>
<div>
<pre style="line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: consolas, 'Courier New', courier, monospace; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">DataFormatString="{}{0:P}" </pre>
</div>
<p>&nbsp;</p>
<p>Hooray! I&rsquo;ve got working code now. So I repeat again. Don&rsquo;t trust intellisense. Just because it says it isn&rsquo;t there doesn't mean it isn&rsquo;t there.</p>
