---
layout: post
title: "Returning From Inside a Using Statement"
date: 2008-11-21 23:59:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Returning-From-Inside-a-Using-Statement/"
---
<!-- more -->



<p>A while back I wrote a blog post regarding this topic. In that post I explain that it is safe to use a <a href="/post/2009/05/06/Return-Within-a-C-Using-Statement.aspx">return statement inside a using block</a>, because the using block will handle the disposing of the defined IDisposable object. This is one truly great ability of the IDisposable interface. It makes it very important to use in my opinion. The using block in combination is very nice, because it handles the disposal for you.</p>
<p>One of my commenter on that post asked me if I was certain that the return statement was safe. He asked this because he couldn't find it in the documents. He also asked me if I had any code showing that this behavior works as I claim it does. I quickly wrote this simple little piece of code which works to demonstrate this behavior.</p>
<p>In my example I have a few things. I have a class which implements IDisposable and all it does to dispose is to write to the console. I then wrote 3 methods which each create and instance of this class in a using statement. One class is normal; it returns after the using statement is complete. The other two end abruptly. One of them returns from within the using statement, and the other throws an exception within the using statement.</p>
<p>&nbsp;</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">class</span> Program
{
    <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Main(<span style="color: #0000ff;">string</span>[] args)
    {
        Console.WriteLine(<span style="color: #006080;">"Application Starting\n"</span>);

        Console.WriteLine(<span style="color: #006080;">"Before normal method"</span>);
        NormalMethod();
        Console.WriteLine(<span style="color: #006080;">"After normal method\n"</span>);
        
        Console.WriteLine(<span style="color: #006080;">"Before return method"</span>);
        ReturnFromMethod();
        Console.WriteLine(<span style="color: #006080;">"After return method\n"</span>);

        Console.WriteLine(<span style="color: #006080;">"Before Throw method"</span>);
        <span style="color: #0000ff;">try</span>
        {
            ThrowFromMethod();
        }
        <span style="color: #0000ff;">catch</span> (Exception ex)
        {
            Console.WriteLine(<span style="color: #006080;">"Caught the Exception: "</span> + ex.Message);
        }
        Console.WriteLine(<span style="color: #006080;">"After Throw method\n"</span>);

        Console.WriteLine(<span style="color: #006080;">"Application Ending"</span>);
    }

    <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> NormalMethod()
    {
        <span style="color: #0000ff;">using</span> (MyDisposable myDisposable = <span style="color: #0000ff;">new</span> MyDisposable())
        {
            <span style="color: #008000;">// do nothing</span>
        }
        <span style="color: #0000ff;">return</span>;
    }

    <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> ThrowFromMethod()
    {
        <span style="color: #0000ff;">using</span> (MyDisposable myDisposable = <span style="color: #0000ff;">new</span> MyDisposable())
        {
            <span style="color: #0000ff;">throw</span> <span style="color: #0000ff;">new</span> Exception(<span style="color: #006080;">"This is the exception"</span>);
        }
    }

    <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> ReturnFromMethod()
    {
        <span style="color: #0000ff;">using</span> (MyDisposable myDisposable = <span style="color: #0000ff;">new</span> MyDisposable())
        {
            <span style="color: #0000ff;">return</span>;
        }
        Console.WriteLine(<span style="color: #006080;">"DO NOT WRITE THIS!!!"</span>);
        <span style="color: #0000ff;">return</span>;
    }

    <span style="color: #0000ff;">class</span> MyDisposable : IDisposable
    {
        <span style="color: #cc6633;">#region</span> IDisposable Members

        <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> Dispose()
        {
            Console.WriteLine(<span style="color: #006080;">"I am disposing!"</span>);
        }

        <span style="color: #cc6633;">#endregion</span>
    }

}</pre>
</div>
<p>This code returns the following result. In this screen shot you should notice that each time it calls the dispose method of the MyDisposable object.</p>
<p>&nbsp;<a href="/files/media/image/WindowsLiveWriter/ReturningFromInsideaUsingStatement_1505E/UsingStatementReturn_7.jpg"><img style="border: 0px none ;" src="http://brendan.enrick.com/files/media/image/WindowsLiveWriter/ReturningFromInsideaUsingStatement_1505E/UsingStatementReturn_thumb_2.jpg" border="0" alt="UsingStatementReturn" width="434" height="291" /></a></p>
<p>Give the code a shot in a console application, and you will see that the using statement cleans up disposable objects pretty nicely.</p>
<p>Download this sample code as a small C# console application <a href="/files/downloads/UsingStatementReturn.zip">here</a>.</p>
<p>I hope you enjoyed this post. I would also like to thank Lambros for the good comment. I hope to get more feedback from you in the future.</p>
