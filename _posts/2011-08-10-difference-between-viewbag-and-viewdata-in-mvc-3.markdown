---
layout: post
title: "Difference Between ViewBag and ViewData in MVC 3"
date: 2011-08-10 10:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["ASP.NET", "ASP.NET MVC"]
permalink: "/post/Difference-Between-ViewBag-and-ViewData-in-MVC-3/"
---
<!-- more -->



<p>If you’re new to ASP.NET MVC, you might be wondering what these two things are and when to use each one. If you’ve been using MVC and are just new to version 3 of MVC, you are probably wondering what this new ViewBag is for and if it’s different from the ViewData you’ve been using. In the beginning of the Summer, I had the opportunity to explain this difference to the two NimblePros interns when they started working on ASP.NET MVC 3 for the first time. This post should serve as a reference for them, me, and anyone else who is interested in knowing more about these two objects.</p>  <p>ViewBag and ViewData serve the same purpose in allowing developers to pass data from controllers to views. When you put objects in either one, those objects become accessible in the view. This is one way we interact between the view and the controller in ASP.NET MVC. We pass data from the view to the controller by placing it in these objects.</p>  <h2>How ViewData Works</h2>  <p>ViewData is a dictionary of objects that are accessible using strings as keys. This means that we will write code like this:</p>  <p><strong>In the Controller</strong></p>  <div id="codeSnippetWrapper">   <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">public</span> ActionResult Index()<br>{<br>    var softwareDevelopers = <span style="color: #0000ff">new</span> List&lt;<span style="color: #0000ff">string</span>&gt;<br>    {<br>        <span style="color: #006080">"Brendan Enrick"</span>, <br>        <span style="color: #006080">"Kevin Kuebler"</span>, <br>        <span style="color: #006080">"Todd Ropog"</span><br>    };<br><br>    ViewData[<span style="color: #006080">"softwareDevelopers"</span>] = softwareDevelopers;<br><br>    <span style="color: #0000ff">return</span> View();<br>}<br></pre>

  <br></div>

<p><strong>In the View</strong></p>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">&lt;</span><span style="color: #800000">ul</span><span style="color: #0000ff">&gt;</span><br>@foreach (var developer in (List<span style="color: #0000ff">&lt;</span><span style="color: #800000">string</span><span style="color: #0000ff">&gt;</span>)ViewData["softwareDevelopers"])<br>{<br>    <span style="color: #0000ff">&lt;</span><span style="color: #800000">li</span><span style="color: #0000ff">&gt;</span><br>        @developer<br>    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">li</span><span style="color: #0000ff">&gt;</span><br>}<br><span style="color: #0000ff">&lt;/</span><span style="color: #800000">ul</span><span style="color: #0000ff">&gt;</span></pre>

  <br></div>

<p>Notice that when we go to use out object on the view that we have to cast it since the ViewData is storing everything as object. Also, we need to be careful since we’re using magic strings to access these values.</p>

<h2>How ViewBag Works</h2>

<p>ViewBag uses the dynamic feature that was added in to C# 4. It allows an object to dynamically have properties added to it. The code we write using ViewBag will look like this:</p>

<p><strong>In the Controller</strong></p>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">public</span> ActionResult Index()<br>{<br>    var softwareDevelopers = <span style="color: #0000ff">new</span> List&lt;<span style="color: #0000ff">string</span>&gt;<br>    {<br>        <span style="color: #006080">"Brendan Enrick"</span>, <br>        <span style="color: #006080">"Kevin Kuebler"</span>, <br>        <span style="color: #006080">"Todd Ropog"</span><br>    };<br><br>    ViewBag.softwareDevelopers = softwareDevelopers;<br><br>    <span style="color: #0000ff">return</span> View();<br>}<br></pre>

  <br></div>

<p><strong>In the View</strong></p>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">&lt;</span><span style="color: #800000">ul</span><span style="color: #0000ff">&gt;</span><br>@foreach (var developer in ViewBag.softwareDevelopers)<br>{<br>    <span style="color: #0000ff">&lt;</span><span style="color: #800000">li</span><span style="color: #0000ff">&gt;</span><br>        @developer<br>    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">li</span><span style="color: #0000ff">&gt;</span><br>}<br><span style="color: #0000ff">&lt;/</span><span style="color: #800000">ul</span><span style="color: #0000ff">&gt;</span></pre>

  <br></div>



<p>Notice here that we did not have to cast our object when using the ViewBag. This is because the dynamic we used lets us know the type. <em>Keep in mind that these dynamics are as the name suggest, dynamic, which means that you need to be careful as these are basically magic properties instead of magic strings.</em></p>

<h2>ViewBag and ViewData Under the Hood</h2>

<p>So these two things seem to work almost exactly the same. What’s the difference? The difference is only in how you access the data. ViewBag is actually just a wrapper around the ViewData object, and its whole purpose is to let you use dynamics to access the data instead of using magic strings. Some people prefer one style over the other. You can pick whichever you like. In fact, because they’re the same data just with two different ways of accessing it, you can use them interchangeably. (I don’t recommend this, but you can do it.) If you want you are able to put data into the ViewBag and access it from the ViewData or put stuff in the ViewData and access it in the ViewBag.</p>

<p>This is all that the ViewBag property is. It’s just a DynamicViewDataDictionary with the ViewData as its data.</p>

<div id="codeSnippetWrapper">
  <div id="codeSnippetWrapper">
    <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">public</span> dynamic ViewBag <br>{ <br>    get <br>    { <br>        <span style="color: #0000ff">if</span> (_dynamicViewData == <span style="color: #0000ff">null</span>) <br>        {<br>            _dynamicViewData = <br>                <span style="color: #0000ff">new</span> DynamicViewDataDictionary(() =&gt; ViewData); <br>        }<br>        <span style="color: #0000ff">return</span> _dynamicViewData;<br>    }<br>} </pre>

    <br>Then when we access the dynamic members of the DynamicViewDataDictionary, we are actually just getting this override of the DynamicObject’s TryGetMember. In this method, it’s just using the name of the member we tried to access as the string key for the ViewData dictionary.</div>
</div>

<div id="codeSnippetWrapper">
  <div id="codeSnippetWrapper">
    <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">public</span> <span style="color: #0000ff">override</span> <span style="color: #0000ff">bool</span> TryGetMember(<br>    GetMemberBinder binder, <span style="color: #0000ff">out</span> <span style="color: #0000ff">object</span> result)<br>{<br>    result = ViewData[binder.Name]; <br>    <span style="color: #0000ff">return</span> <span style="color: #0000ff">true</span>;<br>}</pre>

    <br>So for a short answer:</div>
</div>

<p><em>These two objects are two different ways of accessing the exact same data. The ViewBag is just a dynamic wrapper around the ViewData dictionary.</em></p>
