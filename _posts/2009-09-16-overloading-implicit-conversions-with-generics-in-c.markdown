---
layout: post
title: "Overloading Implicit Conversions with Generics in C#"
date: 2009-09-16 10:55:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Overloading-Implicit-Conversions-with-Generics-in-C", "/post/overloading-implicit-conversions-with-generics-in-c"]
---
<!-- more -->

<p>Overloading operators in a language is an excellent tool in every developer&rsquo;s tool belt. It allows us to design our code in ways feeling far more natural. For example if we didn&rsquo;t implement operator overloading for addition of numbers we would have some strange code. Could you imagine if we still wrote this kind of stuff?</p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">int</span> x = 5;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">int</span> y = 4;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">int</span> z = x.Add(y);</pre>
<!--CRLF--></div>
</div>
<p>When we teach addition the non-computer way we learn it as &ldquo;5 + 4 = 9&rdquo;. The language reverses things and we switch the expression into &ldquo;9 = 5 + 4&rdquo;, but this is no big deal since we&rsquo;re still using our operators. Some things happen behind the scenes so often we really don&rsquo;t even think about them. Implicit conversions of numbers happens all the time. If we have a method that returns an integer we can certainly assign that value to a double. Why? Since we don&rsquo;t lose any information doing that conversion it is just able to happen. We know that it is easy to store an integer value in a double so it is allowed.</p>
<p>One thing that I&rsquo;ve always loved about the Nullable objects in C# is their ability to trick many of their newer users. A lot of people really don&rsquo;t know about Nullable objects. I think they are fooled by the type? syntax into thinking it is something special. When the only thing special is the syntax. Beneath the surface we are actually just using Nullable&lt;type&gt;. My favorite part about the object is that they were nice enough to overload the implicit conversion from your type T into the Nullable&lt;T&gt;. The nullable object is just a cleverly hidden use of C# generics.</p>
<p>If you use .NET Reflector to examine the code for their implementation you will see this method.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">implicit</span> <span style="color: #0000ff">operator</span> T?(T <span style="color: #0000ff">value</span>)</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">{</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">return</span> <span style="color: #0000ff">new</span> T?(<span style="color: #0000ff">value</span>);</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">}</pre>
<!--CRLF--></div>
</div>
<p>&nbsp;</p>
<p>Sure that seems kind of boring. This is basically like a constructor in that it creates a new instance of the Nullable type and accepts an object of type T. The power comes from the fact that the user doesn&rsquo;t need to realize he is changing types. It lets us do this.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">int</span> regularInteger = 3</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">int</span>? nullableInteger = regularInteger;</pre>
<!--CRLF--></div>
</div>
<p>&nbsp;</p>
<p>Now to make things a little bit clearer I will change how their operator works so we don&rsquo;t use their &ldquo;?&rdquo; shorthand. We will qualify things in the code so it is clear how the generic is working for us.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">implicit</span> <span style="color: #0000ff">operator</span> Nullable&lt;T&gt;(T <span style="color: #0000ff">value</span>)</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">{</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">return</span> <span style="color: #0000ff">new</span> Nullable&lt;T&gt;(<span style="color: #0000ff">value</span>);</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">}</pre>
<!--CRLF--></div>
</div>
<p>&nbsp;</p>
<p>So now if you want to use this for your generic object you can do the same thing as above. All you need is a constructor for your object that takes in a value of T, and then you write this method with your class name instead of Nullable. There is one thing to keep in mind though. There is one thing that could catch you off guard if your generic object contains state. That is that using this operator <em>will create a new object</em>.</p>
<p>If your generic is being exposed using a property, <em>Value</em>, like with Nullable then you could just set <em>Value</em> equal to the object. That approach is not as elegant, so if you can avoid having to set the value of the <em>Value</em> property I recommend it.</p>
<p>You can also perform an implicit conversion the other way, but that can potentially lose information if your object has state. If it does not then it is safe to perform that one. To achieve it just switch things around so you have this instead.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">implicit</span> <span style="color: #0000ff">operator</span> T(Nullable&lt;T&gt; <span style="color: #0000ff">value</span>)</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">{</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">    <span style="color: #0000ff">return</span> <span style="color: #0000ff">value</span>.Value;</pre>
<!--CRLF-->
<pre style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">}</pre>
<!--CRLF--></div>
</div>
<p>So have fun assigning objects to the implicitly-converting, generic objects.</p>
<p>If you have questions or concerns or you just plain think I am wrong. Tell me about it! :-)</p>
