---
layout: post
title: "Unable to cast object of type 'Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection' to type 'Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection'"
date: 2008-01-22 16:26:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Unable-to-cast-object-of-type-MicrosoftVisualStudioTestToolsUnitTestingTestConfigurationSection-to-type-MicrosoftVisualStudioTestToolsUnitTestingTestConfigurationSection"
---
<!-- more -->

<p>Earlier today I was trying to track down this error.</p>
<blockquote>
<p>Unit Test Adapter threw exception: The type initializer for 'Microsoft.VisualStudio.TestTools.UnitTesting.TestConfiguration' threw an exception. Unable to cast object of type 'Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection' to type 'Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection'</p>
</blockquote>
<p>I tried Googling for it, but I didn't find anything regarding this problem. I was pretty sure it was a VS 2008 upgrade issue, because it looks like it is a dll version issue. Since the two classes it is trying to cast between are the same class. So I must be using the wrong version of a dll and I not too long ago upgraded to VS 2008.</p>
<p>In the App.config file there is a config section defined like this.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">section</span> <span style="color:#ff0000;">name</span><span style="color:#0000ff;">="microsoft.visualstudio.testtools"</span> <span style="color:#ff0000;">type</span><span style="color:#0000ff;">="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"</span><span style="color:#0000ff;">/&gt;</span></pre>
</div>
<p>All that needs to be changes is to change the 8 into a 9. Once you make that change all will work once again.</p>
<p>This will work for pretty much any version issue you run into which looks like this. It is funny because the two class names are the same. This is your signal that it is a version issue. The nice thing is that you usually just need to change an 8 into a 9.</p>
<p>I hope everyone is enjoying Visual Studio 2008. Have a great day!</p>
