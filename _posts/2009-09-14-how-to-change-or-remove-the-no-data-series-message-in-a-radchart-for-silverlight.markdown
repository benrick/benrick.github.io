---
layout: post
title: "How to Change or Remove the No Data Series Message in a RadChart for Silverlight"
date: 2009-09-14 14:01:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/How-to-Change-or-Remove-the-No-Data-Series-Message-in-a-RadChart-for-Silverlight/"
---
<!-- more -->



<p>I&rsquo;ve been working with the charts from Telerik&rsquo;s RadControls for Silverlight. I am of course not blocking the UI when I make my requests to get my data for the charts. Since I am doing this late-loading of the data into the charts it causes them to initially show a message, &ldquo;No Data Series.&rdquo; This message is not a bad default message since it provides adequate information about why the chart is not displaying data.</p>
<p><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="NoDataSeries" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/HowtoChangeorRemovetheNoDataSeriesMessag_A066/NoDataSeries_3.png" border="0" alt="NoDataSeries" width="399" height="263" /></p>
<p>However, since my charts will always start with no data, that message is quite silly. Luckily, changing or removing that message is easy. There is a convenient property on the <em>ChartArea</em> object called <em>NoDataString</em>, and in my case I set that as an empty string and I receive this nice blank chart now. I could potentially change the message to something else.</p>
<p><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="BlankChart" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/HowtoChangeorRemovetheNoDataSeriesMessag_A066/BlankChart_3.png" border="0" alt="BlankChart" width="401" height="259" /></p>
<p><span style="text-decoration: underline;"><strong>Snippet of Relevant Code</strong></span></p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">&lt;</span><span style="color: #800000">UserControl</span> <span style="color: #ff0000">x:Class</span><span style="color: #0000ff">="MyProject.UI.Charts.MyChart"</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #ff0000">xmlns</span><span style="color: #0000ff">="http://schemas.microsoft.com/winfx/2006/xaml/presentation"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #ff0000">xmlns:x</span><span style="color: #0000ff">="http://schemas.microsoft.com/winfx/2006/xaml"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #ff0000">xmlns:telerikChart</span>=</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">"clr-namespace:Telerik.Windows.Controls;assembly=Telerik.Windows.Controls.Charting"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #ff0000">xmlns:telerikCharting</span>=</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">"clr-namespace:Telerik.Windows.Controls.Charting;assembly=Telerik.Windows.Controls.Charting"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #ff0000">Width</span><span style="color: #0000ff">="400"</span> <span style="color: #ff0000">Height</span><span style="color: #0000ff">="300"</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">&lt;</span><span style="color: #800000">Grid</span> <span style="color: #ff0000">x:Name</span><span style="color: #0000ff">="LayoutRoot"</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #0000ff">&lt;</span><span style="color: #800000">telerikChart:RadChart</span> <span style="color: #ff0000">x:Name</span><span style="color: #0000ff">="Chart1"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">           <span style="color: #ff0000">UseDefaultLayout</span><span style="color: #0000ff">="False"</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">            <span style="color: #0000ff">&lt;</span><span style="color: #800000">Grid</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                <span style="color: #0000ff">&lt;</span><span style="color: #800000">Grid.RowDefinitions</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                    <span style="color: #0000ff">&lt;</span><span style="color: #800000">RowDefinition</span> <span style="color: #ff0000">Height</span><span style="color: #0000ff">="Auto"</span> <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                    <span style="color: #0000ff">&lt;</span><span style="color: #800000">RowDefinition</span> <span style="color: #ff0000">Height</span><span style="color: #0000ff">="*"</span> <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                <span style="color: #0000ff">&lt;/</span><span style="color: #800000">Grid.RowDefinitions</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                <span style="color: #0000ff">&lt;</span><span style="color: #800000">telerikCharting:ChartTitle</span> <span style="color: #ff0000">Content</span><span style="color: #0000ff">="My Chart"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                  <span style="color: #ff0000">HorizontalAlignment</span><span style="color: #0000ff">="Center"</span><span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                <span style="color: #0000ff">&lt;</span><span style="color: #800000">telerikCharting:ChartArea</span> <span style="color: #ff0000">x:Name</span><span style="color: #0000ff">="ChartArea1"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">                  <span style="color: #ff0000">Grid</span>.<span style="color: #ff0000">Row</span><span style="color: #0000ff">="1"</span> <span style="color: #ff0000">NoDataString</span><span style="color: #0000ff">=""</span> <span style="color: #0000ff">/&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">            <span style="color: #0000ff">&lt;/</span><span style="color: #800000">Grid</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">        <span style="color: #0000ff">&lt;/</span><span style="color: #800000">telerikChart:RadChart</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">Grid</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">&lt;/</span><span style="color: #800000">UserControl</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF--></div>
</div>
