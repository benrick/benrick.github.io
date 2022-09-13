---
layout: post
title: "Great Conditional Logic"
date: 2007-12-12 21:21:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Great-Conditional-Logic"
---
<!-- more -->

<p>It is amazing some of the relics that can be found while code reviewing old code. Sometimes developers do things without thinking and make some <em>great</em> code. I am of course referring to some really funny code such as what I found a few minutes ago. I am always annoyed when boolean values are checked explicitly in conditional statements like the following code.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">if</span> (IsValid == <span style="color:#0000ff;">true</span>)</pre>
</div>
<p>This bothers me because the true is completely useless. I would read this code as "If is valid is true", and that is kind of silly when I could say "If is valid".</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">if</span> (IsValid)</pre>
</div>
<p>This is just part of the annoyance in the code. Now I've cleaned it up a bit here, because it didn't really have a variable named <em>IsValid</em>. It was actually a variable named <em>edit</em>. We were not sure if <em>edit</em> meant that someone was allowed to edit or if it was in edit mode or what.</p>
<p>This was just slightly annoying. The really amazing part was in the <em>else</em> of this <em>if</em> statement. It had a great bit of <em>else if</em> logic. The code looked overall like this.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">if</span> (edit == <span style="color:#0000ff;">true</span>)
    <span style="color:#008000;">// Lines of code here</span>
<span style="color:#0000ff;">else</span> <span style="color:#0000ff;">if</span> (edit == <span style="color:#0000ff;">false</span>)
    <span style="color:#008000;">// Lines of code here</span>
</pre>
</div>
<p>I now wonder what possible other condition is there? In the else is there another state for <em>edit</em>? It is not a reference type, it is a value type so it can never be null. Just got to be careful of boolean operators there are so many other values for them other than <em>true</em> and <em>false</em>.</p>
<p>I hope everyone enjoyed this fun little code snippet.</p>
