---
layout: post
title: "Validating Entity objects"
date: 2009-01-21 14:22:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["Validation"]
permalink: "/post/Validating-Entity-objects/"
---

<p>While working with an entity object I wanted to validate, I took some time to do some Googling. I was planning on creating an IValidator&lt;T&gt; interface so I could keep the validation separate from my classes, and I was going to implement this interface for every entity that needed it. Since validation is pretty common I figured I would take a look around first to see if there were some good ways of performing validation which differed slightly from how I had done things previously or offered any insight on a good solution similar to what I mention above. I found a link to a blog post that had exactly what I was looking for. It turns out that <a href="http://www.lostechies.com/blogs/jimmy_bogard/default.aspx">Jimmy Bogard</a> already had a great post on this topic. His post, <a href="http://www.lostechies.com/blogs/jimmy_bogard/archive/2007/10/24/entity-validation-with-visitors-and-extension-methods.aspx">Entity validation with visitors and extension methods</a>, demonstrates a very cool IValidator implementation.</p>
<p>He combines a couple of cool interfaces to get this working. He uses an IValidator&lt;T&gt; interface like I mentioned I wanted to use. His implementation of this is pretty nice. (I made a slight adjustment to it here, because his example code had a bug.)</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> OrderPersistenceValidator : IValidator&lt;Order&gt;
{
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">bool</span> IsValid(Order entity)
    {
        <span style="color: #0000ff">return</span> BrokenRules(entity).Count() == 0;
    }

    <span style="color: #0000ff">public</span> IEnumerable&lt;<span style="color: #0000ff">string</span>&gt; BrokenRules(Order entity)
    {
        <span style="color: #0000ff">if</span> (entity.Id &lt; 0)
            <span style="color: #0000ff">yield</span> <span style="color: #0000ff">return</span> <span style="color: #006080">"Id cannot be less than 0."</span>;

        <span style="color: #0000ff">if</span> (<span style="color: #0000ff">string</span>.IsNullOrEmpty(entity.Customer))
            <span style="color: #0000ff">yield</span> <span style="color: #0000ff">return</span> <span style="color: #006080">"Must include a customer."</span>;

        <span style="color: #0000ff">yield</span> <span style="color: #0000ff">break</span>;
    }
}
</pre>
</div>
<p>&nbsp;</p>
<p>I look at this an see a fairly nice and elegant solution to the validation problem. He also has an IValidatable&lt;T&gt; interface he uses, which is nice because it sets up a method to pass in the IValidator to use.</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> Order : IValidatable&lt;Order&gt;
{
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">int</span> Id { get; set; }
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">string</span> Customer { get; set; }

    <span style="color: #0000ff">public</span> <span style="color: #0000ff">bool</span> Validate(IValidator&lt;Order&gt; validator, <span style="color: #0000ff">out</span> IEnumerable&lt;<span style="color: #0000ff">string</span>&gt; brokenRules)
    {
        brokenRules = validator.BrokenRules(<span style="color: #0000ff">this</span>);
        <span style="color: #0000ff">return</span> validator.IsValid(<span style="color: #0000ff">this</span>);
    }
}
</pre>
</div>
<p>So I think this code is pretty cool, but the only thing that was still irking me about this code is that now I would have to pass the IValidator object in to the Validate method of the entity. I really don't want to have to pass those in, so I start thinking about how to get around that problem. Well then I just read a little further in his article. He has a very nice solution to this problem using an extension method on a Validator class. (I adjusted this snippet slightly also, because it too had a bug.)</p>
<div>
<pre style="font-size: 8pt; margin: 0em; overflow: visible; width: 100%; color: black; line-height: 12pt; font-family: consolas, 'Courier New', courier, monospace; background-color: #f4f4f4; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">class</span> Validator
{
    <span style="color: #0000ff">private</span> <span style="color: #0000ff">static</span> Dictionary&lt;Type, <span style="color: #0000ff">object</span>&gt; _validators = <span style="color: #0000ff">new</span> Dictionary&lt;Type, <span style="color: #0000ff">object</span>&gt;();

    <span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">void</span> RegisterValidatorFor&lt;T&gt;(T entity, IValidator&lt;T&gt; validator)
        <span style="color: #0000ff">where</span> T : IValidatable&lt;T&gt;
    {
        _validators.Add(entity.GetType(), validator);
    }

    <span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> IValidator&lt;T&gt; GetValidatorFor&lt;T&gt;(T entity)
        <span style="color: #0000ff">where</span> T : IValidatable&lt;T&gt;
    {
        <span style="color: #0000ff">return</span> _validators[entity.GetType()] <span style="color: #0000ff">as</span> IValidator&lt;T&gt;;
    }

    <span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">bool</span> Validate&lt;T&gt;(<span style="color: #0000ff">this</span> T entity, <span style="color: #0000ff">out</span> IEnumerable&lt;<span style="color: #0000ff">string</span>&gt; brokenRules)
        <span style="color: #0000ff">where</span> T : IValidatable&lt;T&gt;
    {
        IValidator&lt;T&gt; validator = Validator.GetValidatorFor(entity);

        <span style="color: #0000ff">return</span> entity.Validate(validator, <span style="color: #0000ff">out</span> brokenRules);
    }
}
</pre>
</div>
<p>&nbsp;</p>
<p>This Validator class reminds me a lot of IOC stuff. You register a validator with the entity type it validates. This lets you set up which validators each class needs so you don't have to specify on use. It also provides a nice extension method which allows you to call the validate method without having to pass in the correct validator. It will use the one it has registered for that entity type.</p>
<p>Great solution in my opinion. Now I am going to add his blog to the blogs I read. I hope some of you do also.</p>
