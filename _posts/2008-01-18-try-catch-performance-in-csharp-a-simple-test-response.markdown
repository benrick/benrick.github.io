---
layout: post
title: "Try Catch Performance in CSharp: A Simple Test Response"
date: 2008-01-18 14:57:00 -0500
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Try-Catch-Performance-in-CSharp-A-Simple-Test-Response"
---
<!-- more -->

<p>I read an interesting little post about a <a href="http://paltman.com/2008/01/17/try-except-performance-in-python-a-simple-test/" target="_blank">Try Except Performance Test Using Python</a> written by <a href="http://paltman.com/" target="_blank">Patrick Altman</a>. As he mentioned, I have also had discussions with people about this exact topic in the past plenty of times. He was testing the performance issue of whether it is better to use a try catch block to handle possible errors or to check for them before they're a problem.</p>
<p>He handled 2 different cases; the success and the failure. Using loops he performed time checks on these to see how long it took. I thought it was very interesting, but the nice question is how does this hold up using C#. So I also wrote a simple little test similar to his. The results are pretty interesting. Keep in mind this just gives some rough estimates on this.</p>
<p>&nbsp;</p>
<blockquote>
<p>The case where the key does not exist:<br /> 1,000 iterations:<br /> Try_NotExist(1000) = 00:00:00.0852580<br /> Without_Try_NotExist(1000) = 00:00:00.0000089<br /> Without_Try_NotExist_Not(1000) = 00:00:00.0000089<br /> 100,000 iterations:<br /> Try_NotExist(100000) = 00:00:06.1590461<br /> Without_Try_NotExist(100000) = 00:00:00.0006802<br /> Without_Try_NotExist_Not(100000) = 00:00:00.0006799<br /> 1,000,000 iterations:<br /> Try_NotExist(1000000) = 00:01:02.8172468<br /> Without_Try_NotExist(1000000) = 00:00:00.0070592<br /> Without_Try_NotExist_Not(1000000) = 00:00:00.0092609</p>
<p>The case where the key does exist:<br /> 1,000 iterations:<br /> Try_Exist(1000) = 00:00:00.0000083<br /> Without_Try_Exist(1000) = 00:00:00.0000117<br /> Without_Try_Exist_Not(1000) = 00:00:00.0000117<br /> 100,000 iterations:<br /> Try_Exist(100000) = 00:00:00.0006185<br /> Without_Try_Exist(100000) = 00:00:00.0008624<br /> Without_Try_Exist_Not(100000) = 00:00:00.0008492<br /> 1,000,000 iterations:<br /> Try_Exist(1000000) = 00:00:00.0088896<br /> Without_Try_Exist(1000000) = 00:00:00.0086661<br /> Without_Try_Exist_Not(1000000) = 00:00:00.0097892</p>
</blockquote>
<p>As you can see here my results are somewhat similar to the findings Patrick found. If it is going to fail often at all you're much better off checking for the error before it fails because of how immense the difference between handling the error and not is. However if pretty much every time the code will succeed without any errors, you're better off with the try-catch block by a very small amount. The fact that it is only a small amount better tells me that I am much better off checking for an error than I am using a try-catch block to trap the error.</p>
<p>And so you can try for yourself or inform me of any errors I've made I'll include my code.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; font-size: 8pt; width: 100%; color: black; line-height: 12pt; font-family: consolas,'Courier New',courier,monospace; background-color: #f4f4f4;"><span style="color: #0000ff;">using</span> System;
<span style="color: #0000ff;">using</span> System.Diagnostics;
<span style="color: #0000ff;">using</span> System.Text;

