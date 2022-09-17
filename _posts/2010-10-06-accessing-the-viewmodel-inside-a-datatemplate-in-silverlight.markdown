---
layout: post
title: "Accessing the ViewModel Inside a DataTemplate in Silverlight"
date: 2010-10-06 10:40:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Accessing-the-ViewModel-Inside-a-DataTemplate-in-Silverlight/"
---
<!-- more -->



<p>I’ve been doing a lot of Windows Phone 7 Development, which means that I have also been doing a lot of Silveright development, so here is a tip for accessing your ViewModel when you’re in a DataTemplate.</p>  <p>In Silveright, DataTemplates are used when binding data to a control. For example if I want to list users I will define the DataTemplate, which will define the XAML that will be bound to for each of the users in the list. When I do this, the data context for the DataTemplate is my user and no longer the VM. I have a few options here, I can modify the user to have what I need, I can access some global class which has what I need or can access my ViewModel, or I could do what I prefer doing, which is just to name my View.</p>  <p>I give my name a view, and I can then create a binding which accesses an element by name instead of by using its current data context. To do this I can just name my View like this.</p>  <div id="codeSnippetWrapper">   <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">&lt;</span><span style="color: #800000">Views:ViewBase</span><br>    ...<br>    <span style="color: #ff0000">x:Name</span><span style="color: #0000ff">="TheView"</span><br>    <span style="color: #ff0000">DataContext</span><span style="color: #0000ff">="{Binding BarViewModel, Source={StaticResource SL}}"</span><span style="color: #0000ff">&gt;</span><br></pre>

  <br></div>

<div id="codeSnippetWrapper">&nbsp;</div>

<p>Then in my binding I can access it using the ElementName property like this. This example is wiring up a Click event using MVVM Light Toolkit’s EventToCommand.</p>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">&lt;</span><span style="color: #800000">Custom:Interaction.Triggers</span><span style="color: #0000ff">&gt;</span><br>    <span style="color: #0000ff">&lt;</span><span style="color: #800000">Custom:EventTrigger</span> <span style="color: #ff0000">EventName</span><span style="color: #0000ff">="Click"</span><span style="color: #0000ff">&gt;</span><br>        <span style="color: #0000ff">&lt;</span><span style="color: #800000">Command:EventToCommand</span> <br>          <span style="color: #ff0000">Command</span><span style="color: #0000ff">="{Binding DataContext.DoSomething, ElementName=TheView}"</span> <br>          <span style="color: #ff0000">CommandParameter</span><span style="color: #0000ff">="{Binding}"</span> <span style="color: #0000ff">/&gt;</span><br>    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">Custom:EventTrigger</span><span style="color: #0000ff">&gt;</span><br><span style="color: #0000ff">&lt;/</span><span style="color: #800000">Custom:Interaction.Triggers</span><span style="color: #0000ff">&gt;</span></pre>

  <br></div>

<div id="codeSnippetWrapper">&nbsp;</div>

<div id="codeSnippetWrapper">This allows me to access the commands on my ViewModel while I am using a DataTemplate. Without doing the “ElementName=TheView”, I would not easily be able to access the command from my ViewModel. I would only be able to access the commands from the User object.</div>
