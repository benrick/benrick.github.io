---
layout: post
title: "Using a DropDownList without ViewState"
date: 2008-08-06 14:09:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Using-a-DropDownList-without-ViewState", "/post/using-a-dropdownlist-without-viewstate"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>One of the most ViewState heavy controls is the DropDownList. It stores in ViewState the Text and Value for every ListItem in the DropDownList. This means large Lists can get really nasty when ViewState comes into play. They also include all of these entries a second time because they're all in the html. Being in the html will only slow the page down as it is sent to the user, but the ViewState is downloaded by the user and also must be uploaded back up to the web server. This is a horrible user experience if the page has a large amount of ViewState. Since upload speeds are usually worse than download, the user will probably not like the amount of time the postbacks on the site take. In the following example I am going to show how much ViewState can be saved by simply reloading the data into the DropDownList each time the page is requested.</p>
<p>This is how much ViewState my hundred item DropDownList contains at the beginning of this example.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">input</span> <span style="color:#ff0000;">type</span><span style="color:#0000ff;">="hidden"</span> <span style="color:#ff0000;">name</span><span style="color:#0000ff;">="__VIEWSTATE"</span> <span style="color:#ff0000;">id</span><span style="color:#0000ff;">="__VIEWSTATE"</span> <span style="color:#ff0000;">value</span><span style="color:#0000ff;">="/wEPDwULLTEwNjkzMDQ2Nz
MPZBYCAgMPZBYEAgEPEA8WAh4LXyFEYXRhQm91bmRnZBAVZAlFbGVtZW50IDAJRWxlbWVudCAxCUVsZW1lbnQg
MglFbGVtZW50IDMJRWxlbWVudCA0CUVsZW1lbnQgNQlFbGVtZW50IDYJRWxlbWVudCA3CUVsZW1lbnQgOAlFbG
VtZW50IDkKRWxlbWVudCAxMApFbGVtZW50IDExCkVsZW1lbnQgMTIKRWxlbWVudCAxMwpFbGVtZW50IDE0CkVs
ZW1lbnQgMTUKRWxlbWVudCAxNgpFbGVtZW50IDE3CkVsZW1lbnQgMTgKRWxlbWVudCAxOQpFbGVtZW50IDIwCk
VsZW1lbnQgMjEKRWxlbWVudCAyMgpFbGVtZW50IDIzCkVsZW1lbnQgMjQKRWxlbWVudCAyNQpFbGVtZW50IDI2
CkVsZW1lbnQgMjcKRWxlbWVudCAyOApFbGVtZW50IDI5CkVsZW1lbnQgMzAKRWxlbWVudCAzMQpFbGVtZW50ID
MyCkVsZW1lbnQgMzMKRWxlbWVudCAzNApFbGVtZW50IDM1CkVsZW1lbnQgMzYKRWxlbWVudCAzNwpFbGVtZW50
IDM4CkVsZW1lbnQgMzkKRWxlbWVudCA0MApFbGVtZW50IDQxCkVsZW1lbnQgNDIKRWxlbWVudCA0MwpFbGVtZW
50IDQ0CkVsZW1lbnQgNDUKRWxlbWVudCA0NgpFbGVtZW50IDQ3CkVsZW1lbnQgNDgKRWxlbWVudCA0OQpFbGVt
ZW50IDUwCkVsZW1lbnQgNTEKRWxlbWVudCA1MgpFbGVtZW50IDUzCkVsZW1lbnQgNTQKRWxlbWVudCA1NQpFbG
VtZW50IDU2CkVsZW1lbnQgNTcKRWxlbWVudCA1OApFbGVtZW50IDU5CkVsZW1lbnQgNjAKRWxlbWVudCA2MQpF
bGVtZW50IDYyCkVsZW1lbnQgNjMKRWxlbWVudCA2NApFbGVtZW50IDY1CkVsZW1lbnQgNjYKRWxlbWVudCA2Nw
pFbGVtZW50IDY4CkVsZW1lbnQgNjkKRWxlbWVudCA3MApFbGVtZW50IDcxCkVsZW1lbnQgNzIKRWxlbWVudCA3
MwpFbGVtZW50IDc0CkVsZW1lbnQgNzUKRWxlbWVudCA3NgpFbGVtZW50IDc3CkVsZW1lbnQgNzgKRWxlbWVudC
A3OQpFbGVtZW50IDgwCkVsZW1lbnQgODEKRWxlbWVudCA4MgpFbGVtZW50IDgzCkVsZW1lbnQgODQKRWxlbWVu
dCA4NQpFbGVtZW50IDg2CkVsZW1lbnQgODcKRWxlbWVudCA4OApFbGVtZW50IDg5CkVsZW1lbnQgOTAKRWxlbW
VudCA5MQpFbGVtZW50IDkyCkVsZW1lbnQgOTMKRWxlbWVudCA5NApFbGVtZW50IDk1CkVsZW1lbnQgOTYKRWxl
bWVudCA5NwpFbGVtZW50IDk4CkVsZW1lbnQgOTkVZAlFbGVtZW50IDAJRWxlbWVudCAxCUVsZW1lbnQgMglFbG
VtZW50IDMJRWxlbWVudCA0CUVsZW1lbnQgNQlFbGVtZW50IDYJRWxlbWVudCA3CUVsZW1lbnQgOAlFbGVtZW50
IDkKRWxlbWVudCAxMApFbGVtZW50IDExCkVsZW1lbnQgMTIKRWxlbWVudCAxMwpFbGVtZW50IDE0CkVsZW1lbn
QgMTUKRWxlbWVudCAxNgpFbGVtZW50IDE3CkVsZW1lbnQgMTgKRWxlbWVudCAxOQpFbGVtZW50IDIwCkVsZW1l
bnQgMjEKRWxlbWVudCAyMgpFbGVtZW50IDIzCkVsZW1lbnQgMjQKRWxlbWVudCAyNQpFbGVtZW50IDI2CkVsZW
1lbnQgMjcKRWxlbWVudCAyOApFbGVtZW50IDI5CkVsZW1lbnQgMzAKRWxlbWVudCAzMQpFbGVtZW50IDMyCkVs
ZW1lbnQgMzMKRWxlbWVudCAzNApFbGVtZW50IDM1CkVsZW1lbnQgMzYKRWxlbWVudCAzNwpFbGVtZW50IDM4Ck
VsZW1lbnQgMzkKRWxlbWVudCA0MApFbGVtZW50IDQxCkVsZW1lbnQgNDIKRWxlbWVudCA0MwpFbGVtZW50IDQ0
CkVsZW1lbnQgNDUKRWxlbWVudCA0NgpFbGVtZW50IDQ3CkVsZW1lbnQgNDgKRWxlbWVudCA0OQpFbGVtZW50ID
UwCkVsZW1lbnQgNTEKRWxlbWVudCA1MgpFbGVtZW50IDUzCkVsZW1lbnQgNTQKRWxlbWVudCA1NQpFbGVtZW50
IDU2CkVsZW1lbnQgNTcKRWxlbWVudCA1OApFbGVtZW50IDU5CkVsZW1lbnQgNjAKRWxlbWVudCA2MQpFbGVtZW
50IDYyCkVsZW1lbnQgNjMKRWxlbWVudCA2NApFbGVtZW50IDY1CkVsZW1lbnQgNjYKRWxlbWVudCA2NwpFbGVt
ZW50IDY4CkVsZW1lbnQgNjkKRWxlbWVudCA3MApFbGVtZW50IDcxCkVsZW1lbnQgNzIKRWxlbWVudCA3MwpFbG
VtZW50IDc0CkVsZW1lbnQgNzUKRWxlbWVudCA3NgpFbGVtZW50IDc3CkVsZW1lbnQgNzgKRWxlbWVudCA3OQpF
bGVtZW50IDgwCkVsZW1lbnQgODEKRWxlbWVudCA4MgpFbGVtZW50IDgzCkVsZW1lbnQgODQKRWxlbWVudCA4NQ
pFbGVtZW50IDg2CkVsZW1lbnQgODcKRWxlbWVudCA4OApFbGVtZW50IDg5CkVsZW1lbnQgOTAKRWxlbWVudCA5
MQpFbGVtZW50IDkyCkVsZW1lbnQgOTMKRWxlbWVudCA5NApFbGVtZW50IDk1CkVsZW1lbnQgOTYKRWxlbWVudC
A5NwpFbGVtZW50IDk4CkVsZW1lbnQgOTkUKwNkZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dn
Z2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2dnZ2
RkAgUPDxYCHgRUZXh0BQlFbGVtZW50IDBkZGQCc/YoLQgXzJamhzzCRizwdOQs9w=="</span> <span style="color:#0000ff;">/&gt;</span></pre>
</div>
<p>And at the end of it, this is all that remains.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;">&lt;input type=<span style="color:#006080;">"hidden"</span> name=<span style="color:#006080;">"__VIEWSTATE"</span> id=<span style="color:#006080;">"__VIEWSTATE"</span> <span style="color:#0000ff;">value</span>=<span style="color:#006080;">"/wEPDwULLTEwNjkzMDQ2NzM
PZBYCAgMPZBYCAgUPDxYCHgRUZXh0BQpFbGVtZW50IDIzZGRky26p9Cn4TiZyx2yoBv7mRgWW+gQ="</span> /&gt;</pre>
</div>
<p>It is a frightening thought, but there are plenty of sites with far more ViewState than this. I am talking some people have talked to me about pages that are multiple megabytes in size.</p>
<p>In the following example I use a simple page with 1 DropDownList, 1 Button, and 1 Label.</p>
<p>Here is the starting Default.aspx page.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="background-color:#ffff00;">&lt;%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %&gt;</span>

