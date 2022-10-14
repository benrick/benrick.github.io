---
layout: post
title: "When to Not Use && and Use and in C# instead - Pattern Combinators"
date: 2022-10-14 01:00:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["CSharp", "Tips and Tricks", "YouTube Video"]
permalink: "/post/Pattern-Combinators-in-CSharp/"
---

When I first started programming, one things I found frustrating was that the conditional operators required that I follow the pattern specifying multiple comparisons of the same variable in their entirety. For example, I might have written code like this:

{% highlight csharp %}
if (age < 45 && age > 25)
{
    // Code here
}
else if (age <= 25 || age >= 45)
{
    // Code here
}
{% endhighlight %}

And that code works fine, but I always wanted to write it like this:

{% highlight csharp %}
// NOT VALID C#
if (age < 45 && > 25)
{
    // NOT VALID C#
}
else if (age <= 25 || >= 45)
{
    // NOT VALID C#
}
{% endhighlight %}

I didn't understand why I had to repeat the variable for each condition.

## Using Pattern Combinators in C\#

Starting with C# 9 in .NET 5, we've been able to leverage pattern matching to allow us to write code the way I was always trying to. With this version, pattern combinators were added to allow us to combine multiple conditions. We can use `not`, `and`, and `or` in our conditionals (they execute in that order).

{% highlight csharp %}
if (age < 45 and > 25)
{
    // Code here
}
else if (age <= 25 or >= 45)
{
    // Code here
}
{% endhighlight %}

## Short Video Showing Pattern Combinators in C\#

I made this short video about these as well.

<div class="video-container">
    <iframe src="https://www.youtube.com/embed/grQ98qjbl4Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
