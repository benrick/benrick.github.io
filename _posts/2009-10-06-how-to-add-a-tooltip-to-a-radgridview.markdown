---
layout: post
title: "How to Add a ToolTip to a RadGridView"
date: 2009-10-06 13:23:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/How-to-Add-a-ToolTip-to-a-RadGridView"
---
<!-- more -->

<p>So I was using a RadGridView to display some data and I wanted to add a tooltip with more information. Shouldn&rsquo;t be too difficult. I of course checked through intellisense to see if there were any obviously named properties for setting a tooltip.</p>
<p>I checked on the RadGridView tag for the properties and I also checked the GridViewDataColumn for it. Didn&rsquo;t come up with anything so I Binged until I found a potential solution. It didn&rsquo;t really make sense to me and the solution had me doing a lot of what seemed like extra stuff. It was adjusting the tooltip using the styles for the cell. So, then it hit me that I was thinking about this the wrong way. Since I just wanted text and a tooltip why don&rsquo;t I just add that in?</p>
<p>So I took control of things and I just used a template for the column instead. Here is the quick and easy way to add a tooltip into a RadGridView.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">&lt;</span><span style="color: #800000">grid:RadGridView</span> <span style="color: #ff0000">x:Name</span><span style="color: #0000ff">="RadGridView1"</span> <span style="color: #ff0000">AutoGenerateColumns</span><span style="color: #0000ff">="False"</span><span style="color: #0000ff">&gt;</span>            </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">&lt;</span><span style="color: #800000">grid:RadGridView.Columns</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #0000ff">&lt;</span><span style="color: #800000">grid:GridViewColumn</span> <span style="color: #ff0000">Header</span><span style="color: #0000ff">="Person"</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">            <span style="color: #0000ff">&lt;</span><span style="color: #800000">grid:GridViewColumn.CellTemplate</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                <span style="color: #0000ff">&lt;</span><span style="color: #800000">DataTemplate</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                    <span style="color: #0000ff">&lt;</span><span style="color: #800000">TextBlock</span> <span style="color: #ff0000">Text</span><span style="color: #0000ff">="{Binding NickName}"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                       <span style="color: #ff0000">ToolTipService</span>.<span style="color: #ff0000">ToolTip</span><span style="color: #0000ff">="{Binding FullName}"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                       <span style="color: #ff0000">VerticalAlignment</span><span style="color: #0000ff">="Center"</span> <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                <span style="color: #0000ff">&lt;/</span><span style="color: #800000">DataTemplate</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">            <span style="color: #0000ff">&lt;/</span><span style="color: #800000">grid:GridViewColumn.CellTemplate</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #0000ff">&lt;/</span><span style="color: #800000">grid:GridViewColumn</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #0000ff">&lt;</span><span style="color: #800000">grid:GridViewDataColumn</span> <span style="color: #ff0000">Header</span><span style="color: #0000ff">="Place"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">          <span style="color: #ff0000">DataMemberBinding</span><span style="color: #0000ff">="{Binding Place}"</span> <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #0000ff">&lt;</span><span style="color: #800000">grid:GridViewDataColumn</span> <span style="color: #ff0000">Header</span><span style="color: #0000ff">="Thing"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">          <span style="color: #ff0000">DataMemberBinding</span><span style="color: #0000ff">="{Binding Thing}"</span> <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">grid:RadGridView.Columns</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">&lt;/</span><span style="color: #800000">grid:RadGridView</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF--></div>
</div>
<p>&nbsp;</p>
<p>And there you have a tooltip on the text of a cell in a RadGridView. You can obviously add different content items into the DataTemplate so that you can support more advanced templates. Just throw the tooltip on the root element inside the DataTemplate and you&rsquo;ll be set.</p>
