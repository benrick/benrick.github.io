---
layout: post
title: "Passing ViewData to User Controls in ASP.NET MVC Preview 4"
date: 2008-07-24 15:55:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Passing-ViewData-to-User-Controls-in-ASPNET-MVC-Preview-4", "/post/passing-viewdata-to-user-controls-in-aspnet-mvc-preview-4"]
---
<!-- more -->

<p>Yesterday I was upgrading an ASP.NET MVC site from Preview 2 to Preview 4. For the most part this is an easy process. Some assemblies needed to be updated and some information updated in the web.config file. Route declaration changed, but the same information is still required, so updating that was pretty easy. The released documentation and examples clearly show these changes. I also had to make the change to my controller actions so that they return ActionResults instead of being void methods. Again, this is a fairly simple task.</p>
<p>There was an adjustment to user controls which caused some problems though. Yasir and I were working on this task together so we could both learn about the preview 4 changes in MVC. We scoured articles looking for this information, and we tried many different changes to the user control.</p>
<p>Our problem was that we could not get access to the ViewData. ViewData in the user control was always null. It was quite annoying. Eventually in desperation after reading articles and release notes and not finding what we were looking for, we started reading the source code for MVC. We took a look at this file, which is the one containing the extension method we were calling in the .aspx files. <a title="http://www.codeplex.com/aspnet/SourceControl/FileView.aspx?itemId=8283&amp;changeSetId=12044" href="http://www.codeplex.com/aspnet/SourceControl/FileView.aspx?itemId=8283&amp;changeSetId=12044" target="_blank">System.Web.Mvc.UserControlExtensions</a> This file contains the extension method RenderUserControl, which our code used.</p>
<p><strong>The .aspx code we were using</strong></p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="background-color:#ffff00;">&lt;%</span><pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: white; border-style: none; padding: 0px;"><span style="color:#606060;">   </span>=Html.RenderUserControl(<span style="color:#006080;">"~/Views/Shared/MyUserControl.ascx"</span>, ViewData, <span style="color:#0000ff;">new</span> { DisplayTitle = <span style="color:#006080;">"Hello World!"</span> }) </pre>
<span style="background-color:#ffff00;">%&gt;</span></pre>
</div>
<p><strong>RenderUserControl calls this method called DoRendering</strong></p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">private</span> <span style="color:#0000ff;">static</span> <span style="color:#0000ff;">string</span> DoRendering(ViewUserControl instance, ViewContext context, <span style="color:#0000ff;">object</span> controlData, <span style="color:#0000ff;">object</span> propertySettings) {
            ViewPage dummyPage = <span style="color:#0000ff;">new</span> ViewPage();
            dummyPage.ViewContext = context;
            dummyPage.Controls.Add(instance);
            dummyPage.InitHelpers();

            <span style="color:#008000;">//set the properties</span>

            SetUserControlProperties(instance, propertySettings);

            <span style="color:#0000ff;">if</span> (controlData != <span style="color:#0000ff;">null</span>) {
                instance.ViewData.Model = controlData;
            }
            <span style="color:#0000ff;">else</span> {
                instance.ViewData = context.ViewData;
            }

            <span style="color:#008000;">//Render it</span>

            <span style="color:#0000ff;">string</span> result = HtmlExtensionUtility.RenderPage(dummyPage);

            <span style="color:#0000ff;">return</span> result;
        }</pre>
</div>
<p>In my haste to find a solution, I didn't read the code very carefully. All I noticed was exactly how to solve our problem. I discovered that the <em>controlData</em> parameter we were passing to this method was being assigned into <em>instance.ViewData.Model</em>. I didn't even read the next couple of lines which gave away the real answer. We went and added in the <em>.Model</em> to our code so that it could access the ViewData. The ViewData we were passing was going into a property of the ViewData called Model, so we just used it. We went to our user control and we changed the code there. This felt really bad to us, but we went along with it.</p>
<p>Today I realized our error. I was thinking about the code we had looked at this morning, and I realized our mistake. I was wondering, "Why was it checking if control data was null? If it was null shouldn't ViewData.Model be null? That's our ViewData right?" That is when I realized what must have been after that.</p>
<p>We were not supposed to be using Model. We had some standard ViewData. No strongly-typed ViewData was being used. We were using an the standard ViewDataDictionary object and passing it to the user control. A ViewUserControl object (which is the class we were inheriting from) supports generics. It was at that time when I realized exactly what everything was being used for. The <em>Model</em> property and the <em>controlData</em> parameter are there for strongly typed ViewData. You can use boxing and unboxing or generics to pass strongly-typed data to your ViewControl. The parameter and the generic Model were added so that the ViewData property of the ViewUserControl would not be interfered with.</p>
<p>This solution the MVC guys use allows custom ViewData to be used without having to muck the ViewData property of the user controls. Since they added this extra piece it could be the generic one. So now I have gone and changed my code. I no longer pass the ViewData as was done in the past. It is now simply grabbed from the context of the page. I pass a null value instead of passing in any controlData to the RenderUserControl method. It wires everything up for me now.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">&lt;%=Html.RenderUserControl(<span style="color:#006080;">"~/Views/Shared/MyUserControl.ascx"</span>, <span style="color:#0000ff;">null</span>, <span style="color:#0000ff;">new</span> { DisplayTitle = <span style="color:#006080;">"Hello World!"</span> })%&gt;</pre>
</div>
<p>As a reminder to everyone. Open source code means that you can go look at the code. If you are not sure how something works, just go read the code. It is freely available on CodePlex. You can look at how everything is working and get a much better understanding of the inner workings of the technology.</p>
