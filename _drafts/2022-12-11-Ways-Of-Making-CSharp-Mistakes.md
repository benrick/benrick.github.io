---
layout: post
title: "11 Ways of Making C# Mistakes"
date: 2022-12-11 00:00:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Programming", "Tips and Tricks", "Advent"]
permalink: "/post/Ways-Of-Making-CSharp-Mistakes/"
---

Programming is hard. Most of us work in teams, building software that other people are going to work with. For that reason, it's important that we try to make things easier for our team. As this post is scheduled for the 11th of December, I figured I'd make a list of 11 ways of writing C# that will make our code harder for our team to work with, earning us a spot on the naughty list.

Here are 11 things you should **NOT** do in your C# code.

## Abusing for Loop Expressions

The "for" loop exists in many languages. It's a useful structure for creating consistent loops, and it's no different in C#. I'm sure you've seen this a million times:

{% highlight csharp %}
for(int i = 0; i < 100; i++)
{
    Console.WriteLine(i);
}
{% endhighlight %}

### Understanding the For Loop

Doing that is OK, but what might upset some people is if you start getting too creative with your loops. Let's jump back and explain the structure of the for loop, so we can discuss how someone might abuse it.

{% highlight csharp %}
for (before statement; conditional statement; after each statement)
{
}
{% endhighlight %}

The 3 statements inside of the parentheses have conditions for when they run, but they're just statements like any others you might have in your code. For this reason, you can put whatever you want in them.

### Non-Standard For Loops

Let's start by creating an infinite loop by leaving each of the 3 statements blank.

{% highlight csharp %}
// Instead of this:
while (true) {}
// You could write this:
for (; ;) {}
{% endhighlight %}

That's not really useful though. We could also try leaving out the increment step by just incrementing in the conditional.

{% highlight csharp %}
for(int i = 0; ++i < 100;)
{
    Console.WriteLine(i);
}
{% endhighlight %}

Yes, I switched from a post increment to a pre-increment to keep the usual structure, but we're able to skip that third statement now!

Let's get serious by using strings in a for loop instead of numbers. Let's slowly remove letters from a string as part of a for loop.

{% highlight csharp %}
for (string name = "Brendan"; name.Length > 0; name = name.Substring(1))
{
  Console.WriteLine(name);
}
{% endhighlight %}

OK, but what if we want to get really crazy. Let's create multiple variables and use them in the loop! We *can* as long as we use tuple construction and deconstruction! **Not Subtle Foreshadowing**

{% highlight csharp %}
for (var (number, name) = (1, "Brendan"); number < 7; name += number.ToString(), number += 1) {
    Console.WriteLine(name);
}
{% endhighlight %}

## Tuple Construction and Deconstruction as Constructor Assignment

As we just saw, you can construct and deconstruct tuples in the same line. Awesome! Now to upset the rest of our time, because we can put our entire constructor in **one line** now!

{% highlight csharp %}
public Person(string prefix, string first, string middle, string last, string suffix, string nickname, DateTime birthday, string favoriteColor)
{
    (Prefix, First, Middle, Last, Suffix, Nickname, Birthday, FavoriteColor) = (prefix, first, middle, last, nickname, suffix, birthday, favoriteColor);
}
{% endhighlight %}

Now there's nothing wrong with doing this for a couple related values, but if you start writing the whole thing this way, it gets a lot harder for people to see what's going on. These are also assigned in order, so it would be very easy for me to have these mixed up. Did you notice? It is messed up. Look again!

Yep, nickname and suffix get flipped in this constructor, but it's hard to notice in that mess!

## Overusing Var

With all of the complex types we can get by using linq in C#, var was necessary. In fact, it's an awesome addition to the language to not have to specify the type of variable, since the compiler knows the type already.

Let's start by talking about why `var` is good and useful in C# coding. Hint: it's not useful for just avoiding writing types in C# code. It's useful when the type is more complicated than is needed. Exhibit A, the GroupBy.

{% highlight csharp %}

    FILL IN EXAMPLE POSSIBLE OF EVENTS GROUPED BY YEAR THEN BY COUNTRY

