---
layout: post
title: "Throwing Away Return Values"
date: 2008-10-21 18:08:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Throwing-Away-Return-Values", "/post/throwing-away-return-values"]
---
<!-- more -->

<p>So it probably took me 15 seconds to track down this error in my code, and those wasted seconds, while very minor, are exactly why I wish Visual Studio or ReSharper or some program would alert me to what I've mistakenly done. It is easy with some methods to throw away a return value without noticing.</p>
<p>If I am calling a method which has a return value I am ignoring, it might be nice if it made it a little more obvious I am doing so. Perhaps an underline with a note explaining that I am not processing a return value. Sure lots of people ignore return values all the time, but they really shouldn't be. The return value probably exists for a reason.</p>
<p>As an example assume you want to get a substring.</p>
<div>
<div style="border-style: none; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;"><span style="color: #0000ff;">string</span> myString = <span style="color: #006080;">"LongStringWithTooMuchStuffSoItProbablyNeedsToBeCutDownToSize"</span>;</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">myString.Substring(5,10);</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">Console.WriteLine(myString);</pre>
</div>
</div>
<p>Looking at that code it is pretty easy to miss the fact that I am not doing anything with the return value. Right now the value written to the console is "LongStringWithTooMuchStuffSoItProbablyNeedsToBeCutDownToSize". I am just ignoring the value that substring is returning. This means I am not actually doing anything. I am just printing out the original string. What I really should have written is this.</p>
<div>
<div style="border-style: none; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;"><span style="color: #0000ff;">string</span> myString = <span style="color: #006080;">"LongStringWithTooMuchStuffSoItProbablyNeedsToBeCutDownToSize"</span>;</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">myString = myString.Substring(5,10);</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">Console.WriteLine(myString);</pre>
</div>
</div>
<p>It wouldn't be that difficult for a program to detect unused return values. I am already informed when I don't use variables. Since plenty of plug-ins for visual studio already read method signatures, one of them could easily detect that I am ignoring the return value of that method. Ah the little things. Not too big a deal, but kind of annoying since I executed my program once and had to look to see why my code didn't work as expected.</p>
<p>Maybe some program does mention this already, or maybe there is some setting I need to enable to do this. Please let me know if you know of one.</p>