<span style="color:#0000ff;">&lt;!</span><span style="color:#800000;">DOCTYPE</span> <span style="color:#ff0000;">html</span> <span style="color:#ff0000;">PUBLIC</span> <span style="color:#0000ff;">"-//W3C//DTD XHTML 1.0 Transitional//EN"</span> <span style="color:#0000ff;">"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;</span><span style="color:#800000;">html</span> <span style="color:#ff0000;">xmlns</span><span style="color:#0000ff;">="http://www.w3.org/1999/xhtml"</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;</span><span style="color:#800000;">head</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span><span style="color:#0000ff;">&gt;</span>
    <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">title</span><span style="color:#0000ff;">&gt;</span>Untitled Page<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">title</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">head</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;</span><span style="color:#800000;">body</span><span style="color:#0000ff;">&gt;</span>
    <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">form</span> <span style="color:#ff0000;">id</span><span style="color:#0000ff;">="form1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span><span style="color:#0000ff;">&gt;</span>
    <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">div</span><span style="color:#0000ff;">&gt;</span>
        <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:DropDownList</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="DropDownList1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#ff0000;">EnableViewState</span><span style="color:#0000ff;">="true"</span> <span style="color:#0000ff;">/&gt;</span>
        <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:Button</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="Button1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#ff0000;">Text</span><span style="color:#0000ff;">="Postback"</span> <span style="color:#0000ff;">/&gt;</span>
        <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:Label</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="Label1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#0000ff;">/&gt;</span>
    <span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">div</span><span style="color:#0000ff;">&gt;</span>
    <span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">form</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">body</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">html</span><span style="color:#0000ff;">&gt;</span></pre>
