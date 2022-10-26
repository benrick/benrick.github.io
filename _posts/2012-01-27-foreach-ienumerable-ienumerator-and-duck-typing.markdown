---
layout: post
title: "Foreach, IEnumerable, IEnumerator, and Duck Typing"
date: 2012-01-27 10:00:00 -0500
comments: true
published: true
categories: ["Archive"]
tags: ["C#", "IEnumerable", "Duck Typing", "IEnumerator", "Fun"]
permalink: "/post/Foreach-IEnumerable-IEnumerator-and-Duck-Typing/"
---
<!-- more -->



<p>During my <a href="/post/CodeMash-2012-Recap/" target="_blank">Software Craftsmanship Precompiler session</a>, I heard one of the students say, “all you need is an IEnumerable to use a foreach loop”. This sparked a bit of fun when I asked Steve Smith, my co-presenter, if that was correct. He confirmed that it was, and I disagreed. Being the scientists that we are, we decided to try it and see what happened. I of course knew that <a href="http://en.wikipedia.org/wiki/Duck_typing" target="_blank">duck typing</a> in C# should allow the Foreach loop to compile without anything having the method required by the IEnumerable interface. This means that we just need a GetEnumerator method.</p>  <p>We wrote the code that did this and it compiled! </p>  <p>Duck typing is awesome, because it allows the language to treat my type the way I want it to because it has the right tools to do the job. The term duck typing comes from the idea that if it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck. </p>  <p>In the foreach loop example, duck typing assumes that what you have here is able to be enumerated, because it has a method to get the enumerator. If we look at the IEnumerable interface, we can see that this is what we are required to implement.</p>  <div id="codeSnippetWrapper">   <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> MyCollection : IEnumerable<br>{<br>    <span style="color: #0000ff">public</span> IEnumerator GetEnumerator()<br>    {<br>        <span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> NotImplementedException();<br>    }<br>}<br></pre>

  <br></div>

<p>Now that we have our collection written and implementing IEnumerable, we can write a foreach loop that uses our collection.</p>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet">var myCollection = <span style="color: #0000ff">new</span> MyCollection();<br><span style="color: #0000ff">foreach</span> (var thing <span style="color: #0000ff">in</span> myCollection)<br>{<br>    <span style="color: #008000">// Do something with the thing</span><br>}<br></pre>

  <br></div>

<p>Finally, because of the duck typing in C#, we can remove the interface from the code, but keep the method.</p>

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> MyCollection<br>{<br>    <span style="color: #0000ff">public</span> IEnumerator GetEnumerator()<br>    {<br>        <span style="color: #0000ff">throw</span> <span style="color: #0000ff">new</span> NotImplementedException();<br>    }<br>}<br></pre>

  <br></div>

<p>It still compiles!</p>

<p>One of the many <a href="/post/Null-Reference-Exception-on-Instance-Methods/" target="_blank">cool things about C# that I love</a>. It’s a fun language, so go experimenting!</p>