<span style="color: #0000ff;">namespace</span> Try_Catch_Performance
{
    <span style="color: #0000ff;">class</span> Program
    {
        <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">int</span>[] x = { 0 };
        <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">int</span> ExistIndex = 0;
        <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">int</span> NotExistIndex = 1;

        <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Try_NotExist(<span style="color: #0000ff;">int</span> iterations)
        {
            Stopwatch st = <span style="color: #0000ff;">new</span> Stopwatch();
            st.Start();
            <span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> i = 0; i &lt; iterations; i++)
            {
                <span style="color: #0000ff;">try</span>
                {
                    <span style="color: #0000ff;">int</span> y = x[NotExistIndex];
                }
                <span style="color: #0000ff;">catch</span> (Exception)
                {
                }
            }
            st.Stop();
            Console.WriteLine(<span style="color: #006080;">"Try_NotExist({0}) = {1}"</span>, iterations, st.Elapsed);
        }

        <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Without_Try_NotExist(<span style="color: #0000ff;">int</span> iterations)
        {
            Stopwatch st = <span style="color: #0000ff;">new</span> Stopwatch();
            st.Start();
            <span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> i = 0; i &lt; iterations; i++)
            {
                <span style="color: #0000ff;">if</span> (x.Length &gt; NotExistIndex)
                {
                    <span style="color: #0000ff;">int</span> y = x[NotExistIndex];
                }
            }
            st.Stop();
            Console.WriteLine(<span style="color: #006080;">"Without_Try_NotExist({0}) = {1}"</span>, iterations, st.Elapsed);
        }

        <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Without_Try_NotExist_Not(<span style="color: #0000ff;">int</span> iterations)
        {
            Stopwatch st = <span style="color: #0000ff;">new</span> Stopwatch();
            st.Start();
            <span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> i = 0; i &lt; iterations; i++)
            {
                <span style="color: #0000ff;">if</span> (!(x.Length &lt;= NotExistIndex))
                {
                    <span style="color: #0000ff;">int</span> y = x[NotExistIndex];
                }
            }
            st.Stop();
            Console.WriteLine(<span style="color: #006080;">"Without_Try_NotExist_Not({0}) = {1}"</span>, iterations, st.Elapsed);
        }

        <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Try_Exist(<span style="color: #0000ff;">int</span> iterations)
        {
            Stopwatch st = <span style="color: #0000ff;">new</span> Stopwatch();
            st.Start();
            <span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> i = 0; i &lt; iterations; i++)
            {
                <span style="color: #0000ff;">try</span>
                {
                    <span style="color: #0000ff;">int</span> y = x[ExistIndex];
                }
                <span style="color: #0000ff;">catch</span> (Exception)
                {
                }
            }
            st.Stop();
            Console.WriteLine(<span style="color: #006080;">"Try_Exist({0}) = {1}"</span>, iterations, st.Elapsed);
        }

        <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Without_Try_Exist(<span style="color: #0000ff;">int</span> iterations)
        {
            Stopwatch st = <span style="color: #0000ff;">new</span> Stopwatch();
            st.Start();
            <span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> i = 0; i &lt; iterations; i++)
            {
                <span style="color: #0000ff;">if</span> (x.Length &gt; ExistIndex)
                {
                    <span style="color: #0000ff;">int</span> y = x[ExistIndex];
                }
            }
            st.Stop();
            Console.WriteLine(<span style="color: #006080;">"Without_Try_Exist({0}) = {1}"</span>, iterations, st.Elapsed);
        }

        <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Without_Try_Exist_Not(<span style="color: #0000ff;">int</span> iterations)
        {
            Stopwatch st = <span style="color: #0000ff;">new</span> Stopwatch();
            st.Start();
            <span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> i = 0; i &lt; iterations; i++)
            {
                <span style="color: #0000ff;">if</span> (!(x.Length &lt;= ExistIndex))
                {
                    <span style="color: #0000ff;">int</span> y = x[ExistIndex];
                }
            }
            st.Stop();
            Console.WriteLine(<span style="color: #006080;">"Without_Try_Exist_Not({0}) = {1}"</span>, iterations, st.Elapsed);
        }

        <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> Main(<span style="color: #0000ff;">string</span>[] args)
        {
            Console.WriteLine(<span style="color: #006080;">"The case where the key does not exist:"</span>);
            Console.WriteLine(<span style="color: #006080;">"1,000 iterations:"</span>);
            Try_NotExist(1000);
            Without_Try_NotExist(1000);
            Without_Try_NotExist_Not(1000);
            Console.WriteLine(<span style="color: #006080;">"100,000 iterations:"</span>);
            Try_NotExist(100000);
            Without_Try_NotExist(100000);
            Without_Try_NotExist_Not(100000);
            Console.WriteLine(<span style="color: #006080;">"1,000,000 iterations:"</span>);
            Try_NotExist(1000000);
            Without_Try_NotExist(1000000);
            Without_Try_NotExist_Not(1000000);

            Console.WriteLine(<span style="color: #006080;">"The case where the key does exist:"</span>);
            Console.WriteLine(<span style="color: #006080;">"1,000 iterations:"</span>);
            Try_Exist(1000);
            Without_Try_Exist(1000);
            Without_Try_Exist_Not(1000);
            Console.WriteLine(<span style="color: #006080;">"100,000 iterations:"</span>);
            Try_Exist(100000);
            Without_Try_Exist(100000);
            Without_Try_Exist_Not(100000);
            Console.WriteLine(<span style="color: #006080;">"1,000,000 iterations:"</span>);
            Try_Exist(1000000);
            Without_Try_Exist(1000000);
            Without_Try_Exist_Not(1000000);
        }
    }
}</pre>
</div>
<p>Happy Error Checking!</p>
