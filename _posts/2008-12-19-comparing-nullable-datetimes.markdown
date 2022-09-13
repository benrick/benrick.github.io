---
layout: post
title: "Comparing Nullable DateTimes"
date: 2008-12-19 09:52:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Comparing-Nullable-DateTimes"
---
<!-- more -->

<p>A couple of days ago I was working on some code when I noticed a comparisons of two DateTime? variables. So I wondered what would happen if either or both of those variables had gotten null values. Since I had never tried it before I figured I would just take a couple of minutes and test some things. Since I already had visual studio open I just created a unit test and wrote some code in there to test the behavior. I've not done it in a console application since it is easier for most people to use the console app version of the code.</p>
<p>So the first thing to do is to create a few Nullable DateTime variables. I then wrote a small amount of completely unnecessary code. I did this to assure the readers of this post that the assumption that the Nullable variables' HasValue properties is correct. I then proceed with a bunch of test cases some of which are unnecessary, but I believe they help demonstrate the point.</p>
<p>My task for readers of this post is to try to figure out the results of this code before reading the answer below.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">int</span>? lesserDateTime = 1;
<span style="color: #0000ff;">int</span>? greaterDateTime = 2;
<span style="color: #0000ff;">int</span>? nullDateTime1 = <span style="color: #0000ff;">null</span>;
<span style="color: #0000ff;">int</span>? nullDateTime2 = <span style="color: #0000ff;">null</span>;

<span style="color: #0000ff;">if</span> (!lesserDateTime.HasValue || !greaterDateTime.HasValue 
    || nullDateTime1.HasValue || nullDateTime2.HasValue)
{
    <span style="color: #0000ff;">throw</span> <span style="color: #0000ff;">new</span> Exception(<span style="color: #006080;">"Something is very wrong here!"</span>);
}

Console.WriteLine(<span style="color: #006080;">"\n lesserDateTime &gt; greaterDateTime = "</span> 
    + (lesserDateTime &gt; greaterDateTime));
Console.WriteLine(<span style="color: #006080;">"\n greaterDateTime &gt; lesserDateTime = "</span> 
    + (greaterDateTime &gt; lesserDateTime));
Console.WriteLine(<span style="color: #006080;">"\n lesserDateTime == lesserDateTime = "</span> 
    + (lesserDateTime == lesserDateTime));
Console.WriteLine(<span style="color: #006080;">"\n lesserDateTime &gt; nullDateTime1 = "</span> 
    + (lesserDateTime &gt; nullDateTime1));
Console.WriteLine(<span style="color: #006080;">"\n greaterDateTime &gt; nullDateTime1 = "</span> 
    + (greaterDateTime &gt; nullDateTime1));
Console.WriteLine(<span style="color: #006080;">"\n lesserDateTime == nullDateTime1 = "</span> 
    + (lesserDateTime == nullDateTime1));
Console.WriteLine(<span style="color: #006080;">"\n greaterDateTime == nullDateTime1 = "</span> 
    + (greaterDateTime == nullDateTime1));
Console.WriteLine(<span style="color: #006080;">"\n nullDateTime1 &gt; greaterDateTime = "</span> 
    + (nullDateTime1 &gt; greaterDateTime));
Console.WriteLine(<span style="color: #006080;">"\n nullDateTime1 &gt; lesserDateTime = "</span> 
    + (nullDateTime1 &gt; lesserDateTime));
Console.WriteLine(<span style="color: #006080;">"\n nullDateTime1 == greaterDateTime = "</span> 
    + (nullDateTime1 == greaterDateTime));
Console.WriteLine(<span style="color: #006080;">"\n nullDateTime1 == lesserDateTime = "</span> 
    + (nullDateTime1 == lesserDateTime));
Console.WriteLine(<span style="color: #006080;">"\n nullDateTime1 &gt; nullDateTime2 = "</span> 
    + (nullDateTime1 &gt; nullDateTime2));
Console.WriteLine(<span style="color: #006080;">"\n nullDateTime2 &gt; nullDateTime1 = "</span> 
    + (nullDateTime2 &gt; nullDateTime1));
Console.WriteLine(<span style="color: #006080;">"\n nullDateTime1 == nullDateTime2 = "</span> 
    + (nullDateTime1 == nullDateTime2));
Console.WriteLine(<span style="color: #006080;">"\n nullDateTime2 == nullDateTime1 = "</span> 
    + (nullDateTime2 == nullDateTime1));

Console.WriteLine(<span style="color: #006080;">"\n"</span>);</pre>
</div>
<p>Answer below.</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p>|</p>
<p><img style="border-width: 0px;" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ComparingNullableDateTimes_7EE9/NullableCompareConsoleResults_3.png" border="0" alt="NullableCompareConsoleResults" width="453" height="477" /></p>
<p>And just to show that this has to do with Nullable really and not the DateTime part, I did the test with int? also.</p>
<p><img style="border-width: 0px;" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ComparingNullableDateTimes_7EE9/NullableCompareIntResults_3.png" border="0" alt="NullableCompareIntResults" width="445" height="465" /></p>
<p>This is why you need to be a little bit careful with Nullable types. Make sure that you are always checking the HasValue property when working with Nullable types so you can handle the situation in the desired fashion. If you didn't know or check the type of that variable the results could be disastrous.</p>
<p>Don't make too many assumptions about behavior. I asked a few people what they might expect to get when comparing with the null value, and they guessed that the null would be treated as the default value for the data type. That guess makes a lot of sense, but it is not the case. Notice that every time a null was involved the result was false. The only time this is not the case is when comparing the equality of two null values.</p>
<p>As a final note I will say that if you want to do comparisons of Nullable values I recommend doing the following. Since Nullable's are a little bit special, we need to compare them this way.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">Console.WriteLine(<span style="color: #006080;">"\n Nullable.Compare(lesserDateTime, nullDateTime1) = "</span>
    + Nullable.Compare(lesserDateTime, nullDateTime1));
Console.WriteLine(<span style="color: #006080;">"\n Nullable.Compare(nullDateTime1, lesserDateTime) = "</span>
    + Nullable.Compare(nullDateTime1, lesserDateTime));</pre>
</div>
<p>If we don't do the comparison in this manner we are likely to get the above unexpected results. If you want to see the specifics of the Nullable.Compare method, read the <a href="http://msdn.microsoft.com/en-us/library/dxxt7t2a.aspx" target="_blank">MSDN Nullable.Compare documentation</a>.</p>
