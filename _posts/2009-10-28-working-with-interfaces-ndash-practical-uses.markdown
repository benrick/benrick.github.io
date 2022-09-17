---
layout: post
title: "Working with Interfaces - Practical Uses"
date: 2009-10-28 09:10:00 -0400
comments: true
published: true
categories: ["Archive"]
tags: ["Blog"]
permalink: "/post/Working-with-Interfaces-ndash-Practical-Uses/"
---
<!-- more -->



<p>Expanding on an article I wrote a couple of years ago where I explained <a href="http://aspalliance.com/1516_Understanding_Interfaces_in_C" target="_blank">interfaces in C#</a>, I&rsquo;d like to explain why people should use interfaces. I received an email from a reader of my ASP Alliance article. He understands <em>how</em> interfaces work, but he&rsquo;s trying to see why so many people are raving wildly about their greatness. His questioning of them is great, because it really is not obvious why interfaces are useful. Anyone who says otherwise is just trying to brag.</p>
<blockquote>
<p>A couple of years ago, you wrote an article for ASP Alliance called "Understanding Interfaces." Once again, I saw how the code works, once again, I failed to see how it will benefit me.</p>
<p>Here's where everything breaks down for me: You create an interface with just method, property and event signatures. Then you inherit them in a class, recreate these same signatures and write the code to implement these methods and properties.</p>
</blockquote>
<p>So I&rsquo;ll start by mentioning that nearly all patterns, practices, principles, etc. in software development are based on code reuse. One of the most important reasons for code reuse is change. Developers are always responding to and creating changes. We must mitigate the risks of change, identify where changes will occur, and we must make changes.</p>
<p>Right about now you might be thinking, &ldquo;but interfaces <em>don&rsquo;t</em> reuse code. They just force you to implement new code. Using inheritance would be the way to achieve code reuse.&rdquo; You ate technically correct. You understand how interfaces work, but you&rsquo;re not seeing why we use interfaces. Interfaces themselves do not give us code reuse at all, however, they enable us to achieve code reuse.</p>
<p>Remember that I said that we must identify where changes will occur. Making this identification allows us to<em> isolate changes</em> thus <em>mitigating the risks of changes</em> and allowing us to <em>make changes</em>. Isolating the places that change also allow us the reuse the code which <em>does not change</em>, so by keeping some parts separate we can reuse others. The interfaces are for the places we <em>can&rsquo;t</em> reuse the code.</p>
<p>Interfaces are &ldquo;places of change&rdquo;. Each implementation of the interface is a variation on how that required piece of the puzzle could have been implemented. This is contrary to how you&rsquo;ll see a lot of interfaces used. It is sometimes difficult to see this as the behavior of interfaces, because people overuse interfaces.</p>
<blockquote>
<p>As I see it, I could have saved a whole lot of time by not creating the interface in the first place! I mean, it's not doing any work. I still have to create the signatures in the class. Why on Earth do people praise these things and call them the answer to multiple inheritence? They don't do anything!</p>
</blockquote>
<p>It is mostly true that interfaces don&rsquo;t do anything. As far as being executable code is concerned an interface is basically just a worthless extra step, so why would we use them? Declaring an interface is like saying, &ldquo;there is more than one way that this behavior could be implemented, but interactions with this behavior should be done this way only.&rdquo; Having that common &ldquo;interface&rdquo; allows us to use any of these implementations interchangeably.</p>
<h3>When to Use Interfaces</h3>
<p>Some people would recommend that interfaces should be used everywhere. I&rsquo;ve heard people say that no variable should be declared with a concrete type if it can be avoided. That may be a valid point, but if you&rsquo;re just learning how interfaces can be useful that is a bad approach. If you don&rsquo;t see value in interfaces, you will certainly not see the value of them when people use them <em>everywhere</em>. This washes them out and obfuscates their purpose.</p>
<p>Interfaces are used for logic which will have multiple or changing implementations. This means that we should use them in places where we will out of necessity have duplicate logic. Using the interface is what allows us to do this. Take a look at this code for composing a letter.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">string</span> ComposeLetter(<span style="color: #0000ff">string</span> recipientName, <br />    <span style="color: #0000ff">string</span> messageBody, <span style="color: #0000ff">bool</span> isFormal)<br />{<br />    <span style="color: #0000ff">string</span> messageText = <span style="color: #0000ff">string</span>.Empty;<br />    <span style="color: #0000ff">if</span> (isFormal)<br />    {<br />        messageText += GetFormalGreeting(recipientName);<br />    }<br />    <span style="color: #0000ff">else</span><br />    {<br />        messageText += GetCasualGreeting(recipientName);<br />    }<br /><br />    messageText += messageBody;<br /><br />    <span style="color: #0000ff">if</span> (isFormal)<br />    {<br />        messageText += GetFormalSignature();<br />    }<br />    <span style="color: #0000ff">else</span><br />    {<br />        messageText += GetCasualSignature();<br />    }<br /><br />    <span style="color: #0000ff">return</span> messageText;<br />}</pre>
</div>
</div>
</div>
<p>Notice how we have these flow control operators dictating how the code will execute. What will happen if we need to have a third option for greetings and signatures for family members? We might add another else-if or we might use a switch. Either way this code gets larger and changed every time.</p>
<p>However, if we identify the aspects of the code that are changing we can isolate them and mitigate the risks of changing the code by keeping separate the logic which has multiple implementations. Notice we have already used one form of encapsulation by keeping each of those pieces of logic in separate methods. The logic we haven&rsquo;t encapsulated is the flow control.</p>
<p>We can create an interface for it. The best name I&rsquo;ve got for now is <em>IFormalityGenerator</em>, which is not a great name, but it will do for now. I&rsquo;ll create that interface with two methods: <em>GetGreeting</em> and <em>GetSignature</em>. Very simple interface. Now we can rewrite our method to look like this.</p>
<div id="codeSnippetWrapper">
<div id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;">
<div id="codeSnippetWrapper">
<pre id="codeSnippet" style="text-align: left; line-height: 12pt; background-color: #f4f4f4; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color: black; font-size: 8pt; overflow: visible; border-style: none; padding: 0px;"><span style="color: #0000ff">public</span> <span style="color: #0000ff">string</span> ComposeLetter(<span style="color: #0000ff">string</span> recipientName, <span style="color: #0000ff">string</span> messageBody, <br />    IFormalityGenerator formalityGenerator)<br />{<br />    <span style="color: #0000ff">string</span> messageText = <span style="color: #0000ff">string</span>.Empty;<br /><br />    messageText += formalityGenerator.GetGreeting(recipientName);<br />    <br />    messageText += GetMessageBody();<br /><br />    messageText += formalityGenerator.GetSignature();<br /><br />    <span style="color: #0000ff">return</span> messageText;<br />}</pre>
</div>
</div>
</div>
<p>We now just make the decision sooner and only once which implementation we are using. If this is a formal letter we will use the <em>FormalFormalityGenerator.</em> If it is casual we will use the <em>CasualFormalityGenerator</em>. Down the road when we create one for family members we can just go and create an implementation for the <em>FamilyFormalityGenerator</em>. We&rsquo;ve made it so we create new code each time instead of going and changing the existing code in this method.</p>
<p><em>The power of an interface is in its ability to encapsulate the volatile aspects of a program and isolate that which can be reused more easily.</em></p>
