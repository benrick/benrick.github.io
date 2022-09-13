---
layout: post
title: "Wire up your ViewModels using a Service Locator"
date: 2010-10-24 14:57:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Wire-up-your-ViewModels-using-a-Service-Locator", "/post/wire-up-your-viewmodels-using-a-service-locator"]
---
<!-- more -->

<p>No MVVM solution is complete without having the DataContext bound to a ViewModel, but this wouldn’t be a fun development community if there were not some disagreement on the specifics of how to achieve certain goals. I will be recommending how I like to wire up ViewModels. There are other ways of doing this, but I will explain some of the reasons I use this method.</p>  <p>You can start by building a View that needs to have certain traits in its ViewModel and then create a well-tested ViewModel separately. This ViewModel should have all of the properties and data required by the View. Make sure you also have any commands or other functionality the View will require. It is then your job to make the connection between these two objects. The way I like doing this is by using a Service Locator to give my View the ViewModel it needs. This also gives me a good centralized location where I can make sure that my ViewModels are wired up the way I need them to be.</p>  <p>To create our service model we are going to need to create a class which has methods returning the ViewModels we are using in our Views. We should have one getter per ViewModel to be requested. I tend to use names matching the name of the ViewModel for the getters. The service locator will look a bit like this when you’re done. (You can also use an IoC container in the service locator, which is what I do in all of my production code. In that case you would just use the IoC container rather than instantiating the object as is done in this example.)</p>  <h4>Code Listing 1 – The Service Locator:</h4>  <div id="codeSnippetWrapper">   <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> ServiceLocator<br>{<br>    <span style="color: #0000ff">public</span> AwesomeViewModel AwesomeViewModel<br>    {<br>        get { <span style="color: #0000ff">return</span> <span style="color: #0000ff">new</span> AwesomeViewModel(); }<br>    }<br>}<br></pre>

  <br></div>
Notice that I can pass in any parameters needed for the ViewModel constructor so my ViewModel can depend on abstractions. The service locator can be more complicated than this if other work needs to be done to create these ViewModels. An example of such a situation is if I have shared dependencies or I am using an IoC container to create my objects. 

<p>Now that we have our code written to get us our ViewModel object we need to make this class available to all of our Views. This can be achieved by creating an instance of one of these as a static resource in our App.xaml file. Static resources defined here are easily accessible.</p>

<h4>Code Listing 2 – Declaring the Service Locator as a Resource in App.xaml:</h4>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">&lt;</span><span style="color: #800000">Application</span> <span style="color: #ff0000">x:Class</span><span style="color: #0000ff">="Awesome.App"</span><br>    <span style="color: #ff0000">xmlns</span><span style="color: #0000ff">="http://schemas.microsoft.com/winfx/2006/xaml/presentation"</span><br>    <span style="color: #ff0000">xmlns:x</span><span style="color: #0000ff">="http://schemas.microsoft.com/winfx/2006/xaml"</span><br>    <span style="color: #ff0000">xmlns:Awesome</span><span style="color: #0000ff">="clr-namespace:Awesome"</span><br>    <span style="color: #ff0000">StartupUri</span><span style="color: #0000ff">="MainWindow.xaml"</span><span style="color: #0000ff">&gt;</span><br>  <span style="color: #0000ff">&lt;</span><span style="color: #800000">Application.Resources</span><span style="color: #0000ff">&gt;</span><br>    <span style="color: #0000ff">&lt;</span><span style="color: #800000">Awesome:ServiceLocator</span> <span style="color: #ff0000">x:Key</span><span style="color: #0000ff">="SvcLoc"</span> <span style="color: #0000ff">/&gt;</span><br>  <span style="color: #0000ff">&lt;/</span><span style="color: #800000">Application.Resources</span><span style="color: #0000ff">&gt;</span><br><span style="color: #0000ff">&lt;/</span><span style="color: #800000">Application</span><span style="color: #0000ff">&gt;</span></pre>

  <br></div>

<p>The key that we have assigned to this resource is how we will reference it when we access it later. In other parts of our code we will just specify in our bindings that we are accessing this static resource and calling its properties to get the data that we need. In fact this is exactly how we can get our ViewModel into our View. When we bind our DataContext we will tell it that our source is going to be this ServiceLocator instance and that we are binding our DataContext to a specified path, which is a property of the ServiceLocator.</p>

<p>The binding can be done either of these two ways. I don’t really prefer one or the other. These are effectively the same things, so it really comes down to preference.</p>

<h4>Code Listing 3 – Binding the DataContext to the ServiceLocator:</h4>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">&lt;</span><span style="color: #800000">Window.DataContext</span><span style="color: #0000ff">&gt;</span><br>  <span style="color: #0000ff">&lt;</span><span style="color: #800000">Binding</span> <span style="color: #ff0000">Path</span><span style="color: #0000ff">="AwesomeViewModel"</span> <br>    <span style="color: #ff0000">Source</span><span style="color: #0000ff">="{StaticResource SvcLoc}"</span><span style="color: #0000ff">/&gt;</span><br><span style="color: #0000ff">&lt;/</span><span style="color: #800000">Window.DataContext</span><span style="color: #0000ff">&gt;</span></pre>

  <br></div>

<h4>Code Listing 4 – Binding the DataContext to the ServiceLocator Inline:</h4>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet">DataContext="{Binding AwesomeViewModel, Source={StaticResource SvcLoc}}"</pre>

  <br></div>

<p>Now we can access this DataContext throughout our View by just binding to different paths on it.</p>

<p>I like this approach because it keeps the binding in the XAML and not in the code. It is also nice because we are able to bind easily to properties and have these properties do dependency injection for our ViewModels. The centralization of all of this ViewModel creation is also very convenient. We are able to visit this one class to make adjustments for how the entire application handles its ViewModel initialization.</p>
