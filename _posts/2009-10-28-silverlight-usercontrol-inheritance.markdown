---
layout: post
title: "Silverlight UserControl Inheritance"
date: 2009-10-28 09:51:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Silverlight"]
permalink: "/post/Silverlight-UserControl-Inheritance/"
---

<p>One way in which we object-oriented developers try to achieve code reuse is by using inheritance. This allows us to have shared functionality in one place. Awesome we all know how to do this and it&rsquo;s easy right? Try it in Silverlight for your UserControls. It is a little bit more challenging.</p>
<p>The problem we have is that we&rsquo;re working with partial classes and these classes are trying to make things difficult for us. One of them is the noticeably declared one in the code behind file. The other one is created from the XAML file. The XAML file declares the base class it is inheriting from. In this instance it is the UserControl class.</p>
<p>Here are the steps required to use a different base class for your UserControls in Silverlight.</p>
<p><strong>1. Create a class inheriting from UserControl and add your desired extras to the class.</strong></p>
<p><strong>2. Create a normal UserControl class and change the base class in the XAML file. You will need to declare an xml namespace for the namespace your base class is in, and use that namespace when declaring the base class.</strong></p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">&lt;</span><span style="color: #800000"><strong>UI:MyBaseClass</strong></span> <span style="color: #ff0000">x:Class</span><span style="color: #0000ff">="MyProject.UI.UserControls.ConcreteImplementation"</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #ff0000">xmlns</span><span style="color: #0000ff">="http://schemas.microsoft.com/winfx/2006/xaml/presentation"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #ff0000">xmlns:x</span><span style="color: #0000ff">="http://schemas.microsoft.com/winfx/2006/xaml"</span> </pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><strong>    <span style="color: #ff0000">xmlns:UI</span><span style="color: #0000ff">="clr-namespace:MyProject.UI"</span> </strong></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #ff0000">Width</span><span style="color: #0000ff">="400"</span> <span style="color: #ff0000">Height</span><span style="color: #0000ff">="300"</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">&lt;</span><span style="color: #800000">Grid</span> <span style="color: #ff0000">x:Name</span><span style="color: #0000ff">="LayoutRoot"</span> <span style="color: #ff0000">Background</span><span style="color: #0000ff">="White"</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">&nbsp;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">Grid</span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">&lt;/</span><span style="color: #800000"><strong>UI:MyBaseClass</strong></span><span style="color: #0000ff">&gt;</span></pre>
<!--CRLF--></div>
</div>
<p><strong>3. Change the inheritance in the code behind (.cs or .vb) file so that it is using the new base class. [Optional &ndash; Because of the way partials work you don&rsquo;t need to declare this one as inheriting from the base class, but it does make things more obvious for someone using the code.]</strong></p>
<p>Enjoy using your base class in Silverlight.</p>
