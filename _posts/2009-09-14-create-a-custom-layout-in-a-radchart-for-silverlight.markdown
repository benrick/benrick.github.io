---
layout: post
title: "Create a Custom Layout in a RadChart for Silverlight"
date: 2009-09-14 14:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Create-a-Custom-Layout-in-a-RadChart-for-Silverlight"
---
<!-- more -->

<p>The default layout for the RadChart for Silverlight is a very common one. It has a title at the top, a legend on the right, and an area in the middle reserved for the chart. It looks roughly like this.</p>
<p><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="DefaultLayout" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/CreateaCustomLayoutforaRadChartforSilver_A46F/DefaultLayout_3.png" border="0" alt="DefaultLayout" width="400" height="299" />&nbsp;</p>
<p>If you started by using the default layout for the chart then you probably used these properties in some way.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">Chart1.DefaultView.ChartArea</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">Chart1.DefaultView.ChartLegend</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">Chart1.DefaultView.ChartTitle</pre>
<!--CRLF--></div>
</div>
<p>When you switch you&rsquo;ll be adding in your own custom content inside of the <em>RadChart</em> tag in the XAML. You can only have one piece of content inside of the <em>RadChart</em> tag, so make sure you put in something like a <em>Grid</em> to do the layout. In this case I am removing the Legend and am going to just have the <em>Title </em>and <em>Area</em> in the chart, so I add this XAML for my chart. With this in place I am now able to see a spiffy new chart.</p>
<p><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="UsingDefaultLayout" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/CreateaCustomLayoutforaRadChartforSilver_A46F/UsingDefaultLayout_3.png" border="0" alt="UsingDefaultLayout" width="399" height="297" /></p>
<p>One more thing to do here. I&rsquo;ve got my new layout in there but the chart is still using the old layout. Notice that the space for the chart and the legend still exist. I have to tell the chart that I don&rsquo;t want it using the default layout anymore. There is an all-too-obvious name for the Boolean property to disable the default layout. Just set <em>UseDefaultLayout</em> to False in the XAML and you&rsquo;ll be using the correct layout.</p>
<p><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="CustomLayout" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/CreateaCustomLayoutforaRadChartforSilver_A46F/CustomLayout_3.png" border="0" alt="CustomLayout" width="399" height="298" /></p>
<p><strong><span style="text-decoration: underline;">XAML for Custom RadChart Layout</span></strong></p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">&lt;</span><span style="color: #800000">telerikChart:RadChart</span> <span style="color: #ff0000">x:Name</span><span style="color: #0000ff">="Chart1"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #ff0000">UseDefaultLayout</span><span style="color: #0000ff">="False"</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">&lt;</span><span style="color: #800000">Grid</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #0000ff">&lt;</span><span style="color: #800000">Grid.RowDefinitions</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">            <span style="color: #0000ff">&lt;</span><span style="color: #800000">RowDefinition</span> <span style="color: #ff0000">Height</span><span style="color: #0000ff">="Auto"</span> <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">            <span style="color: #0000ff">&lt;</span><span style="color: #800000">RowDefinition</span> <span style="color: #ff0000">Height</span><span style="color: #0000ff">="*"</span> <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #0000ff">&lt;/</span><span style="color: #800000">Grid.RowDefinitions</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">&nbsp;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #0000ff">&lt;</span><span style="color: #800000">telerikCharting:ChartTitle</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">            <span style="color: #ff0000">Content</span><span style="color: #0000ff">="Number of Hamburgers Eaten"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">            <span style="color: #ff0000">HorizontalAlignment</span><span style="color: #0000ff">="Center"</span><span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #0000ff">&lt;</span><span style="color: #800000">telerikCharting:ChartArea</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">            <span style="color: #ff0000">x:Name</span><span style="color: #0000ff">="ChartArea1"</span> <span style="color: #ff0000">Grid</span>.<span style="color: #ff0000">Row</span><span style="color: #0000ff">="1"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">            <span style="color: #ff0000">NoDataString</span><span style="color: #0000ff">=""</span> <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">Grid</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">&lt;/</span><span style="color: #800000">telerikChart:RadChart</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF--></div>
</div>
