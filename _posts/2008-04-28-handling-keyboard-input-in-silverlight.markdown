---
layout: post
title: "Handling Keyboard Input in Silverlight"
date: 2008-04-28 17:30:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET", "Orcs Goblins  and .NET"]
alias: ["/post/Handling-Keyboard-Input-in-Silverlight", "/post/handling-keyboard-input-in-silverlight"]
---
<!-- more -->

<p>Keyboard input is one of the most important aspects of truly rich programming environments. I understand that one usually identifies a rich interface as one which can interacted with visually. This interaction feels more natural than keyboard interaction. The mouse allows the user to feel as if he can truly manipulate the environment in which he is working. One cannot, however, ignore the importance of the keyboard in any environment expecting to be able to perform much meaningful work. Again I'll be talking about some code that I wrote many months ago. Sorry for being so late mentioning this stuff. I just need to find more time in the day. I'll find that 25th hour eventually.</p>
<p>Handling keyboard input with Silverlight 2.0 is very easy. In Silverlight 1.1 there wasn't even an enumeration for the keys. Now that it is included one simply has to wire up some handlers for keyboard input. For my purposes I've been using it for gaming, but others could be using this for almost anything. Keep that in mind and use this by adapting it to your needs at the time.</p>
<p>Initializing the key up and key down event handlers is very easy. You just call a couple of lines like these and create a couple of empty methods which we will write later, so we start with this.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">this</span>.KeyDown += <span style="color:#0000ff;">new</span> KeyEventHandler(Page_KeyDown);
<span style="color:#0000ff;">this</span>.KeyUp += <span style="color:#0000ff;">new</span> KeyEventHandler(Page_KeyUp);</pre>
</div>
<p>This will tie these events to the page. If you want to tie them to another element, use its x:Name instead of this. I like to have a more central method for handling keyboard events, so I'll create a method for handling the keys and I will call that method in my event handlers.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">private void</span> Page_KeyUp(<span style="color:#0000ff;">object</span> sender, KeyEventArgs e)
{
    HandleKey(e.Key, <span style="color:#0000ff;">false</span>);
}

<span style="color:#0000ff;">private void</span> Page_KeyDown(<span style="color:#0000ff;">object</span> sender, KeyEventArgs e)
{
    HandleKey(e.Key, <span style="color:#0000ff;">true</span>);
}</pre>
</div>
<p>Notice that the KeyEventArgs parameter, e, has data about the event, so if you needed more information from it you could obtain it and pass it to HandleKey also. I prefer this to having too much logic directly in my event handlers. The boolean value I am passing is just letting me know whether the key is being pressed or released.</p>
<p>In a game it is important to know the state of the keyboard at any given time. Since Silverlight currently doesn't tell me if a key is being pressed I use this system to allow me to detect a held key as well as when keys are pressed and released. If you're doing something similar then you will probably use something similar to this.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color:#0000ff;">private</span> <span style="color:#0000ff;">void</span> HandleKey(Key key, <span style="color:#0000ff;">bool</span> isDown)
{
    <span style="color:#0000ff;">switch</span> (key)
    {
        <span style="color:#0000ff;">case</span> Key.Escape:
            <span style="color:#0000ff;">if</span> (isDown) EndGame(Enums.EndGameType.Quit);
            <span style="color:#0000ff;">break</span>;
        <span style="color:#0000ff;">case</span> Key.Up:
        <span style="color:#0000ff;">case</span> Key.W:
            _upIsPressed = isDown;
            <span style="color:#0000ff;">break</span>;
        <span style="color:#0000ff;">case</span> Key.Down:
        <span style="color:#0000ff;">case</span> Key.S:
            _downIsPressed = isDown;
            <span style="color:#0000ff;">break</span>;
        <span style="color:#0000ff;">case</span> Key.Left:
        <span style="color:#0000ff;">case</span> Key.A:
            _leftIsPressed = isDown;
            <span style="color:#0000ff;">break</span>;
        <span style="color:#0000ff;">case</span> Key.Right:
        <span style="color:#0000ff;">case</span> Key.D:
            _rightIsPressed = isDown;
            <span style="color:#0000ff;">break</span>;
        <span style="color:#0000ff;">default</span>:
            <span style="color:#0000ff;">break</span>;
    }
}</pre>
</div>
<p>By knowing the state of the keyboard at any given time, I can allow <a href="http://aspadvice.com/blogs/name/archive/2008/04/24/Creating-a-Game-Loop-Using-Silverlight.aspx" target="_blank">my silverlight game loop</a> to know what keys are currently being pressed and respond to them. This allows the game to play along as the user uses keyboard input to interact with the game. These same ideas and code can be modified easily to work with nearly anything. This is why I make sure that the code snippets I show are quite simple. It makes them more easily adapted to a variety of solutions.</p>
<p>I hope everyone is enjoying Silverlight. Make sure you listen to the <a href="http://weblogs.asp.net/dwahlin/archive/2008/04/27/silverlight-the-song.aspx" target="_blank">Silverlight Song</a>. It is a riot.</p>
