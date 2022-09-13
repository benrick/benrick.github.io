---
layout: post
title: "Static Methods and Interfaces in C#"
date: 2007-12-13 14:39:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Static-Methods-and-Interfaces-in-C"
---
<!-- more -->

<p>Someone just commented on <a href="http://aspalliance.com/1516_Understanding_Interfaces_in_C">my C# interfaces article on ASP Alliance</a> asking an interesting question, and I figure I will respond to it here since I can give a better response here. I don't want to clutter the article comments. Also I can add nifty cool pictures, format all of my text nicely, and write a heck of a lot more here.</p>
<p>This is the excellent question I was asked.</p>
<blockquote>
<p>All my classes implementing my interface should have a static funtion.<br /> Why can't I have a static function in an interface???</p>
<p>-Jan</p>
</blockquote>
<p>This is how I responded in the article.</p>
<blockquote>
<p>One important thing to understand about static methods is that they don't really need to be tied to classes. Static methods basically just exist for convenience. <br /> An interface is as the name says an interface to something. Think of it like an automobile interface. There are defined ways of working with the car. They have a steering wheel a gas pedal and brakes. An interface defines that and all automobiles will have those, but an interface doesn't define anything about "cars in general" (static) it defines what will be the interface for individual cars (instances).</p>
</blockquote>
<p>As I was saying interfaces are used for defining interfaces for code. I like my car analogy, but I think I'll use a sail boat analogy this time.</p>
<p><img src="http://upload.wikimedia.org/wikipedia/commons/6/60/Freiheitu.jpg" alt="" width="183" height="240" align="right" /> Think of writing an interface in C# called <em>ISailable</em>. This objects implementing this interface will be sailboats. So what does every sailboat need to be able to function. For simplicity I'll say that we just need to have sails and a wheel. All sailboats will also need to be able to sail. So now we've defined how our <em>ISailable</em> objects work. We can now create sailboats using this nice interface. Notice we haven't defined how large the sails are or what style of sails. We just said we need sails. We also did not define the wheel. Is it metal or wood? How large is it? We don't care in the interface the classes implementing the interface will each define those differently. Notice that different boats have very different types of sails.</p>
<p>We might define out ISailable interface in the following way. Keep in mind I am using a lot of simplicity here.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">namespace</span> Enrick.Interfaces
{
    <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">interface</span> ISailable
    {
        <span style="color: #0000ff;">void</span> Sail(<span style="color: #0000ff;">string</span> destination);
        <span style="color: #0000ff;">void</span> Steer(<span style="color: #0000ff;">string</span> direction);
        <span style="color: #0000ff;">void</span> RaiseSails();
        <span style="color: #0000ff;">void</span> LowerSails();
    }
}</pre>
</div>
<p>Then once we have that defined we are able to implement the interface and create our first sailable object which will of course be a sailboat.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">namespace</span> Enrick.Boats
{
    <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">class</span> SailBoat : Enrick.Interfaces.ISailable
    {
        <span style="color: #cc6633;">#region</span> ISailable Members

        <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> Sail(<span style="color: #0000ff;">string</span> destination)
        {
            <span style="color: #008000;">// Write sailing logic here. It should be specific to this type of boat.</span>
        }

        <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> Steer(<span style="color: #0000ff;">string</span> direction)
        {
            <span style="color: #008000;">// Write steering logic here for this exact type of boat.</span>
        }

        <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> RaiseSails()
        {
            <span style="color: #008000;">// Write logic to raise these specific sails here.</span>
        }

        <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> LowerSails()
        {
            <span style="color: #008000;">// Write logic to lower these specific sails here.</span>
        }

        <span style="color: #cc6633;">#endregion</span>
    }
}</pre>
</div>
<p><img src="http://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/Cannon_shot_by_Velde.jpg/511px-Cannon_shot_by_Velde.jpg" alt="" width="204" height="240" align="left" /> Static interfaces do not really apply to what we've defined though. We've just been talking about how to interface with individual sail boats. We haven't gotten to static methods really. This is because static methods aren't really necessary. Many languages have them, but they could just as easily be outside of the class and have the same functionality. Static methods are by definition methods which aren't specific to individual instances of classes. This means we could define these methods anywhere and achieve equivalent functionality. They also don't really apply with interfaces and the C# language specification doesn't allow static methods on interfaces because they don't really make sense with interfaces.</p>
<p>There are circumstances where someone might want to have a static method on an interface. Perhaps the static method was going to be a way of performing an action on an entire collection of the instances of the objects. Perhaps you have a fleet of <em>ISailable</em> ships that you will want to sail together. This would make sense to have a static method which would be associated with the class, but it isn't necessary. Instead we will create a static method elsewhere. It will not be tied to our interface. We can have it take a list of ISailable objects and then it can perform the sailing operation of our fleet.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> SailFleet(List&lt;ISailable&gt; fleet, <span style="color: #0000ff;">string</span> direction)
{
    <span style="color: #0000ff;">foreach</span> (ISailable boat <span style="color: #0000ff;">in</span> fleet)
    {
        boat.Sail(direction);
    }
}</pre>
</div>
<p>Notice here that I've defined a method which might have been static before on each of the boats and each one would have take a List of their instances, but that would be silly. This solution allows us to have methods which work with <em>ISailable</em> objects but they need not be defined as requiring an interface. Sadly there is not a way of having static methods on interfaces in C#.</p>
<p>I hope that answers some questions. As always, thanks for reading!</p>