{% endhighlight %}

It's for complicated types like these that `var` became necessary. In fact, nearly everywhere that a GroupBy result is stored in a variable, you're likely to see `var` in the code.

Now, dear reader, you're likely wondering why we wouldn't just use this *everywhere*. That's because knowing the type of a variable can be useful to us as programmers. When you use `var`, you've hidden the information. We no longer know the type. If the type was somewhere else on the line, that's probably ok, but if it's not there, it better be super clear what the type is.

{% highlight csharp %}

    FILL IN EXAMPLE OF AMBIGUOUS TYPES HIDDEN BY VAR USAGE

{% endhighlight %}

## Working With Disposable Types Without a Using Statement

Something

## Throwing Exceptions Instead of Returning

Something

## Committing Code which Adds Warnings to the Build

Something

## Using Unclear Abbreviations for Variable Names

When naming a variable, it's far more important for a reader to know what the variables purpose is. For this reason, we need to avoid ambiguity, which can arise from abbreviations. Even if those abbreviations are common in your codebase, you could have a collision you haven't thought of yet. Adding a bit of clarity now can save you and your team a headache later! It also makes your codebase easier for new people to join if they don't have to learn a list of abbreviations just to get started.

### Unclear Variable Names

{% highlight csharp %}
var st = new SimpleTransfer();
var st = new ServiceTime();
var st = new SecretTunnel();
{% endhighlight %}

### Clear Variable Names

{% highlight csharp %}
var simpleTransfer = new SimpleTransfer();
var serviceTime = new ServiceTime();
var secretTunnel = new SecretTunnel(); // Through the mountain!
{% endhighlight %}

**Note:** For this example, assume these were in different scopes, so the compiler would allow it, but seeing `st` in the code wouldn't tell you which `st` *this* was!

## Using Single Letter Variables

There are only two places where a single letter variable can be OK. Even then, it might be better to use a full variable name.

basic for loop and lambda selector where the collection name makes the `x` obvious.

## Nesting Null Checks

Nesting null checks that could be one with an `&&` or just use a null conditional or null coalescing.

## Using a One-to-One Interface to Class for a Model

As people learn about Dependency Inversion and mocking, some take this to the extreme, adding an interface to every class regardless of whether there will be multiple implementations or a need to be mocked.

For clarity, I'm not saying you can't have interfaces for models. You might have interfaces for all cached objects, all printable objects, etc. in your codebase. These are likely to have multiple implementations, and there's polymorphic reasons to have these.

The problem is when you get `IStudent` for `Student`, `ITeacher` for `Teacher`, and `ILesson` for `Lesson`. None of those objects likely need a mock for testing, since you could just create instances of those models for testing.

Some useful interfaces might be things like, `ISchoolMember` for `Student`, `Teacher`, and `Administrator`, which provides a `SchoolID`.

## Putting Regions Inside Methods

Yes, we saved the worst for last. I won't shame people for using C# in code. Plenty of people use them, but a region inside of a method is begging to be extracted into a method of its own. Have you done this?

### Region Inside a Method

{% highlight csharp %}
// Bad Code
{% endhighlight %}

### Extracted Method Instead of Region

{% highlight csharp %}
// Good Code
{% endhighlight %}

## Outro

Thanks for participating in this year's C# Advent! I hope you enjoy the next couple of weeks of these C# posts from members of the developer community.

If you don't know me, my name is Brendan Enrick, and I'm a regular speaker at conferences and user groups. I host a live coding streams and create coding videos on my [DevChatter Twitch](https://www.twitch.tv/DevChatter) and [DevChatter YouTube](https://www.YouTube.com/c/DevChatter) channels. You can also follow me as [@Brendoneus](https://twitter.com/brendoneus) on Twitter or [@Brendoneus@Our.DevChatter.com](https://our.devchatter.com/@Brendoneus) on Mastodon.

Lastly, and most importantly, I want to thank [Matt Groves @mgroves](https://twitter.com/mgroves) for organizing the C# Advent, which has been an awesome way to flood our feeds with great C# content! I'm grateful to have been able to help out and add to the C# fun this year!