</div>
<p>Here is the starting Default.aspx.cs code-behind file.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">using</span> System;
<span style="color:#0000ff;">using</span> System.Web.UI.WebControls;

<span style="color:#0000ff;">public</span> <span style="color:#0000ff;">partial</span> <span style="color:#0000ff;">class</span> _Default : System.Web.UI.Page 
{
    <span style="color:#0000ff;">protected</span> <span style="color:#0000ff;">void</span> Page_Load(<span style="color:#0000ff;">object</span> sender, EventArgs e)
    {
        <span style="color:#0000ff;">if</span> (!IsPostBack)
        {
            <span style="color:#008000;">// Create my data source (this would normally be data access or something similar)</span>
            System.Collections.Generic.List&lt;ListItem&gt; myData = <span style="color:#0000ff;">new</span> System.Collections.Generic.List&lt;ListItem&gt;();
            <span style="color:#0000ff;">for</span> (<span style="color:#0000ff;">int</span> i = 0; i &lt; 100; i++)
            {
                myData.Add(<span style="color:#0000ff;">new</span> ListItem(<span style="color:#006080;">"Element "</span> + i.ToString(), i.ToString()));
            }
            DropDownList1.DataSource = myData;
            DropDownList1.DataBind();
        }
        <span style="color:#0000ff;">else</span>
        {
            Label1.Text = DropDownList1.SelectedValue;
        }
    }
}</pre>
</div>
<p>Now we can make a little change here. We need to disable ViewState. The other change that we need to make is that we now have to populate the data on every request. We also need to make sure that we populate the DropDownList before Initialization of the Page occurs. This means we should override OnInit and place out code before base.OnInit. The reason we do this is so that we have data loaded in the DropDownList before the selected value of controls are set for us. Otherwise we would have to handle this on our own.</p>
<p>This is the new Default.aspx</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="background-color:#ffff00;">&lt;%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %&gt;</span>

