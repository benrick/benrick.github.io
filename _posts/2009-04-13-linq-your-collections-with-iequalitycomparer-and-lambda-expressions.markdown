---
layout: post
title: "LINQ Your Collections with IEqualityComparer and Lambda Expressions"
date: 2009-04-13 13:50:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/LINQ-Your-Collections-with-IEqualityComparer-and-Lambda-Expressions", "/post/linq-your-collections-with-iequalitycomparer-and-lambda-expressions"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>Anyone using LINQ to manipulate in-memory collections is probably also using plenty of lambda expressions to make things quite easy. These two additions were really meant for each other. One of our interns here recently ran into an interesting problem while using LINQ. As a relatively new user of .NET based languages, reference types caused him a bit of trouble.</p>
<h4>The problem</h4>
<p>While using the dot notation with lambda expressions, he was using the Except method in the following way.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;">List&lt;MyObject&gt; x = myCollection.Except(otherCollection).ToList();</pre>
</div>
<p>Well the problem here is that these two collections contain "MyObject"s, and when it does the comparison it does so based on the reference. This means if those are separate but equivalent objects that the comparison will claim they are different.</p>
<p>He had unit tests making sure that the except statement worked, but was using the same instance of variables to <em>Assert</em>, so the tests claimed to work.</p>
<p>I told him the problem and mentioned that there was probably an overload of Except that allows one to specify how to do the comparison. I was correct, but the overload takes an IEqualityComparer object. I was hoping for a Func&lt;x,x,bool&gt; as the second parameter, so I did what I always do; I Googled to see if anyone knew an easy way to get that to work without doing extra work.</p>
<p>The Internet was kind enough to inform me that there was no built in way of handling this situation.</p>
<p>Building your own was the suggestion. It is a pretty simple class, so it can just be tossed somewhere to be reused easily. It could easily come up and be needed again.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">class</span> LambdaComparer&lt;T&gt; : IEqualityComparer&lt;T&gt;
{
    <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">readonly</span> Func&lt;T, T, <span style="color: #0000ff;">bool</span>&gt; _lambdaComparer;
    <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">readonly</span> Func&lt;T, <span style="color: #0000ff;">int</span>&gt; _lambdaHash;

    <span style="color: #0000ff;">public</span> LambdaComparer(Func&lt;T, T, <span style="color: #0000ff;">bool</span>&gt; lambdaComparer) :
        <span style="color: #0000ff;">this</span>(lambdaComparer, o =&gt; 0)
    {
    }
    
    <span style="color: #0000ff;">public</span> LambdaComparer(Func&lt;T, T, <span style="color: #0000ff;">bool</span>&gt; lambdaComparer, Func&lt;T, <span style="color: #0000ff;">int</span>&gt; lambdaHash)
    {
        <span style="color: #0000ff;">if</span> (lambdaComparer == <span style="color: #0000ff;">null</span>)
            <span style="color: #0000ff;">throw</span> <span style="color: #0000ff;">new</span> ArgumentNullException(<span style="color: #006080;">"lambdaComparer"</span>);
        <span style="color: #0000ff;">if</span> (lambdaHash == <span style="color: #0000ff;">null</span>)
            <span style="color: #0000ff;">throw</span> <span style="color: #0000ff;">new</span> ArgumentNullException(<span style="color: #006080;">"lambdaHash"</span>);

        _lambdaComparer = lambdaComparer;
        _lambdaHash = lambdaHash;
    }

    <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">bool</span> Equals(T x, T y)
    {
        <span style="color: #0000ff;">return</span> _lambdaComparer(x, y);
    }

    <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">int</span> GetHashCode(T obj)
    {
        <span style="color: #0000ff;">return</span> _lambdaHash(obj);
    }
}</pre>
</div>
<p>Now that we have a nice, Generic, comparer which can take lambda expressions, we are all set to plug this in to the previous code.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;">List&lt;MyObject&gt; x = myCollection.Except(otherCollection, 
  <span style="color: #0000ff;">new</span> LambdaComparer&lt;MyObject&gt;((x, y) =&gt; x.Id == y.Id)).ToList();

<span style="color: #008000;">// or</span>

IEqualityComparer comparer = <span style="color: #0000ff;">new</span> LambdaComparer&lt;MyObject&gt;((x, y) =&gt; x.Id == y.Id);
List&lt;MyObject&gt; x = myCollection.Except(otherCollection, comparer).ToList();</pre>
</div>
<p>I admit I am still kind of annoyed that there wasn't an overload which just took a <em>Func&lt;T, T, bool&gt;</em> or a <em>Func&lt;T, T, int&gt;</em>.</p>
<p>Either way, I hope this helps someone use LINQ a little more easily. I know of some alternate ways of solving this same problem. So if you think I should have solved this differently then blog it and link back here or just post a comment below.</p>
<p><strong>Update 16 April 2009 - From a comment below</strong></p>
<p>One commenter below posted a suggested extension method for use with this. He suggests using this nice extension method so you can hide away the fact that you're using the custom comparer class.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">class</span> Ext
{
    <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">static</span> IEnumerable&lt;TSource&gt; Except&lt;TSource&gt;(<span style="color: #0000ff;">this</span> IEnumerable&lt;TSource&gt; first, 
        IEnumerable&lt;TSource&gt; second , Func&lt;TSource, TSource, <span style="color: #0000ff;">bool</span>&gt; comparer )
    {
        <span style="color: #0000ff;">return</span> first.Except(second, <span style="color: #0000ff;">new</span> LambdaComparer&lt;TSource&gt;(comparer));
    }
}</pre>
</div>
<p>Thank you for the comment. I like the idea. It will very nicely hide away the fact that a silly comparer is needed.</p>
