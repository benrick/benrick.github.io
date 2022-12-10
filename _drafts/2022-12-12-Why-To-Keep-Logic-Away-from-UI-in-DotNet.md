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

Hello and welcome! This post is part of the [2022 .NET Advent Calendar](https://dotnet.christmas/) series of posts, but you can enjoy the content without worrying about that!

For this event, I thought I'd build a program that can show why you don't want to have any logic in your controllers, pages, views, forms, etc. in your .NET application. I also figured we'd make it a fun little game.

## Picking an Application Front-End

Now you might be wondering which choice I made for the UI of the application, since I mentioned a few types of front-ends and there are quite a few to choose from in each of those I mentioned above.

I could have chosen: WPF, UWP, WinForms, or even a Console application. This isn't even considering the 3rd party options and variations on the first party ones!

As the title may have given the game away already, I'm not going to mention which UI we're using yet. Why? I don't need to! We can build the game and decide the UI later!

You're likely also wondering which game I chose to make? I decided to make a Minesweeper-style game as I don't even have a copy of it on my Windows PC anymore! A shame!

Shameless self-promoting side note: I did a coding live stream with Guy Royse (after writing this game) on my [DevChatter programming channel on Twitch](https://www.twitch.tv/devchatter/) where we created a simple, static HTML and JavaScript version of Minesweeper from scratch. You can watch the recording of us [Coding Minesweeper in Static HTML with JavaScript](https://youtu.be/9ssOoL_Wj8I) on YouTube.

## What is Minesweeper?

If you aren't lucky enough to have played minesweeper when it was one of the few included games on Windows, I'll explain the basic rules of the game.

When it loads, you have a grid of blank squares and an indicator of how many bombs are unmarked on the board.

When you left click a square, it will reveal that square (and possibly others).

- If the square is a bomb, you lose.
- If the square is adjacent to a bomb, it will display a number indicating how many of the 8 squares surrounding it contain bombs (1-8).
- Otherwise, the square is blank, and the game will automatically reveal all contiguous blank spaces and the numbered spaces next to them.

When you right click a square, it will mark that space with a flag. This is mostly to remind you that you think a bomb is there. You can remove it by right clicking it again. These are also not required to use in order to win the game.

To win the game, you need only reveal the spaces that are not bombs, and the game will automatically mark the remaining spaces as bombs.

## Initial Game Object

One of basic rules with dotnet is to create types when I want them and to get names that are "good enough for now". Refactoring is the name of the game, because we have tools like Visual Studio, Rider, etc. that are quite good at handling renames.

Following that logic, I created a class to handle interactions with the game called... `Game`. I gave that game class a field containing a multidimensional array of integers positives are a bomb hint, 0 is no adjacent bombs, and negatives indicate a bomb is in the space.

Why did I start so simple? Easy, I may not have needed a `Cell` or a `Grid` class to implement a basic version of the game! I recommend people always stat simple like this, as it's easy to add complexity when it's needed, but harder to remove complexity.

My initial game looked a bit like this:

{% highlight csharp %}
public class Game
{
    private readonly int _size;
    public readonly int[,] Grid { get; }

    public void Start(int size)
    {
        Grid = new int[size, size];
        FillWithBombs(0.1);
    }

    private void FillWithBombs(double bombPercent)
    {
        // Get bombs as a percent of all spaces
        int bombCount = (int)(Grid.Length * bombPercent);
        // Get an array of indexes as if the grid were one array.
        var possibles = Enumerable.Range(0, Grid.Length).ToArray();
        // Pick a random selection of those indexes to receive bombs.
        var locations = possibles.OrderBy(x => _random.Next()).Take(bombCount);

        foreach (var index in locations)
        {
            _grid[index % _size, index / _size] = _random.Next(-5, 0);
        }
    }
}
{% endhighlight %}

Notice that I'm able to create the grid with some basic values without too much trouble. I randomly placed some bombs and mark the hint values. Efficient? Fancy? Nope. Nope. But it works!

With this little bit of code, I was able to get a basic test that the board could get created. What was my initial UI? Console Application. Why? I could easily print out the contents of that array to see if the board looked like I expected. Yeah, the test confirmed that it created positive and negative numbers in a 2 dimensional array, but that's not much gameplay tested yet.

## Hiding and Revealing Spaces

Before we can play this game, we'll need to hide the spaces, so we can reveal them when the player picks them later. Displaying everything was great for confirming that the application was creating the grid as we expected it.

Since we need to keep track of whether a space has been revealed or not, we either need two grids of data, one with the status and one for the value, or we could upgrade our grid to have an object that knows its value and the revealed state.

To start with, I created a `Cell` class and gave it properties for the `Count` of neighboring bombs and a `Revealed` boolean value to know when it should be displayed.

{% highlight csharp %}
Code sample
{% endhighlight %}

Now in order to make it an easier refactoring, I can add some implicit operator methods to the type, so our number operations on it will modify the `Count` property. That looks like this:

{% highlight csharp %}
Code sample
{% endhighlight %}

The code where I did this will work on the cells the same way it did when these were numbers:

{% highlight csharp %}
Code sample
{% endhighlight %}

## Handling Game Over

Minesweeper wouldn't be much fun if we don't lose by clicking a bomb, so let's make sure that this causes an end game. To solve this, we have a few options. We could send a message then reset the game, or we could wait until the user starts a new game and change our "state" to be "Game Over".

I like the idea of remaining in the "game over" state, so that the player can see the grid and their mistake that lost the game. That means we need to store that somewhere. We could use booleans for things like `IsStarted`, `IsWon`, `IsLost`, etc. to know the state. I think we're only ever going to be in one state at a time, so an enum for this might be the simpler solution. Let's create a `GameState` enum to handle this.

{% highlight csharp %}
Code sample - show GameState enum
{% endhighlight %}

Now we can adjust the reveal method to trigger a `GameOver` state if we reveal a bomb while we're in the `GamePlaying` state. We can also restrict the player selecting to reveal a space, so that it only happens if we're in the `GamePlaying` state.

{% highlight csharp %}
Code sample - Guard the Reveal method to require GameState.GamePlayer
{% endhighlight %}

## Handling Winning the Game

We can lose the game, but I think we'd all rather win. It's time to add in the condition to allow a player to win! As we mentioned, that happens when the player has revealed every non-bomb space and not revealing any bomb spaces.

As we already created the `GameWon` value on the `GameState` enum, we can use it now to indicate that the player has won the game.

Thankfully, we already locked the revealing of spaces to require that it be in the `GamePlaying` state, which means that we won't have to worry about accidentally clicking a bomb space after we've revealed all of the other spaces.

{% highlight csharp %}
Code sample - Triggering game won after all spaces revealed.
{% endhighlight %}

## Playing the Game without a UI

Now I'll reveal the secret that I was able to run these tests before writing most of the code. My tests just needed to call methods on the `Game` object, because I could automate playing the game without a UI at all. I can do this, because I kept all of the logic out of the UI.

{% highlight csharp %}
Code sample - Functional Testing of a win and a loss on a 3x3 map with 3 bombs.
{% endhighlight %}

If I'd tied code into the UI, I'd have to spin up controllers, views or other context objects, which I'd rather not do in tests. I also haven't tied myself to MVVM, MVC, MVP, etc. either. We can easily add those as wrappers, or directly put the concept on these classes.

## Optional Homework

I built only the UI for the Console Application and the (FILL ME IN). If you want to try it, I've put the [Minesweeper in C#](https://github.com/DevChatter/elf-sweeper) code on GitHub with a few empty projects that you could wire up a UI for and make buttons to reveal spaces and play the game.

## Outro

One of my favorite things to do while programming in any language is to try to keep the application code away from the UI, because it gives us so much power of it when it's just in a referenced class library.

Thanks for participating in this year's .NET Advent Calendar! I hope you enjoy the next couple of weeks of these dotnet posts from members of the developer community.

If you don't know me, my name is Brendan Enrick, and I'm a regular speaker at conferences and user groups. I host a live coding streams and create coding videos on my [DevChatter Twitch](https://www.twitch.tv/DevChatter) and [DevChatter YouTube](https://www.YouTube.com/c/DevChatter) channels. You can also follow me as [@Brendoneus](https://twitter.com/brendoneus) on Twitter or [@Brendoneus@Our.DevChatter.com](https://our.devchatter.com/@Brendoneus) on Mastodon.

Lastly, and most importantly, I want to be sure to thank the organizers and other authors of the [.NET Advent Calendar](https://dotnet.christmas/) for making this an awesome bit of fun for everyone!
