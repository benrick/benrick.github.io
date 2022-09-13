---
layout: post
title: "Expression Blend Issue with Abstract Base Classes"
date: 2009-10-28 17:22:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/Expression-Blend-Issue-with-Abstract-Base-Classes", "/post/expression-blend-issue-with-abstract-base-classes"]
---
<!-- more -->

<p>Earlier, I wrote a post about <a href="http://brendan.enrick.com/blog/silverlight-usercontrol-inheritance/" target="_blank">using inheritance with Silverlight UserControls</a>. The post shows really quickly how one can have their UserControl inherit from another class. One tip I&rsquo;ll mention is that the base class <em>can</em> be abstract, but not if you plan on using Expression Blend. Generally if you have a class which shouldn&rsquo;t ever be instantiate, you should make it abstract.</p>
<p>The issue is one that I discovered, much to my annoyance, the hard way. As it turns out Expression Blend is currently unable to give a preview of a UserControl that is inheriting from an abstract base class. When you open one of these in Blend you&rsquo;ll get the Red Box of Death and in it is a message stating, &ldquo;Exception: Cannot create an instance of &ldquo;MyClass&rdquo;.</p>
<p>Not exactly very helpful, but it does at least point you to the fact that there is something wrong with your base class. If you run into this make sure you know that you cannot use a base class. I believe that Blend requires a default constructor, and an abstract class has no constructors.</p>
<p><strong>Solution 1</strong></p>
<p>If you have control of the abstract class, you probably just want to make it a concrete class and hope no one is dumb enough to use it as a concrete class. This is actually a good place for a comment so you have a reminder of why the class is not abstract. Otherwise you might make it abstract again. The comment will also tip someone off that they can make it abstract if Blend ever supports this.</p>
<p><strong>Solution 2</strong></p>
<p>If you don&rsquo;t have control of the abstract class, perhaps because it is in a class library you&rsquo;re referencing, you will want to place a concrete class between your class and the abstract. This new class will be the one you specify in your XAML and is thus used by Expression Blend. This one adds an extra layer which really adds nothing and could cause confusion, so I would lean towards the other solution.</p>
