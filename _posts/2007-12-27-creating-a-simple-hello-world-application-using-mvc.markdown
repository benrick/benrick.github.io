---
layout: post
title: "Creating a Simple Hello World Application Using MVC"
date: 2007-12-27 20:25:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Creating-a-Simple-Hello-World-Application-Using-MVC", "/post/creating-a-simple-hello-world-application-using-mvc"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>So I am finally sitting down to play with the ASP.NET MVC Framework. I've installed Visual Studio 2008 on my machine. You can obtain a <a href="http://msdn2.microsoft.com/en-us/vstudio/products/aa700831.aspx" target="_blank">90 day free trial of Visual Studio 2008</a> from Microsoft if you don't own a copy. There are also <a href="http://www.microsoft.com/express/" target="_blank">Express Editions of Visual Studio 2008</a>.</p>
<p>After installing Visual Studio 2008 I installed the <a href="http://www.asp.net/downloads/3.5-extensions/" target="_blank">ASP.NET 3.5 Extensions Preview</a>. It contains the required components to use the new MVC Framework. Now that you have it installed open up Visual Studio and create a new project. Choose the <em>web</em> section and select <em>ASP.NET MVC Web Application</em>. I named my project "HelloMvc".</p>
<p>&nbsp;<img src="http://static.flickr.com/2264/2142110166_2130b37b69.jpg" border="0" alt="NewProjectHelloMvc" /></p>
<p>Here you can see the files currently in this empty project. Notice there are a bunch of files that it comes with including a Controller and a couple of Views.</p>
<p>&nbsp;<img src="http://static.flickr.com/2253/2142110198_6733215dab.jpg" border="0" alt="HelloMvcEmptySolution" /></p>
<p>So now run the application by pressing <em>ctrl </em>+<em> F5</em>. You'll see this page once you run the application.</p>
<p><img src="http://static.flickr.com/2309/2141318629_3b2205064e.jpg" border="0" alt="HelloMvcStartingPage" /></p>
<p>Fairly simple for now, but hey it works. Now we should try to figure out how to create a simple static page. We'll make it look kind of like that about view that is already in there. We want it to be hello. OK, so click on the <em>About Us</em> link in the application. You'll be at a URL similar to this one <a title="http://localhost:64701/Home/About" href="http://localhost:64701/Home/About">http://localhost:64701/Home/About</a>. So as a nice test try changing "About" to Hello in the address bar. You'll receive this nice error message which tells us the first step in creating our Hello World page.</p>
<p>&nbsp;<img src="http://static.flickr.com/2313/2141318677_04270c08eb.jpg" border="0" alt="HelloMvcActionNotFound" /></p>
<p>Ok so we need to define an action in our controller. The Home part of our URL is saying we want to use the HomeController, so open up that file in the Controllers folder and add the following code into that file.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">[ControllerAction]
<span style="color:#0000ff;">public</span> <span style="color:#0000ff;">void</span> Hello()
{
    RenderView(<span style="color:#006080;">"Hello"</span>);
}</pre>
</div>
<p>Notice that all we needed to do here is to use the ControllerAction attribute for a method we define. We'll defined the method named <em>Hello</em> by added a line calling the <em>RenderView</em> method. Congratulations you've defined your first Controller Action. So we now refresh the page where we previously received an error message, and we're greeted with a new one. So we are on the right track.</p>
<p>&nbsp;<img src="http://static.flickr.com/2263/2141318739_95e20bfc5f.jpg" border="0" alt="HelloMvcViewNotFound" /></p>
<p>Now we need to create the view that we are trying to call in our Controller Action. So we'll right click on the <em>Home</em> folder inside of the <em>View</em> folder and select <em>Add</em> then <em>New Item</em>. Here is where Microsoft has tried to trick you. They've now changed how you attach to MasterPages. Instead of picking a <em>Web Form</em> and checking a box you now have a new choice <em>Web Content Form</em>. Make sure you pick that or you'll not get a MasterPage added for you. It will look like this.</p>
<p>&nbsp;<img src="http://static.flickr.com/2157/2141318777_4306fe9b1f.jpg" border="0" alt="HelloMvcAddNewView" /></p>
<p>So now that we have that empty view we can quickly add a nice message into it. So go ahead and type in some html like the following.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">h2</span><span style="color:#0000ff;">&gt;</span>Hello World! MVC is here!<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">h2</span><span style="color:#0000ff;">&gt;</span></pre>
</div>
<p><a href="http://11011.net/software/vspaste"></a></p>
<p>Now you need to go into the code of this view and place in the following.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">using</span> System;
<span style="color:#0000ff;">using</span> System.Web;
<span style="color:#0000ff;">using</span> System.Web.Mvc;

<span style="color:#0000ff;">namespace</span> HelloMvc.Views.Home
{
    <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">partial</span> <span style="color:#0000ff;">class</span> Hello : ViewPage
    {
    }
}</pre>
</div>
<p>Notice here that we need to inherit from the ViewPage class instead of the System.Web.UI.Page class. We are instead using the System.Web.Mvc.ViewPage class. This will allow our .aspx page to work as a view. Make sure to build the application and then open up the view again in the browser. Woohoo you've successfully created an MVC Controller Action and a View. And as some icing on the cake we will now add a link to our view on the MasterPage so that we can easily access this Hello View whenever we want to.</p>
<p>Open up the Site.Master file. It is located in the <em>\Views\Shared</em>. You will see an unordered list in the html. There are currently two list items in the list; Home and About Us. You will want to add a new one using the following code.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">li</span><span style="color:#0000ff;">&gt;<span style="background-color:#ffff00;">&lt;%</span></span>= Html.ActionLink("Say Hello", "Hello", "Home") <span style="background-color:#ffff00;">%&gt;</span><span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">li</span><span style="color:#0000ff;">&gt;</span></pre>
</div>
<p><a href="http://11011.net/software/vspaste"></a>Now refresh the page. From anywhere on this site you can now get to the Hello World View. The method we used here took 3 arguments. The first is the text which appears for the link, the second is the name of the view, and the third is the name of the controller. The following is our final product. We have the Hello World page as well as a nice link to it.</p>
<p><img src="http://static.flickr.com/2326/2141334913_5f926af481.jpg" border="0" alt="HelloMvcHelloView" /></p>
<p>Enjoy creating simple MVC Views!</p>
