---
layout: post
title: "Visual Studio Keyboard Shortcuts Disabled in Code Snippets"
date: 2008-05-22 21:10:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Visual-Studio-Keyboard-Shortcuts-Disabled-in-Code-Snippets"
---
<!-- more -->

<p>Since Visual Studio 2008 came out I've been extremely impressed with the software. One shortcut which I believe probably exists in CodeRush and Resharper is the ability to find the using directive needed at any given time. in VS2008 you can press <em>ctrl</em> +<em> .</em> and a little menu will appear which will add using directives for you. This makes writing code so much easier, because I don't have to go to the top of my file to add using statements. I type the name of what I need, press <em>ctrl</em> + <em>.</em> and keep going. I also love using the <a href="http://msdn.microsoft.com/en-us/library/z4c5cc9b(VS.80).aspx" target="_blank">shortcut snippets in Visual Studio</a>.</p>
<p>These snippets allow me to quickly and easily write properties, for loops, etc. I pretty much use these snippets whenever I have one for the task. They only require you fill in the necessary fields. The problem is that when you are filling in the information for one of these snippets it disables keyboard shortcuts. I can no longer have it automatically add my using directive to the top of the file. It will not bring up the menu.</p>
<p>In order to get this functionality to work again I have to complete the code snippet I am working on and go back to what needed the namespace added to it. I am then able to use the shortcut to add in my using directive.</p>
<p>These are a few examples of snippets I use in Visual Studio. I've been using var a lot lately for my foreach loops since I don't have to worry about this issue with it, but I prefer to avoid var.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">foreach</span> (var item <span style="color: #0000ff;">in</span> collection)
{

}

<span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> i = 0; i &lt; length; i++)
{

}

<span style="color: #0000ff;">using</span> (resource)
{

}</pre>
</div>
<p>Yes, I used a using statement in this example so I could write about using a using shortcut to generate a using statement which needs a using directive.</p>
<p>Perhaps Microsoft will fix this and allow the keyboard shortcuts to still work while using these snippets. Maybe some of the third party tools already get around this. Resharper? CodeRush? Anyone else?</p>
