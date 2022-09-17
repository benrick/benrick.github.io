---
layout: post
title: "Performance with DropDownLists and ViewState"
date: 2008-02-29 17:38:00 -0500
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Blog"]
permalink: "/post/Performance-with-DropDownLists-and-ViewState/"
---
<!-- more -->



<p><img src="http://static.flickr.com/2373/2300646878_4d55dc1cda.jpg" border="0" alt="DropDownList-Horns" align="right" />One problem I've noticed on a bunch of sites is a large amount of ViewState. I'm not going to sit here and explain all about ViewState. There are PLENTY of sources for information on that piece of technology. So in an extremely short description of what ViewState is I will say that, "ViewState is a way of preserving the state of the 'Viewed' elements of ASP.NET while the page is sent to the client and back to the server."</p>
<p>So what is the big deal? A little bit of extra information stored in a text file. That doesn't take long to download. Download speeds are really quick. WRONG! Sure, it does not take long to download a little bit of extra data, but ViewState is stored in an input control. This is how the data is able to get back to the server so it can reconstruct the previous state of things. This means clients will push the data up to the server. As many of you probably know upload speeds are much slower than download speeds.</p>
<p>OK, so I need to upload a little bit of extra data. How much are we talking about here? It can't be enough to matter.</p>
<p>I'll show you a bit of testing here. I'll create two ASP.NET pages.</p>
<p><strong>Default.aspx</strong></p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">form</span> <span style="color:#ff0000;">id</span><span style="color:#0000ff;">="form1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span><span style="color:#0000ff;">&gt;</span>
    <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">div</span><span style="color:#0000ff;">&gt;</span>
        <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:DropDownList</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="DropDownList1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#0000ff;">/&gt;</span>
        <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:Button</span> <span style="color:#ff0000;">id</span><span style="color:#0000ff;">="Button1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#ff0000;">Text</span><span style="color:#0000ff;">="Postback"</span> <span style="color:#0000ff;">/&gt;</span>
    <span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">div</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">form</span><span style="color:#0000ff;">&gt;</span></pre>
</div>
<p><strong>Default2.aspx</strong></p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">form</span> <span style="color:#ff0000;">id</span><span style="color:#0000ff;">="form1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span><span style="color:#0000ff;">&gt;</span>
    <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">div</span><span style="color:#0000ff;">&gt;</span>
        <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:DropDownList</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="DropDownList1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#ff0000;">EnableViewState</span><span style="color:#0000ff;">="false"</span> <span style="color:#0000ff;">/&gt;</span>
        <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:Button</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="Button1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#ff0000;">Text</span><span style="color:#0000ff;">="Postback"</span> <span style="color:#0000ff;">/&gt;</span>
    <span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">div</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">form</span><span style="color:#0000ff;">&gt;</span></pre>
</div>
<p><strong>Default.aspx.cs</strong></p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">protected</span> <span style="color:#0000ff;">void</span> Page_Load(<span style="color:#0000ff;">object</span> sender, EventArgs e)
{
    <span style="color:#008000;">// Create my data source (this would normally be data access or something similar)</span>
    System.Collections.Generic.List&lt;ListItem&gt; myData = <span style="color:#0000ff;">new</span> System.Collections.Generic.List&lt;ListItem&gt;();
    <span style="color:#0000ff;">for</span> (<span style="color:#0000ff;">int</span> i = 0; i &lt; 100; i++)
    {
        myData.Add(<span style="color:#0000ff;">new</span> ListItem(<span style="color:#006080;">"Element "</span> + i.ToString(), i.ToString()));
    }
    DropDownList1.DataSource = myData;
    DropDownList1.DataBind();
}</pre>
</div>
<p><strong>Default2.aspx.cs</strong></p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">protected</span> <span style="color:#0000ff;">override</span> <span style="color:#0000ff;">void</span> OnInit(EventArgs e)
{
    <span style="color:#0000ff;">base</span>.OnInit(e);
    <span style="color:#008000;">// Create my data source (this would normally be data access or something similar)</span>
    System.Collections.Generic.List&lt;ListItem&gt; myData = <span style="color:#0000ff;">new</span> System.Collections.Generic.List&lt;ListItem&gt;();
    <span style="color:#0000ff;">for</span> (<span style="color:#0000ff;">int</span> i = 0; i &lt; 100; i++)
    {
        myData.Add(<span style="color:#0000ff;">new</span> ListItem(<span style="color:#006080;">"Element "</span> + i.ToString(), i.ToString()));
    }
    DropDownList1.DataSource = myData;
    DropDownList1.DataBind();
}</pre>
</div>
<p><strong>Note</strong>: When you disable ViewState you'll want to be binding data to the control during Init otherwise you'll run into some problems, because you'll be binding your data after ViewState has been restored.</p>
<p>These are the only differences between the two pages. So how much of a difference is there? The the amount of data being used for ViewState for the page with ViewState enabled on the DropDownList is 3.07 KB and for the page without ViewState enabled on the DropDownList 52 Bytes. Ok so not too big a deal right? Well imagine if you had a few of these on the page, and maybe the page posts back more than once while being used. Perhaps the hosting server is already somewhat slow. Perhaps you have users on dialup. Keep in mind that if you're setting values from the code for most controls it will end up in viewstate. <strong></strong></p>
<p><strong>Note</strong>: Basic form controls will not be using ViewState since they post their values back anyway.</p>
<p>Grab a ViewState Decoder. I use the <a href="http://www.pluralsight.com/tools.aspx" target="_blank">ViewStateDecoder from Pluralsight</a>. If you use a tool to Decode the ViewState from these pages, you'll notice that the values from the dropdownlist are stored within. It will contain 3 things for each row of the dropdownlist. You'll have the Name of the list item, the value of the list item, and a bool. In total 2 strings and a bit, but since ViewState is all strings anyway this is all stored in a string format.</p>
<p>The spark that formed this blog post. I recently took on some pages with far too much viewstate. They had plenty of stuff on them and none of it had ViewState disabled. I took a page that had html source of 256 KB of data, and I dropped it down to 190 KB of data. It started with 74 KB of ViewState (ouch!) and now has 8 KB of ViewState (w00t!). The page is much much faster. It loads instantly now and when it does a postback it doesn't feel like the application is dying. All it took was removing ViewState from a bunch of controls.</p>
