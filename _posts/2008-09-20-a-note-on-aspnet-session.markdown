---
layout: post
title: "A Note on ASP.NET Session"
date: 2008-09-20 22:13:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/A-Note-on-ASPNET-Session/"
---
<!-- more -->

<p>A while back, I was asked a question by one of the junior developers here at Lake Quincy Media. I had him working on a little feature on an ASP.NET site which could be easily handled using Session. "Where is session stored, on the server or the client?" he asked. As a quick response I said that it's stored on the server. He followed that by saying, "So it doesn't use a cookie?"</p>
<p>And that was all it took to set me on one of my usual lengthy explanations of how a piece of functionality actually works.</p>
<h3>How is ASP.NET Session stored?</h3>
<p>In ASP.NET, session data is stored on the server. It is stored in a per-user basis and maintained only for a limited period of time. Anyone who has used sessions knows that it is accessed during server-side code execution and is accessed using strings as keys. So we know that Session data is stored as key-value pairs. The following is basically how we access the session information. In this code I store a string in Session and pull it back out from session.</p>
<div>
<div style="font-size: 8pt; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: white; border-style: none; padding: 0px;"><span style="color:#0000ff;">string</span> name = <span style="color:#006080;">"Brendan Enrick"</span>;</pre>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">Session[<span style="color:#006080;">"fullName"</span>] = name;</pre>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: white; border-style: none; padding: 0px;"><span style="color:#0000ff;">string</span> nameFromSession = Session[<span style="color:#006080;">"fullName"</span>] <span style="color:#0000ff;">as</span> <span style="color:#0000ff;">string</span>;</pre>
</div>
</div>
<p>Pretty simple really. It is a nice way to store data for a user during this visit to the site.</p>
<h3>How are users associated with their session?</h3>
<p>In the default scenario for ASP.NET Session, cookies are used. No, the data is not stored in the cookie. When a Session is started on the site, the user is given a cookie (yummy cookie) which contains a unique identifier for accessing the session. While the user navigates around the site, the browser sends the cookie information to the server. This is what keeps the user associated with his session. Each time the server receives the cookie from the user so when your code requests data from session, it is pulling the data from the session associated with that user.</p>
<h4>Can cookies be avoided?</h4>
<p>Yes, it is possible to avoid using cookies. Session is able to run without cookies by setting a boolean property in the web.config file to true. The property is called <em>cookieless</em> and it is on <em>sessionState</em>. When session is not using cookies it instead places the SessionId in the url the user requests. Internal links on the site contain the unique session id so that the processing which occurs on the server is able to access the correct session values. I prefer not using this method because it just makes URLs all over the site look terrible.</p>
<h3>How long are values saved in session?</h3>
<p>By default the timeout for session in ASP.NET is 20 minutes. This means that the session will expire 20 minutes after the user last accessed the site, so as long as the user continues using the site it will not expire. If the user waits 25 minutes before clicking a link, the session will have expired. It is easy to adjust the length of time before sessions expire. In the web configuration file you can simply adjust the value for <em>timeout</em> on the <em>sessionState</em> element.</p>
<div>
<div style="font-size: 8pt; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: white; border-style: none; padding: 0px;"><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">sessionState</span> <span style="color:#ff0000;">cookieless</span><span style="color:#0000ff;">="false"</span> <span style="color:#ff0000;">timeout</span><span style="color:#0000ff;">="45"</span> <span style="color:#0000ff;">/&gt;</span></pre>
</div>
</div>
<p>And this is why asking me questions can be a bit crazy. I'll first go on a lecture about the topic and then eventually I'll publish a blog post so I don't have to lecture again. Now if someone asks me that question I'll send him here.</p>
