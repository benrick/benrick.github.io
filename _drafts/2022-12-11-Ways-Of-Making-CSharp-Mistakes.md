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

Whether you celebrate Christmas or are just enjoying the C# content from the C# Advent event, all of us can acknowledge these things that will get you on your team's naughty list.

## Abusing for Loop Expressions

Something.

## Tuple Construction and Deconstruction as Constructor Assignment

Something

## Overusing Var

Something

## Working With Disposables Without a Using Statement

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
