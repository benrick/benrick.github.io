---
layout: post
title: "Silverlight Attached Properties"
date: 2009-02-03 11:12:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Silverlight-Attached-Properties/"
---
<!-- more -->



<p>One cool feature of XAML is the concept of an attached property. These properties are a way of extending the properties of an element in XAML. By this I don't mean that you can add any arbitrary extra property to an element. What I mean is that child elements have certain properties from their parents attached to them. This is often used as a way of allowing a child element to interact with a parent.</p>
<p>A couple of examples of what I mean can be found in the DockPanel and the Canvas elements. Some attached properties you will find from the Canvas element are Canvas.Top, Canvas.Left, and Canvas.ZOrder. These three let you control the location of the child element within the canvas. A DockPanel element gives DockPanel.Dock, because it is important to know where on the DockPanel your child element is docked.</p>
<p>You have probably noticed by now the naming of these attached properties. They are named in the following way.</p>
<p><em>ElementName.PropertyName</em></p>
<p>Here are some examples of how to use these.</p>
<div>
<pre style="line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: consolas, 'Courier New', courier, monospace; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">&lt;</span><span style="color: #800000">DockPanel</span><span style="color: #0000ff">&gt;</span>
  <span style="color: #0000ff">&lt;</span><span style="color: #800000">Button</span> <span style="color: #ff0000">DockPanel</span>.<span style="color: #ff0000">Dock</span><span style="color: #0000ff">="Left"</span><span style="color: #0000ff">/&gt;</span>
<span style="color: #0000ff">&lt;/</span><span style="color: #800000">DockPanel</span><span style="color: #0000ff">&gt;</span>

<span style="color: #0000ff">&lt;</span><span style="color: #800000">Canvas</span><span style="color: #0000ff">&gt;</span>
  <span style="color: #0000ff">&lt;</span><span style="color: #800000">Ellipse</span> <span style="color: #ff0000">Width</span><span style="color: #0000ff">="100"</span> <span style="color: #ff0000">Height</span><span style="color: #0000ff">="100"</span> <span style="color: #ff0000">Fill</span><span style="color: #0000ff">="Black"</span>
    <span style="color: #ff0000">Canvas</span>.<span style="color: #ff0000">Left</span><span style="color: #0000ff">="25"</span> <span style="color: #ff0000">Canvas</span>.<span style="color: #ff0000">Top</span><span style="color: #0000ff">="25"</span> <span style="color: #0000ff">/&gt;</span>
<span style="color: #0000ff">&lt;/</span><span style="color: #800000">Canvas</span><span style="color: #0000ff">&gt;</span></pre>
</div>
<p>Notice I've docked the button to the left of the DockPanel and the Eliipse has been positioned away from the left and away from the top of the canvas.</p>
<p>It would be a nightmare to try to control positioning of elements inside of the canvas anywhere but on the specific element, and the attached properties allow this to happen. I think they are quote cool.</p>
