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

Notice that we can't see the types without putting a cursor on the type. At-a-glance, it's not clear what that type is.

## Working With Disposable Types Without a Using Statement

In the C# world, we work with "disposable" types all the time. When we say that, we usually mean that the type implements the IDisposable interface. There's even a language feature called using statements that was built for these. When you create your variable in one, it is supposed to dispose when you reach the ending curly brace.

{% highlight csharp %}
using (StreamWriter streamWriter = new StreamWriter(filePath, true))
{
    streamWriter.WriteLine("Brendan Enrick");
    streamWriter.WriteLine("C# Advent");
    streamWriter.WriteLine("2022-12-11");
}
{% endhighlight %}

If you want to upset your team, stop using the using statements. Ignore what's special about disposable types. *What could go wrong?*

Well, a lot can go wrong. When a type implements IDisposable, it's so that it can be cleaned up correctly. These are for types that have resources that need to be cleaned up before the type is disposed of. Often these are network connections, file system connections, etc. that we don't want to leave open. If we don't dispose of them correctly, these get left open.

{% highlight csharp %}
// Normal way - GOOD
using (SqlConnection connection = new (connectionString))
{
    SqlCommand command = new (query, connection);
    connection.Open();
    using(SqlDataReader reader = command.ExecuteReader())
    {
        while (reader.Read())
        {
            // Use reader here.
        }
    }
}

// Skipping those Disposables - BAD
SqlConnection connection = new (connectionString)
SqlCommand command = new (query, connection);
connection.Open();
SqlDataReader reader = command.ExecuteReader()
while (reader.Read())
{
    // Use reader here.
}
// GAHHH!!
{% endhighlight %}

And if you're thinking that it's nice to not be so nested, please don't use that as an excuse. The language no longer requires {} and nesting with a using statement. It will dispose at the end of the current context.

{% highlight csharp %}
using (StreamWriter streamWriter = new StreamWriter(filePath, true));
streamWriter.WriteLine("Brendan Enrick");
streamWriter.WriteLine("C# Advent");
streamWriter.WriteLine("2022-12-11");
{% endhighlight %}

So only skip the using statements if you're **trying** to write bad code.

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

### Acceptable Single Letter Variables

You'll often find that classic "i" as the variable in a basic for loop. If you're not *using* the i itself, but it's just the number of times you looped, this can be OK.

{% highlight csharp %}
for (int i = 0; i < greetingCount; i++)
{
    Console.WriteLine(greetingMessage);
}
{% endhighlight %}

Also, for a lambda selector where the collection name makes the `x` obvious, it *can* be OK. Once you start chaining, LINQ extensions, you're no longer OK.

{% highlight csharp %}
// This is an OK alternative
int maxTemperature = dailyForecasts.Max(x => x.Temperature);

// to this
int maxTemperature = dailyForecasts.Max(forecast => forecast.Temperature);
{% endhighlight %}

### Unacceptable Single Letter Variables

Pretty much, if you're doing anything other than what's listed above, you've found your way onto the team's naughty list. When you start chaining LINQ extensions in your code, the data will often change from the initial type that started the chain. Unlike a fluent API, where the return value is often the same type that all the methods extend, these will return new and different objects. As a result, the types of those object matter!

Here's a not-too-complex example that shows that even in the simpler cases, it could be nicer to have variable names.

{% highlight csharp %}
var maxTemperatures =
    allTemperatures
    .GroupBy(x => x.DayOfWeek)
    .Select(y => new { DayOfWeek = y.Key, HighTemp = y.Max(z => z.Temperature) })
    .OrderyBy(o => o.HighTemp)
    .ToList();
{% endhighlight %}

Notice `x`, `y`, `z`, and `o` are all different types. Even if I tried using `g` for the group, there's the risk that it might have an alternate interpretation.

## Nesting Null Checks

Want a quick and easy way to make your code harder to read? Nest your conditionals needlessly deep by adding separate checks instead of using `&&` or a quick null conditional or null coalescing operation.

You can end up with code like this:

