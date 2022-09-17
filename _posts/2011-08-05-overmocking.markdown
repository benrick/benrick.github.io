---
layout: post
title: "Overmocking"
date: 2011-08-05 13:28:00 -0400
comments: true
published: true
categories: ["blog", "Archive"]
tags: ["Tips", "Rant", "Best Practices", "Unit Testing", "Mocking"]
permalink: "/post/Overmocking/"
---
<!-- more -->



<p>One of the most powerful tool available to developers testing a legacy code base is the ability to mock out classes that their code depends on. This is of great importance since our unit tests need to limit the scope, and we do this by trying to limit our dependencies. Through mocking we can exchange one dependency on the infrastructure of our application for an in-memory mock.</p>  <p>Sometimes mocking is overused, and I am not just talking about cases where every objected gets mocked to the point where we’re testing nothing. I am talking about a different issue in mocking. I am talking about where developers put on their mocking blinders when unit testing. It’s an easy thing to do, and I’ve done it plenty of times myself.</p>  <h2>Setting Up Our Example</h2>  <p>We will start of by defining our example. We will have a method to do some sort of calculation (an ideal and easy testing scenario). It will be a legacy code base, which means that it is untested code and probably hard to test. We’ll start off by making it a private static method and put in a nice dependency that one might try to mock to avoid. </p>  <div id="codeSnippetWrapper">   <div id="codeSnippetWrapper">     <div id="codeSnippetWrapper">       <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">private</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">decimal</span> CalculateFooOnXyz(Xyz xyzItem, <br>    <span style="color: #0000ff">decimal</span> calculationParameter1)<br>{<br>    var numbersInCalculation = Repository.GetNumbers()<br>        .Where(n =&gt; n.IsActive);<br><br>    <span style="color: #0000ff">foreach</span> (Number number <span style="color: #0000ff">in</span> numbersInCalculation)<br>    {<br>        <span style="color: #008000">// Some code that executes for each one.</span><br>    }<br>}</pre>

      <br></div>
Now that we have this method, which is scary and really needs some testing we’ll take a look at the simple way of testing it; we will use parameter injection to pass in the dependency since we’re static we not easily able to do any other safe forms of dependency injection. When we do this, we end up with the following code.</div>

  <div>&nbsp;</div>
</div>

<div id="codeSnippetWrapper">
  <div id="codeSnippetWrapper">
    <div id="codeSnippetWrapper">
      <div id="codeSnippetWrapper">
        <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">private</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">decimal</span> CalculateFooOnXyz(Xyz xyzItem, <br>    <span style="color: #0000ff">decimal</span> calculationParameter1, IRepository repository)<br>{<br>    var numbersInCalculation = repository.GetNumbers()<br>        .Where(n =&gt; n.IsActive);<br><br>    <span style="color: #0000ff">foreach</span> (Number number <span style="color: #0000ff">in</span> numbersInCalculation)<br>    {<br>        <span style="color: #008000">// Some code that executes for each one.</span><br>    }<br>}</pre>

        <br>This is a pretty simple change. We now mock out the repository and pass in the mock in our test and we tell it instead to return the collection we specify in memory instead of requesting the data from the database.</div>
    </div>
  </div>
</div>

<h2>Why This is Wrong</h2>

<p>My first question is, what is the name of the method? <em>CalculateFooOnXyz.</em> Notice that I didn’t say, “GetDataFromTheDatabase”. That’s because we shouldn’t be doing that. It isn’t part of the calculation. The numbers returned from the database are required for calculating, so that means that we should have that object as our dependency instead.</p>

<h2>How We Change It</h2>

<p>So instead of making the repository our parameter, we should make the collection of numbers our parameter. This way we’re depending on the in-memory collection of CLR objects. This is much less of a dependency, and in is not one that needs to be mocked. By doing this alternative we’re better following the Single Responsibility and Dependency Inversion principles.</p>

<p>Our best code for testing will look like this.</p>

<div id="codeSnippetWrapper">
  <div id="codeSnippetWrapper">
    <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; background-color: #f4f4f4; margin: 0em; border-left-style: none; padding-left: 0px; width: 100%; padding-right: 0px; font-family: 'Courier New', courier, monospace; direction: ltr; border-top-style: none; color: black; border-right-style: none; font-size: 8pt; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">private</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">decimal</span> CalculateFooOnXyz(Xyz xyzItem, <br>    <span style="color: #0000ff">decimal</span> calculationParameter1, List&lt;CalcNumbers&gt; numbersInCalculation)<br>{<br>  <span style="color: #0000ff">foreach</span> (Number number <span style="color: #0000ff">in</span> numbersInCalculation)<br>  {<br>    <span style="color: #008000">// Some code that executes for each one.</span><br>  }<br>}</pre>

    <br>Comments? Have a better way of doing it? Did I make a mistake?</div>
</div>
