---
layout: post
title: "Why the TextBoxWatermark is the Best AJAX Control"
date: 2007-11-28 15:10:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Why-the-TextBoxWatermark-is-the-Best-AJAX-Control/"
---
<!-- more -->

<p><img src="http://static.flickr.com/2106/2070843877_f417d3bffc.jpg" border="0" alt="bertiebotts-bag-promo" align="right" />There are plenty of AJAX tools being used everyday. The <a href="http://www.asp.net/AJAX/AjaxControlToolkit/Samples/Default.aspx" target="_blank">AJAX Control Toolkit</a> can be likened to&nbsp;a pack of <a href="http://www.mugglenet.com/info/other/beans.shtml" target="_blank">Bertie Bott's Every Flavor Beans</a>; there are far too many choices. Some tools you'll love and some are as&nbsp;useless to you&nbsp;as an earwax flavored bean. Likely no individual developer will find a use for every control in the toolkit, but there is one which I think has a simple use which can be applied to nearly all sites; the <a href="http://www.asp.net/AJAX/AjaxControlToolkit/Samples/TextBoxWatermark/TextBoxWatermark.aspx" target="_blank">TextBoxWatermark control</a>.</p>
<p>When using the&nbsp;TextBoxWatermark&nbsp;control&nbsp;a developer is able to easily place text inside of a TextBox for a user to see. In my experience I've noticed that users tend to read as little text as they can when using forms. It is also difficult sometimes to write necessary information within strict size constraints. Plenty of text boxes require a title on the left so a user know what to type in the box, and then there might be another message below giving more specific instructions.</p>
<p>My personal favorite method for using this control is to place the title of the TextBox to the left and then placing an example in the TextBox as a watermark. This gives the user a nice example which cannot be easily ignored. Overall a very useful control. It is also very simple to use.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">ajaxToolkit:TextBoxWatermarkExtender</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="TextBoxWatermarkExtender1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span>
    <span style="color:#ff0000;">TargetControlID</span><span style="color:#0000ff;">="TextBox1"</span>
    <span style="color:#ff0000;">WatermarkText</span><span style="color:#0000ff;">="YourDomainHere.com"</span>
    <span style="color:#ff0000;">WatermarkCssClass</span><span style="color:#0000ff;">="watermark"</span> <span style="color:#0000ff;">/&gt;</span>
<span style="color:#0000ff;">&lt;</span><span style="color:#800000;">asp:TextBox</span> <span style="color:#ff0000;">ID</span><span style="color:#0000ff;">="TextBox1"</span> <span style="color:#ff0000;">runat</span><span style="color:#0000ff;">="server"</span> <span style="color:#0000ff;">/&gt;</span></pre>
</div>
<p><img src="http://static.flickr.com/2356/2071638738_1c19dfdf2c.jpg" border="0" alt="TextBoxWatermark" /></p>
<p>Using this control it is simple and easy to pass along great information to the user which he or she cannot ignore. It can also make a form look more professional. I am not saying that the TextBoxWatermark is the only useful control. Most of the tools are very useful, but some have some obscure uses. Some of them I know <em>when</em> people use them I just think they <em>shouldn't</em> use them.</p>
<p>Happy AJAXing.</p>
