---
layout: post
title: "ASP.NET Supports Valid HTML Attributes in its Tags"
date: 2009-01-26 14:36:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/ASPNET-Supports-Valid-HTML-Attributes-in-its-Tags/"
---
<!-- more -->

<p>While reading an article, I came across a misconception that seems all too common with people using ASP.NET, and they need to <strong><em><span style="text-decoration: underline;">stop trusting intellisense!!!</span></em></strong> I love intellisense, but you can't trust in it entirely. It doesn't know everything, so as a rule, I will state that if html supports something... SO DOES ASP.NET!</p>
<p>So now that I am done ranting I first want to say I am not intending to bash the author or the publisher site. Both have some great content and are valuable to the .NET community. I simply want to step in and provide some clarity by providing some explanation and an alternative solution to the problem. The <a href="http://aspalliance.com/1803_CodeSnip_Adding_a_ToolTip_for_Each_List_Item" target="_blank">article</a> is about adding a tooltip to individual items in a dropdown list. There are plenty of reasons to do this, including the one the author states which is that the list might have a fixed width and will display badly in IE. Below is an example of a DropDownList with this problem.</p>
<p><img style="border: 0px none ;" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ASP.NETSupportsValidHTMLAttributesinitsT_C610/SmallDropDown_3.jpg" border="0" alt="SmallDropDown" width="409" height="267"></p>
<p>That is a terrible UI problem right there. I personally prefer the way Firefox handles this situation, but aside from that we might want to use a tooltip anyway.</p>
<p><img style="border: 0px none ;" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ASP.NETSupportsValidHTMLAttributesinitsT_C610/GoFirefox_3.jpg" border="0" alt="GoFirefox" width="591" height="110"></p>
<p>The thing that seems to throw everyone off is that some ASP.NET controls don't seem to have many properties when you look at intellisense. A lot of them don't include <em>style, title</em>, or some other commonly used attributes. THEY ARE STILL THERE!! Underneath the hood ASP.NET is basically just the HTML you know and love. So when you go in and try to add the title attribute to a ListItem, you will not see it in the intellisense box.</p>
<p><img style="border: 0px none ;" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ASP.NETSupportsValidHTMLAttributesinitsT_C610/TitleNotInList_3.jpg" border="0" alt="TitleNotInList" width="637" height="140"></p>
<p>The article suggested doing a foreach loop over the Items in the DropDownList and edit their <em>title</em> property. Well, you can actually just set the title property. ASP.NET will give you a warning about it because it isn't an ASP.NET attribute, but it will work.</p>
<p><img style="border: 0px none ;" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ASP.NETSupportsValidHTMLAttributesinitsT_C610/ValidationMessage_3.jpg" border="0" alt="ValidationMessage" width="655" height="89"></p>
<p>I would also like to mention that this also works with the <em>style</em> attribute. I've heard plenty of people complain that some controls don't support the style attribute in ASP.NET. If their underlying HTML control supports a tag it supports a tag. For this example since the <em>option</em> tag supports the <em>title</em> attribute it means that the <em>ListItem</em> of a <em>DropDownList</em> also supports the attribute.</p>
<p><img style="border: 0px none ;" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ASP.NETSupportsValidHTMLAttributesinitsT_C610/DropDownWithToolTip_3.jpg" border="0" alt="DropDownWithToolTip" width="261" height="255"></p>
<p>In his article he does one great thing showing people that it is very easy to make changes to the html by simply using the Attributes collection of any control in the code behind an ASP.NET page. Using this allows us to alter any attribute we wish. One thing&nbsp; you need to be careful of is the ease through which we are able to add duplicate attributes or cause other problems by this.</p>
<p>In his article he uses the following line of code to add in the title attribute.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;">_listItem.Attributes.Add(<span style="color: #006080;">"title"</span>, _listItem.Text); 
</pre>
</div>
<p>If the above code were to somehow run twice it literally would add two separate title tags into the HTML which is not always the best way of handling things. Just figured I would throw this out there so people have a better understanding how the connection between ASP.NET and HTML. Some people try to separate ASP.NET as some new thing when at the end of the day it is really just creating HTML. Don't let ASP.NET be mystical, it is relatively easy to understand if you just read articles and blogs. Be curious and questioning of everything. Yes, I mean for you to question what I tell you also. Plenty of things I write over a long period of time will be questionable and some will just be outright wrong. Everyone will do it. Yes, even people writing documentation.</p>
