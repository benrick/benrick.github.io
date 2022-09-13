---
layout: post
title: "A Quick Answer About Reference Types"
date: 2009-11-23 09:14:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/A-Quick-Answer-About-Reference-Types", "/post/a-quick-answer-about-reference-types"]
---
<!-- more -->

<p>Reference types were created to make dealing with pointers a little bit easier. They hide away the details of the pointers, so that the programmer need not think about them. In many ways I think they&rsquo;re awesome, because they really achieve that goal. The problem is that by abstracting away the details of the pointers they&rsquo;re sometimes <em>difficult</em> to work with, because they can be a little bit confusing.</p>
<p>I received a comment about this topic on one of my <a href="http://aspalliance.com/" target="_blank">ASP Alliance</a> articles explaining <a href="http://aspalliance.com/1682_What_to_Know_About_Value_Types_and_Reference_Types_in_C" target="_blank">value types and reference types in C#</a>.</p>
<blockquote>
<p>First of all the article is excellent.     <br />But why the following program produces output as:: abc:xyz      <br />it should produce xyz:xyz.      <br />I am confused...Plz help      <br />The Code:      <br />string myName = "abc";      <br />string authorName = null;      <br />authorName = myName;      <br />authorName = "xyz";      <br />Console.WriteLine("{0}:{1}",myName,authorName);      <br />Console.ReadLine();      <br />The Actual Output:      <br />abc:xyz      <br />The Expected Output:      <br />xyz:xyz      <br />as it's areference type only one copy is shared between references.</p>
</blockquote>
<p>How about if we take this step by step looking at the variables and their values, and I&rsquo;ll be able to explain why the behavior is as you&rsquo;ve found. First here is the code we&rsquo;ll be looking at.</p>
<div>
<pre style="line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: consolas, 'Courier New', courier, monospace; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">string</span> myName = <span style="color: #006080">"Brendan"</span>;
<span style="color: #0000ff">string</span> authorName = <span style="color: #0000ff">null</span>;
authorName = myName;
authorName = <span style="color: #006080">"Enrick"</span>;
Console.WriteLine(<span style="color: #006080">"{0}:{1}"</span>,myName,authorName);
Console.ReadLine();</pre>
</div>
<p>We are expecting it to print out &ldquo;Brendan:Enrick&rdquo;.</p>
<p><em>Red is for the variables and orange is for referenced values for those variables.</em></p>
<p><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="ReferenceTypes1" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/AQuickAnswerAboutReferenceTypes_77F5/ReferenceTypes1_3.png" border="0" alt="ReferenceTypes1" width="440" height="1131" /></p>
<p>Notice that when we set a variable equal to a literal string value we get a new location in memory, but when we set it equal to another variable all we are doing is copying the pointer to that memory location. However, when we then set that variable equal to a new literal value it doesn&rsquo;t replace the old one for both since they each had a pointer. It just creates a new location in memory with that value and assigns a pointer to that variable.</p>
<p>The type of behavior that the writer of this code was trying to achieve could be handled by pointers very easily, but reference types take away control of pointers. Loss of freedom for the sake of safety one might say. Now that I&rsquo;ve said that everyone will switch back to using c++ to get their pointers back.</p>
<p>Thank you for asking the questions <strong></strong>saurabh. I hope this thoroughly answers your question. If you have any more, please feel free to ask them as well.</p>