<span style="color:#0000ff;">&lt;!</span><span style="color:#800000;">DOCTYPE</span> <span style="color:#ff0000;">html</span> <span style="color:#ff0000;">PUBLIC</span> <span style="color:#0000ff;">"-//W3C//DTD XHTML 1.0 Transitional//EN"</span> <span style="color:#0000ff;">"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;</span><span style="color:#800000;">html</span> <span style="color:#ff0000;">xmlns</span><span style="color:#0000ff;">="http://www.w3.org/1999/xhtml"</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;</span><span style="color:#800000;">head</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span><span style="color:#0000ff;">&gt;</span>
    <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">title</span><span style="color:#0000ff;">&gt;</span>Untitled Page<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">title</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">head</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;</span><span style="color:#800000;">body</span><span style="color:#0000ff;">&gt;</span>
    <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">form</span> <span style="color:#ff0000;">id</span><span style="color:#0000ff;">="form1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span><span style="color:#0000ff;">&gt;</span>
    <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">div</span><span style="color:#0000ff;">&gt;</span>
        <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:DropDownList</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="DropDownList1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#ff0000;">EnableViewState</span><span style="color:#0000ff;">="false"</span> <span style="color:#0000ff;">/&gt;</span>
        <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:Button</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="Button1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#ff0000;">Text</span><span style="color:#0000ff;">="Postback"</span> <span style="color:#0000ff;">/&gt;</span>
        <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:Label</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="Label1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#0000ff;">/&gt;</span>
    <span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">div</span><span style="color:#0000ff;">&gt;</span>
    <span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">form</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">body</span><span style="color:#0000ff;">&gt;</span>
<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">html</span><span style="color:#0000ff;">&gt;</span></pre>
</div>
<p>This is the new Default.aspx.cs</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">using</span> System;
<span style="color:#0000ff;">using</span> System.Web.UI.WebControls;

<span style="color:#0000ff;">public</span> <span style="color:#0000ff;">partial</span> <span style="color:#0000ff;">class</span> _Default : System.Web.UI.Page 
{
    <span style="color:#0000ff;">protected</span> <span style="color:#0000ff;">override</span> <span style="color:#0000ff;">void</span> OnInit(EventArgs e)
    {
        <span style="color:#008000;">// Create my data source (this would normally be data access or something similar)</span>
        System.Collections.Generic.List&lt;ListItem&gt; myData = <span style="color:#0000ff;">new</span> System.Collections.Generic.List&lt;ListItem&gt;();
        <span style="color:#0000ff;">for</span> (<span style="color:#0000ff;">int</span> i = 0; i &lt; 100; i++)
        {
            myData.Add(<span style="color:#0000ff;">new</span> ListItem(<span style="color:#006080;">"Element "</span> + i.ToString(), i.ToString()));
        }
        DropDownList1.DataSource = myData;
        DropDownList1.DataBind();
        <span style="color:#0000ff;">base</span>.OnInit(e);
    }

    <span style="color:#0000ff;">protected</span> <span style="color:#0000ff;">void</span> Page_Load(<span style="color:#0000ff;">object</span> sender, EventArgs e)
    {
        <span style="color:#0000ff;">if</span> (IsPostBack)
        {
            Label1.Text = DropDownList1.SelectedValue;
        }
    }
}</pre>
</div>
<p>Enjoy not having TONS of extra ViewState. Remember that ViewState is extremely useful, but can cause problems if you ignore its existence completely. It can lead to huge pages that are quite slow.</p>
