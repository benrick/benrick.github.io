---
layout: post
title: "Nested Using Statements"
date: 2008-08-28 19:50:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Nested-Using-Statements/"
---
<!-- more -->

<p><img src="http://upload.wikimedia.org/wikipedia/commons/e/e1/Basket_style_nest.jpg" alt="" width="96" height="72" align="right" /> I think it is a great idea to always be reading code. You may learn more than you intend to sometimes. Read an article to learn one trick and you may learn a completely different one. Earlier today I was reading some code written by <a href="http://stevesmithblog.com/" target="_blank">Steve Smith</a>. He wrote an extension method for the System.Web.UI.Control class called RenderControl. I was just looking to see what he had written, and from this little snippet of code I learned a cool trick.</p>
<p>&nbsp;</p>
<div>
<div style="border-style: none; padding: 0px; overflow: visible; font-size: 8pt; width: 99.05%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; height: 173px; background-color: #f4f4f4;">
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">string</span> RenderControl(<span style="color: #0000ff;">this</span> System.Web.UI.Control control)</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">{</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">    StringBuilder sb = <span style="color: #0000ff;">new</span> StringBuilder();</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">    <span style="color: #0000ff;">using</span> (StringWriter sw = <span style="color: #0000ff;">new</span> StringWriter(sb))</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">    <span style="color: #0000ff;">using</span> (HtmlTextWriter textWriter = <span style="color: #0000ff;">new</span> HtmlTextWriter(sw))</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">    {</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">        control.RenderControl(textWriter);</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">    }</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">    <span style="color: #0000ff;">return</span> sb.ToString();</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">}</pre>
</div>
</div>
<p>In the past I would have nested my using statements like this.</p>
<div>
<div style="border-style: none; padding: 0px; overflow: visible; font-size: 8pt; width: 99.11%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; height: 205px; background-color: #f4f4f4;">
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">string</span> RenderControl(<span style="color: #0000ff;">this</span> System.Web.UI.Control control)</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">{</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">    StringBuilder sb = <span style="color: #0000ff;">new</span> StringBuilder();</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">    <span style="color: #0000ff;">using</span> (StringWriter sw = <span style="color: #0000ff;">new</span> StringWriter(sb))</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">    {</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">        <span style="color: #0000ff;">using</span> (HtmlTextWriter textWriter = <span style="color: #0000ff;">new</span> HtmlTextWriter(sw))</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">        {</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">            control.RenderControl(textWriter);</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">        }</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">    }</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: white;">    <span style="color: #0000ff;">return</span> sb.ToString();</pre>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">}</pre>
</div>
</div>
<div>So now I can go ahead and save myself some curly braces and extra indentation.</div>
<p>I enjoy all the little things one can learn from reader the code others write.</p>
