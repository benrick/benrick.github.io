---
layout: post
title: "Dynamically Register an Asynchronous Postback Control with a ScriptManager"
date: 2007-07-17 20:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
permalink: "/post/Dynamically-Register-an-Asynchronous-Postback-Control-with-a-ScriptManager/"
---
<!-- more -->



<p>In order to use an update panel you have to specify the triggers either individually or by setting the ChildrenAsTriggers property of the UpdatePanel. Sometimes you may need to set these triggers dynamically such as if the desired trigger is inside of a repeater and is not inside of the update panel. In instances such as this you will need to from the code behind register the control with the script manager. To do this you will want to use the RegisterAsynchPostBackControl function of the ScriptManager in the following manner:</p>
<pre id="ctl00_MainBody_SourceCode">ScriptManager1.RegisterAsyncPostBackControl(Button1);</pre>
<p>This code could be inside of the OnItemDataBound event handler for a repeater or even in page load if you want to register it in code. The script manager will now know to hijack the postbacks created by this control and turn them into asynchronous postbacks. The good thing about this is that you will now not do a full postback. The bad part is that you still have to let the update panel know that it needs to update after the asynchronous postback. To do this you will want to Call the Update() method of the UpdatePanel so for example you might do the following:</p>
<pre id="ctl00_MainBody_SourceCode">protected void Button1_Click(object sender, EventArgs e)
{
&nbsp;&nbsp;&nbsp;&nbsp; // Do work
&nbsp;&nbsp;&nbsp;  UpdatePanel1.Update();
}
</pre>
<p>By using this method you will not be tied to your .aspx pages. It is not quite as elegant as when you just use the triggers collection in the UpdatePanel on the .aspx page, but this way of doing this is still easy and possible when inside of a template such as in a repeater or a gridview.</p>
<p>Happy AJAXing!&nbsp;</p>
