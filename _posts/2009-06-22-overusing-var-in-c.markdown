---
layout: post
title: "Overusing var in C#"
date: 2009-06-22 09:37:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Overusing-var-in-C/"
---
<!-- more -->



<p>With C# 3.0 came one new feature I both love and hate; the implicitly typed local variable: var. I think it is great because it is implicitly typed, but it is still strongly typed. At compile time it will be the explicit type as if you had typed the actual type name. Visual Studio is able to determine during development what the type is, so there isn't much of a downside. However, I believe it gets overused.</p>
<p>I think it is great if the line contains the "new" keyword, because I can already see the type name because it gets written for the constructor. Using "var" all the time really irks me though. It is inconvenient, because I can't always tell what type the variable is. This isn't always too much of an issue, but I prefer defining the type when possible.</p>
<p>For generics it is great since those type names get quite long. With generics we define two types together, so with longer names this sometimes becomes a little unwieldy. This is one of the great strengths of this new behavior in C#.</p>
<p>Earlier today I was reading an interesting post from <a href="http://www.lostechies.com/blogs/jimmy_bogard/default.aspx" target="_blank">Jimmy Bogard</a>. He was blogging about <a href="http://www.lostechies.com/blogs/jimmy_bogard/archive/2009/06/18/the-filter-viewdata-anti-pattern.aspx" target="_blank">The Filter-View anti-pattern</a>. What bugged me about the post was his use of var. Now I know this has nothing to do with the actual post itself, but who can resist posting about their coding preferences?</p>
<p>In the post he had this code snippet.</p>
<div>
<pre style="border-style: none; margin: 0em; padding: 0px; overflow: visible; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: consolas,'Courier New',courier,monospace; color: black; font-size: 8pt;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">class</span> ProductController : Controller
{
    [LoginInfo]
    <span style="color: #0000ff;">public</span> ActionResult Index()
    {
        var products = _productRepository.FindAll();

        <span style="color: #0000ff;">return</span> View(products);
    }</pre>
</div>
<p>Now can you tell me what type is the variable products? Sure you might guess a collection of <em>Product</em> objects. You're probably right. Is it an IEnumerable? Is it an array? Is it a list? No, you don't know for certain. In fact you can't be sure it is a collection of <em>Product</em> objects. What if it were a collection of product <em>names</em>? That could be a badly named method and you get back strings.</p>
<p>You might think I am stretching a bit there on the strings, but there certainly could be methods which just didn't clarify well enough in there name. Now I know that I can mouse over the type in Visual Studio and instantly find out what type it is, but I should have to. In fact I probably wouldn't. I would probably try to use it and be kind of annoyed. Odds are I would have made an assumption on what type it is, and then I might have been annoyed when I tried to use <em>Length</em> thinking it was an array and then found our it was a <em>List</em> and I needed to use <em>Count</em>.</p>
<p>Anyway, I do recommend reading blog posts from Jimmy Bogard even though he overuses the implicitly typed local variable in his code snippets.</p>