{% highlight csharp %}
if (building != null)
{
    if (building.Office != null)
    {
        if (building.Office.IsAvailable)
        {
            if (user.CanReserve)
            {
                ReserveOffice(user, building.Office);
            }
        }
    }
}
{% endhighlight %}

When you could have just done this, but you'd miss that sweet pyramid of code.

{% highlight csharp %}
if (building?.Office?.IsAvailable == true && user.CanReserve)
{
    ReserveOffice(user, building.Office);
}
{% endhighlight %}

## Using a One-to-One Interface to Class for a Model

As people learn about Dependency Inversion and mocking, some take this to the extreme, adding an interface to every class regardless of whether there will be multiple implementations or a need to be mocked.

For clarity, I'm not saying you can't have interfaces for models. You might have interfaces for all cached objects, all printable objects, etc. in your codebase. These are likely to have multiple implementations, and there's polymorphic reasons to have these.

The problem is when you get `IStudent` for `Student`, `ITeacher` for `Teacher`, and `ILesson` for `Lesson`. None of those objects likely need a mock for testing, since you could just create instances of those models for testing.

Some useful interfaces might be things like, `ISchoolMember` for `Student`, `Teacher`, and `Administrator`, which requires a `SchoolID` property on these objects.

## Putting Regions Inside Methods

Yes, we saved the worst for last. I won't shame anyone for using a region in their code, however, nearly all uses of them are better replaced by a change t the code.

Plenty of people do use regions, and like being able to define sections of code in those named blocks. A region inside of a method, however, better have a *really* good reason to exist. By labeling that section of code with a region, you're begging for a method to be extracted for that code.

Have you done this? Are you the one?!

### Region Inside a Method

{% highlight csharp %}
public ProcessResult ProcessStatusUpdate(ChangeLog changes)
{
    #region Validate Changes
    if (changes == null)
    {
        throw InvalidChangeLogException(changes);
    }
    if (changes.Actions <= MinimumActions)
    {
        throw InvalidChangeLogException(changes);
    }
    #end region

    #region Print Changes
    Console.WriteLine(changes.Title);
    Console.WriteLine(changes.SubTitle);
    foreach(var changeAction in changes.Actions)
    {
        Console.WriteLine(changeAction.Message);
    }
    #endregion

    // More code here
}
{% endhighlight %}

### Extracted Method Instead of Region

Instead of the regions, we could've just created methods for those named parts of the code.

{% highlight csharp %}
public ProcessResult ProcessStatusUpdate(ChangeLog changes)
{
    ValidateChanges(changes);

    PrintChanges(changes);

    // More code here
}

public void ValidateChanges(ChangeLog changes)
{
    if (changes == null)
    {
        throw InvalidChangeLogException(changes);
    }
    if (changes.Actions <= MinimumActions)
    {
        throw InvalidChangeLogException(changes);
    }
}

public void PrintChanges(ChangeLog changes)
{
    Console.WriteLine(changes.Title);
    Console.WriteLine(changes.SubTitle);
    foreach(var changeAction in changes.Actions)
    {
        Console.WriteLine(changeAction.Message);
    }
}
{% endhighlight %}

## Outro

Thanks for participating in this year's C# Advent! I hope you enjoy the next couple of weeks of these C# posts from members of the developer community.

If you don't know me, my name is Brendan Enrick, and I'm a regular speaker at conferences and user groups. I host a live coding streams and create coding videos on my [DevChatter Twitch](https://www.twitch.tv/DevChatter) and [DevChatter YouTube](https://www.YouTube.com/c/DevChatter) channels. You can also follow me as [@Brendoneus](https://twitter.com/brendoneus) on Twitter or [@Brendoneus@Our.DevChatter.com](https://our.devchatter.com/@Brendoneus) on Mastodon.

Lastly, and most importantly, I want to thank [Matt Groves @mgroves](https://twitter.com/mgroves) for organizing the C# Advent, which has been an awesome way to flood our feeds with great C# content! I'm grateful to have been able to help out and add to the C# fun this year!
