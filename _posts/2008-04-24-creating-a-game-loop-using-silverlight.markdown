---
layout: post
title: "Creating a Game Loop Using Silverlight"
date: 2008-04-24 15:58:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
alias: ["/post/Creating-a-Game-Loop-Using-Silverlight", "/post/creating-a-game-loop-using-silverlight"]
---
<!-- more -->

<p>I've been playing with silverlight as a gaming platform for a few months now. I've not published or released anything I've done yet, but I expect I will at some point. I am not much of a game developer really, and I've been hacking things together as best I can. I, like many other developers, have always found game development to be quite interesting. So for now I'll talk about how to create a game loop.</p>
<h4>What are Game Loops Used For?</h4>
<p>In most games you need to have some control over the passing of time. You always need to be constantly able to respond to user input without stopping the game waiting for this user interaction. It allows you an opportunity to have the game move with or without the player. This loop will allow you to have computer-controlled enemies and neutrals decide how to act and to take these actions.</p>
<h4>How to Create a Game Loop</h4>
<p>I've found two ways I like for creating game loops. I am sure that there are plenty of others. If you wanted to, you could also wrap these up into classes so it abstracts the ugly details of creating a game loop. Perhaps a class which just lets you create a new instance of the game loop class and lets you assign a method for handling the looping.</p>
<p>Since I am just trying to show the simple how to of it, I'll leave out the class and leave that as an exercise for the reader. The two ways I know of for creating game loops are to use a System.Windows.Threading.DispatchTimer or a System.Windows.Media.Animation.Storyboard. I prefer the timer simply because it feels more <a href="http://en.wikipedia.org/wiki/Hack_%28technology%29" target="_blank">hacky</a> to use a storyboard. This just feels more like it should be some sort of a timer managing this, so it's what I like to use.</p>
<p>&nbsp;</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color:#008000;">// Initialize the Main Game Loop</span><br />
<br />
_timer = <span style="color:#0000ff;">new</span> DispatcherTimer();<br />
<br />
_timer.Interval = <span style="color:#0000ff;">new</span> TimeSpan(100);<br />
<br />
_timer.Tick += <span style="color:#0000ff;">new</span> EventHandler(MainGameLoop);<br />
<br />
_timer.Start();</pre>
</div>
<p>What we've done here is just created this DispatchTimer and told it to run fire the MainGameLoop method every time the timer ticks. The timer has an interval set to 10 miliseconds in this example, so our loop should execute 100 times every second.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color:#0000ff;">private</span> <span style="color:#0000ff;">void</span> MainGameLoop(<span style="color:#0000ff;">object</span> sender, EventArgs e)<br />
<br />
{<br />
<br />
    <span style="color:#008000;">// ....</span><br />
<br />
    <span style="color:#008000;">// Do Stuff Here For the Game</span><br />
<br />
    <span style="color:#008000;">// ....</span><br />
<br />
}</pre>
</div>
<p>Again another exercise for the reader is to create a game by filling in that MainGameLoop as well as other portions of the code. I plan on fleshing out some games if I ever get enough free time to work on it. I'll be back to post some more stuff. I expect it will be more complicated that this. I just don't want to post my whole game yet. It will be released eventually. I am not making <a href="http://en.wikipedia.org/wiki/Duke_Nukem_Forever" target="_blank">Duke Nukem Forever</a>, so you can expect my game will actually release at some point.</p>
