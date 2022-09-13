---
layout: post
title: "Types of ASP.NET MVC 3 Action Results"
date: 2011-08-11 10:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Types-of-ASPNET-MVC-3-Action-Results"
---
<!-- more -->

<p>This will surprise some of you that know me or the company I work for, but not all of our staff are experts with ASP.NET MVC. In fact, I am hoping that the couple who aren’t will read this post and learn a little bit more about the topic.</p>
<p>Since the actions of controllers in MVC are dealt with constantly, I think it is a good place to start. This post is going to briefly describe the different types of results that are available to you in ASP.NET MVC 3. I will show some of the code that makes them work, which should make all of this seem a lot less complicated.</p>
<p>When creating new controllers in ASP.NET MVC 3, they will come with one or more actions by default. This depends on whether you selected a template which includes extras for you. The Empty controller template comes with an Index action with a return value of type ActionResult.</p>
<h2>ActionResult</h2>
<p>The action result is a very generic return value for an action. This is because it is the abstract base class for other types of actions. It is actually a very simple class having only one method that needs implementing.</p>
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">abstract</span> <span style="color: #0000ff">class</span> ActionResult<br>{<br>    <span style="color: #0000ff">public</span> <span style="color: #0000ff">abstract</span> <span style="color: #0000ff">void</span> <br>        ExecuteResult(ControllerContext context);<br>}<br></pre>
<br></div>
<p>Inheriting from the ActionResult are the following classes:</p>
<ul>
<li>ContentResult </li>
<li>EmptyResult </li>
<li>FileResult </li>
<li>HttpStatusCodeResult </li>
<li>JavaScriptResult </li>
<li>RedirectResult </li>
<li>RedirectToRouteResult </li>
<li>ViewResultBase </li>
</ul>
<p>These are the classes that inherit from ActionResult indirectly:</p>
<ul>
<li>FileContentResult </li>
<li>FilePathResult </li>
<li>FileStreamResult </li>
<li>HttpNotFoundResult </li>
<li>HttpUnauthorizedResult </li>
<li>PartialViewResult </li>
<li>ViewResult </li>
</ul>
<h2>ViewResultBase, ViewResult, and PartialViewResult</h2>
<p>The ViewResult is the most common concrete type you will be returning as a controller action. It has an abstract base class called ViewResultBase, which it shares with PartialViewResult.</p>
<p>It is in the ViewResultBase abstract base class that we get access to all of our familiar data objects like: TempData, ViewData, and ViewBag.</p>
<p>PartialViews are not common as action results. PartialViews are not the primary thing being displayed to the user, that is the View. The partial view is usually a widget or something else on the page. It’s usually not the primary content the user sees.</p>
<p>This is the common return syntax, and it means that you’re returning a ViewResult.</p>
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">return</span> View();<br></pre>
<br></div>
<p>That is actually a call to the base Controller.View method, which is just going to call through with some defaults.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">protected</span> <span style="color: #0000ff">internal</span> ViewResult View()<br>{<br>    <span style="color: #0000ff">return</span> View(<span style="color: #0000ff">null</span>, <span style="color: #0000ff">null</span>, <span style="color: #0000ff">null</span>); <br>}<br></pre>
<br></div>
<div>&nbsp;</div>
</div>
<p>The beauty of ASP.NET MVC is actually in its simplicity though, because all that really did was create our ViewResult for us. If we take a look at the method that is being called you can see that we’re just taking a little shortcut and keeping our action clean of this code we would otherwise repeat every time we wanted a ViewResult.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">protected</span> <span style="color: #0000ff">internal</span> <span style="color: #0000ff">virtual</span> ViewResult View(<br>    <span style="color: #0000ff">string</span> viewName, <span style="color: #0000ff">string</span> masterName, <span style="color: #0000ff">object</span> model) <br>{<br>    <span style="color: #0000ff">if</span> (model != <span style="color: #0000ff">null</span>) <br>    { <br>        ViewData.Model = model; <br>    }<br> <br>    <span style="color: #0000ff">return</span> <span style="color: #0000ff">new</span> ViewResult <br>    {<br>        ViewName = viewName,<br>        MasterName = masterName,<br>        ViewData = ViewData, <br>        TempData = TempData<br>    }; <br>} <br></pre>
<br></div>
<p>Notice how simple that really is. All it did was put the model data in if we specified it, give the ViewResult the Controller properties that we set already, and assign the viewName and masterName.</p>
<p>Keep in mind, that we already saw that the abstract method in the ActionResult was the ExecuteResult method. The last two things to look at with the ViewResultBase are the ExecuteResult method and its abstract method FindView, which is being implemented by ViewResult and PartialViewResult.</p>
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">override</span> <span style="color: #0000ff">void</span> ExecuteResult(<br>    ControllerContext context)<br>{<br>    <span style="color: #0000ff">if</span> (context == <span style="color: #0000ff">null</span>) <br>    { <br>        <span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> ArgumentNullException(<span style="color: #006080">"context"</span>); <br>    }<br>    <span style="color: #0000ff">if</span> (String.IsNullOrEmpty(ViewName)) <br>    { <br>        ViewName = context.RouteData<br>            .GetRequiredString(<span style="color: #006080">"action"</span>);<br>    }<br><br>    ViewEngineResult result = <span style="color: #0000ff">null</span>; <br><br>    <span style="color: #0000ff">if</span> (View == <span style="color: #0000ff">null</span>) <br>    { <br>        result = FindView(context); <br>        View = result.View;<br>    } <br><br>    TextWriter writer = context.HttpContext.Response.Output;<br>    ViewContext viewContext = <span style="color: #0000ff">new</span> ViewContext(<br>        context, View, ViewData, TempData, writer);<br>    View.Render(viewContext, writer); <br><br>    <span style="color: #0000ff">if</span> (result != <span style="color: #0000ff">null</span>) <br>    { <br>        result.ViewEngine.ReleaseView(context, View); <br>    }<br>} <br></pre>
<br></div>
<p>This method is also not very complicated. It checks to make sure we have context, and then if we don’t have the ViewName then we get that information from the RouteData. Remember in MVC that the name of action is included in the RouteData, so we can use that as the default view name. This means that in the Index action, if we just call View(), it will give us a ViewName of “Index”.</p>
<p>We then get the view we’re looking for by calling the FindView abstract method, which means we’re calling through to either ViewResult and PartialViewResult. Those I am not going to get into the guts of, but each one is going to try to find the correct view based on the name using its collection of ViewEngines.</p>
<p>Once we have the view, we are able to tell it to render itself using the context and the TextWriter we give to it.</p>
<p>That’s all there is to a ViewResult.</p>
<h2>ContentResult</h2>
<p>The content result lets you define whatever content you wish to return. You can specify the content type, the encoding, and the content. This gives you control to have the system give whatever response you want. This is a good result to use when you need a lot of control over what you’re returning and it’s not one of the standards.</p>
<p>Its ExecuteResult override is extremely simple.</p>
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">override</span> <span style="color: #0000ff">void</span> ExecuteResult(ControllerContext context) <br>{ <br>    <span style="color: #0000ff">if</span> (context == <span style="color: #0000ff">null</span>) <br>    {<br>        <span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> ArgumentNullException(<span style="color: #006080">"context"</span>); <br>    } <br><br>    HttpResponseBase response = context.HttpContext.Response; <br><br>    <span style="color: #0000ff">if</span> (!String.IsNullOrEmpty(ContentType)) <br>    {<br>        response.ContentType = ContentType;<br>    } <br>    <span style="color: #0000ff">if</span> (ContentEncoding != <span style="color: #0000ff">null</span>) <br>    {<br>        response.ContentEncoding = ContentEncoding; <br>    } <br>    <span style="color: #0000ff">if</span> (Content != <span style="color: #0000ff">null</span>) <br>    {<br>        response.Write(Content); <br>    }<br>}<br></pre>
<br></div>
<p>It just puts what you specified directly into the response.</p>
<h2>EmptyResult</h2>
<p>There is no simpler result than the EmptyResult. All it does is override the ExecuteResult method and since that method is void, the method is empty.</p>
<p>I really don’t think I need that code snippet for this one.</p>
<h2>FileResult, FileStreamResult, FilePathResult, and FileContentResult</h2>
<p>If you want specific actions to send files as the response, then the FileResult is for you. Sadly, the FileResult is abstract, so you’ll need to use one of the inheriting classes instead. Each of these actually just overrides the WriteFile method for the abstract FileResult class.</p>
<p>If you want to just send the contents of the file back with the array of bytes for the file, then you want the FileContentResult. It uses the response’s OutputStream and writes those bytes directly into the stream sending it down to the user.</p>
<p>If you want to transmit the file using its name, you can use FilePathResult, which will call through a whole bunch of layers finally down to the HttpResponse. Once there it is going to create a new FileStream for your file and write the stream to the response allowing the file to be accessed from your action.</p>
<p>If you’ve already got a stream you can use the FileStreamResult, which will read all of the data from your stream and then write it into the OutputStream to be send back in the response.</p>
<p>These really aren’t all that complicated, but if you want to have control over the file downloads in your application, this is a great way to do it. These give you the power to put any code you want in your action before you give back the FileResult.</p>
<h2>HttpStatusCodeResult</h2>
<p>The HttpStatusCodeResult is as simple as the ContentResult. In fact, the two are quite similar since they both just directly modify the response object.</p>
<p>This one lets you return any StatusCode you want and you can include a StatusDescription for specifics.</p>
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">override</span> <span style="color: #0000ff">void</span> ExecuteResult(ControllerContext context)<br>{ <br>    <span style="color: #0000ff">if</span> (context == <span style="color: #0000ff">null</span>)<br>    {<br>        <span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> ArgumentNullException(<span style="color: #006080">"context"</span>); <br>    } <br><br>    context.HttpContext.Response.StatusCode = StatusCode; <br>    <span style="color: #0000ff">if</span> (StatusDescription != <span style="color: #0000ff">null</span>)<br>    {<br>        context.HttpContext.Response<br>            .StatusDescription = StatusDescription;<br>    }<br>} <br></pre>
</div>
<p>See how simple that is? It’s basically just two lines of code with some null checking included.</p>
<h3>HttpNotFoundResult and HttpUnauthorizedResult</h3>
<p>These two results are actually just implementing the HttpStatusCodeResult, which means that they are very simple and just set the StatusCode to 404 for the HttpNotFoundResult and 401 for the HttpUnauthorizedResult.</p>
</div>
<div id="codeSnippetWrapper">
<h2>JavaScriptResult</h2>
<p>About as simple as plenty of the others, this is just a quick way of getting JavaScript returned from a action. It’s similar to the ContentResult, but it has the ContentType hardcoded to “application/x-javascript” and just writes out the Script property.</p>
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">override</span> <span style="color: #0000ff">void</span> ExecuteResult(ControllerContext context)<br>{<br>    <span style="color: #0000ff">if</span> (context == <span style="color: #0000ff">null</span>)<br>    {<br>        <span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> ArgumentNullException(<span style="color: #006080">"context"</span>);<br>    } <br><br>    HttpResponseBase response = context.HttpContext.Response; <br>    response.ContentType = <span style="color: #006080">"application/x-javascript"</span>; <br><br>    <span style="color: #0000ff">if</span> (Script != <span style="color: #0000ff">null</span>)<br>    { <br>        response.Write(Script);<br>    }<br>}<br></pre>
<br></div>
<h2>JsonResult</h2>
<p>This one is a bit more complex, but still not very. It also has hardcoded its ContentType, but what makes it a bit more complex is that it uses a hardcoded JavaScriptSerializer to serialize the JSON data before writing it directly to the response.</p>
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">override</span> <span style="color: #0000ff">void</span> ExecuteResult(ControllerContext context)<br>{ <br>    <span style="color: #0000ff">if</span> (context == <span style="color: #0000ff">null</span>)<br>    { <br>        <span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> ArgumentNullException(<span style="color: #006080">"context"</span>);<br>    } <br>    <span style="color: #0000ff">if</span> (JsonRequestBehavior == JsonRequestBehavior.DenyGet &amp;&amp;<br>        String.Equals(context.HttpContext.Request.HttpMethod, <br>            <span style="color: #006080">"GET"</span>, StringComparison.OrdinalIgnoreCase)) <br>    {<br>        <span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> InvalidOperationException(<br>            MvcResources.JsonRequest_GetNotAllowed);<br>    } <br><br>    HttpResponseBase response = context.HttpContext.Response; <br> <br>    <span style="color: #0000ff">if</span> (!String.IsNullOrEmpty(ContentType)) {<br>        response.ContentType = ContentType; <br>    }<br>    <span style="color: #0000ff">else</span> {<br>        response.ContentType = <span style="color: #006080">"application/json"</span>;<br>    } <br>    <span style="color: #0000ff">if</span> (ContentEncoding != <span style="color: #0000ff">null</span>) {<br>        response.ContentEncoding = ContentEncoding; <br>    } <br>    <span style="color: #0000ff">if</span> (Data != <span style="color: #0000ff">null</span>) {<br>        JavaScriptSerializer serializer = <br>            <span style="color: #0000ff">new</span> JavaScriptSerializer(); <br>        response.Write(serializer.Serialize(Data));<br>    }<br>}<br></pre>
<br></div>
<h2>RedirectResult and RedirectToRouteResult</h2>
<p>These to are a little bit more complex, but both are ways of redirecting. Each one can either be a permanent or temporary redirect and they both just use the Redirect methods on the Response object.</p>
<p>For redirecting to a route, it is going to generate a URL to the route using the UrlHelper’s GenerateUrl method. For the RedirectResult it is instead going to use the UrlHelpers GenerateContentUrl method.</p>
<p>Either of these two are useful, and both will maintain your TempData if you need to pass something along with the redirect, all you have to do is put it in TempData.</p>
<h2>Conclusion</h2>
<p>I hope you’ve learned that the results of actions in MVC are not actually very complicated, but there is a lot you can do with them. You’re not being forced into just displaying views. You have a lot more control than that. None of them were that complicated were they? The code under the hood is not always complicated, so it’s worth taking a look from time to time. If you examine how something is working, it’s often far easier to use it.</p>
</div>
