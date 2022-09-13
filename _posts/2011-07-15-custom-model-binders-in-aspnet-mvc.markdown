---
layout: post
title: "Custom Model Binders in ASP.NET MVC"
date: 2011-07-15 10:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Custom-Model-Binders-in-ASPNET-MVC"
---
<!-- more -->

<p>In ASP.NET MVC, our system is built such that the interactions with the user are handled through Actions on our Controllers. We select our actions based on the route the user is using, which is a fancy way of saying that we base it on a pattern found in the URL they’re using. If we were on a page editing an object and we clicked the save button we would be sending the data to a URL somewhat like this one.</p>  <p>&nbsp;</p>  <p>Notice that in our route that we have specified the name of the object that we’re trying to save. There is a default Model Binder for this in MVC that will take the form data that we’re sending and bind it to a CLR objects for us to use in our action. The standard Edit action on a controller looks like this.</p>  <div id="codeSnippetWrapper">   <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet">[HttpPost]<br><span style="color: #0000ff">public</span> ActionResult Edit(<span style="color: #0000ff">int</span> id, FormCollection collection)<br>{<br>    <span style="color: #0000ff">try</span><br>    {<br>        <span style="color: #008000">// TODO: Add update logic here</span><br> <br>        <span style="color: #0000ff">return</span> RedirectToAction(<span style="color: #006080">"Index"</span>);<br>    }<br>    <span style="color: #0000ff">catch</span><br>    {<br>        <span style="color: #0000ff">return</span> View();<br>    }<br>}<br></pre>

  <br></div>

<p>If we were to flesh some of this out the way it’s set up here, we would have code that looked a bit like this.</p>

<div id="codeSnippetWrapper">
  <div id="codeSnippetWrapper">
    <div id="codeSnippetWrapper">
      <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet">[HttpPost]<br><span style="color: #0000ff">public</span> ActionResult Edit(<span style="color: #0000ff">int</span> id, FormCollection collection)<br>{<br>    <span style="color: #0000ff">try</span><br>    {<br>        Profile profile = _profileRepository.GetProfileById(id);<br><br>        profile.FavoriteColor = collection[<span style="color: #006080">"favorite_color"</span>];<br>        profile.FavoriteBoardGame = collection[<span style="color: #006080">"FavoriteBoardGame"</span>];<br><br>        _profileRepository.Add(profile);<br><br>        <span style="color: #0000ff">return</span> RedirectToAction(<span style="color: #006080">"Index"</span>);<br>    }<br>    <span style="color: #0000ff">catch</span><br>    {<br>        <span style="color: #0000ff">return</span> View();<br>    }<br>}<br></pre>

      <br></div>

    <br>What is bad about this is that we are accessing the FormCollection object which is messy and brittle. Once we start testing this code it means that we are going to be repeating code similar to this elsewhere. In our tests we will need to create objects using these magic strings. What this means is that we are now making our code brittle. If we change the string that is required for this we will have to go through our code correcting them. We will also have to find them in our tests or our tests will fail. This is bad. What we should do instead is have these only appear on one place, our model binder. Then all the code we test is using CLR objects that get compile-time checking. To create our Custom Model Binder this is all we need to do is write some code like this.</div>
</div>

<div id="codeSnippetWrapper">
  <div id="codeSnippetWrapper">
    <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> ProfileModelBinder : IModelBinder<br>{<br>    ProfileRepository _profileRepository = <span style="color: #0000ff">new</span> ProfileRepository();<br><br>    <span style="color: #0000ff">public</span> <span style="color: #0000ff">object</span> BindModel(ControllerContext controllerContext, <br>        ModelBindingContext bindingContext)<br>    {<br>        <span style="color: #0000ff">int</span> id = (<span style="color: #0000ff">int</span>)controllerContext.RouteData.Values[<span style="color: #006080">"Id"</span>];<br>        Profile profile = _profileRepository.GetProfileById(id);<br><br>        profile.FavoriteColor = bindingContext<br>            .ValueProvider<br>            .GetValue(<span style="color: #006080">"favorite_color"</span>)<br>            .ToString();<br><br><br>        profile.FavoriteBoardGame = bindingContext<br>            .ValueProvider<br>            .GetValue(<span style="color: #006080">"FavoriteBoardGame"</span>)<br>            .ToString();<br><br>        <span style="color: #0000ff">return</span> profile;<br>    }<br>}<br></pre>

    <br></div>

  <div>&nbsp;</div>
</div>

<p>Notice that we are using the form collection here, but it is limited to this one location. When we test we will just have to pass in the Profile object to our action, which means that we don’t have to worry about these magic strings as much, and we’re also not getting into the situation where our code becomes so brittle that our tests inhibit change. The last thing we need to do is tell MVC that when it is supposed to create a Profile object that it is supposed to use this model binder. To do this, we just need to Add our binder to the collection of binders in the Application_Start method of our GLobal.ascx.cs file. It’s done like this. We say that this binder is for objects of type Profile and give it a binder to use.</p>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet">ModelBinders.Binders.Add(<span style="color: #0000ff">typeof</span> (Profile), <span style="color: #0000ff">new</span> ProfileModelBinder());</pre>

  <br></div>

<p>Now we have a model binder that should let us keep the messy code out of our controllers. Now our controller action looks like this.</p>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet">[HttpPost]<br><span style="color: #0000ff">public</span> ActionResult Edit(Profile profile)<br>{<br>    <span style="color: #0000ff">try</span><br>    {<br>        _profileRepository.Add(profile);<br><br>        <span style="color: #0000ff">return</span> RedirectToAction(<span style="color: #006080">"Index"</span>);<br>    }<br>    <span style="color: #0000ff">catch</span><br>    {<br>        <span style="color: #0000ff">return</span> View();<br>    }<br>}<br></pre>

  <br></div>

<p>That looks a lot cleaner to me, and if there were other things I needed to do during that action, I could do them without all of the ugly binding logic.</p>
