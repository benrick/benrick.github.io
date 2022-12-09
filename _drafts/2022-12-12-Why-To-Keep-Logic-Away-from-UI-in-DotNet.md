---
layout: post
title: "Why to Keep Logic Away from the UI in DotNet"
date: 2022-12-12 00:00:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Programming", "Tips and Tricks", "Advent", "dotnet", ".NET", "C#", "CSharp"]
permalink: "/post/Why-To-Keep-Logic-Away-from-UI-in-DotNet/"
---

## Intro

Hello and welcome! This post is part of the [2022 .NET Advent Calendar](https://dotnet.christmas/) series of posts, but you can enjoy the content without worrying about that!

For this event, I thought I'd make a fun little game for .NET using C#. Now you might be wondering which choice I made for the UI of the application as there are quite a few to choose from in the dotnet ecosystem.

I could have chosen: WPF, UWP, WinForms, or even a Console application. This isn't even considering the 3rd party options and variations on the first party ones!

As the title may have given the game away already, I'm not going to mention which UI we're using yet. Why? I don't need it.

You're likely also wondering which game I chose to make? I decided to make a Minesweeper-style game as I don't even have a copy of it on my Windows PC anymore! A shame!

Shameless self-promoting side note: I did a coding live stream with Guy Royse (after writing this game) on my [DevChatter programming channel on Twitch](https://www.twitch.tv/devchatter/) where we created a simple, static HTML and JavaScript version of Minesweeper from scratch. You can watch the recording of us [Coding Minesweeper in Static HTML with JavaScript](https://youtu.be/9ssOoL_Wj8I) on YouTube.

## What is Minesweeper

If you aren't lucky enough to have played minesweeper when it was one of the few included games on Windows, I'll explain the basic rules of the game.

When it loads, you have a grid of blank squares and an indicator of how many bombs are unmarked on the board.

When you left click a sqaure, it will reveal that square (and possibly others).

- If the square is a bomb, you lose.
- If the square is adjacent to a bomb, it will display a number indicating how many of the 8 squares surrrounding it contain bombs (1-8).
- Otherwise, the square is blank, and the game will automatically reveal all contiguous blank spaces and the numbered spaces next to them.

When you right click a square, it will mark that space with a flag. This is mostly to remind you that you think a bomb is there. You can remove it by right clicking it again. These are also not required to use in order to win the game.

To win the game, you need only reveal the spaces that are not bombs, and the game will automatically mark the remaining spaces as bombs.

## Initial Game Object

One of basic rules with dotnet is to create types when I want them and to get names that are "good enough for now". Refactoring is the name of the game, because we have tools like Visual Studio, Rider, etc. that are quite good at handling renames.

Following that logic, I created a class to handle interactions with the game called... `Game`. I gave that game class a field containing a multidimensional array of integers positives are a bomb hint, 0 is no adjacent bombs, and negatives indicate a bomb is in the space.

Why did I start so simple? Easy, I may not have needed a `Cell` or a `Grid` class to implement a basic version of the game! I recommend people always stat simple like this, as it's easy to add complexity when it's needed, but harder to remove complexity.

My initial game looked a bit like this:

{% highlight csharp %}
Code sample
{% endhighlight %}

Notice that I'm able to create the grid with some basic values without too much trouble. I randomly placed some bombs and mark the hint values. Efficient? Fancy? Nope. Nope. But it works!

With this little bit of code, I was able to get a basic test that the board could get created. What was my initial UI? Console Application. Why? I could easily print out the contents of that array to see if the board looked like I expected. Yeah, the test confirmed that it created positive and negative numbers in a 2 dimensional array, but that's not much gameplay tested yet.

## Revealing Spaces



## Outro

Thanks for participating in this year's .NET Advent Calendar! I hope you enjoy the next couple of weeks of these dotnet posts from members of the developer community.

If you don't know me, my name is Brendan Enrick, and I'm a regular speaker at conferences and user groups. I host a live coding streams and create coding videos on my [DevChatter Twitch](https://www.twitch.tv/DevChatter) and [DevChatter YouTube](https://www.YouTube.com/c/DevChatter) channels. You can also follow me as [@Brendoneus](https://twitter.com/brendoneus) on Twitter or [@Brendoneus@Our.DevChatter.com](https://our.devchatter.com/@Brendoneus) on Mastodon.

Lastly, and most importantly, I want to be sure to thank the organizers and other authors of the [.NET Advent Calendar](https://dotnet.christmas/) for making this an awesome bit of fun for everyone!
