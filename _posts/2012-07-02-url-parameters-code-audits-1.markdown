---
layout: post
title: "URL Parameters - Code Audits #1"
date: 2012-07-02 10:00:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Blog"]
alias: ["/post/URL-Parameters-Code-Audits-1", "/post/url-parameters-code-audits-1"]
---
<!-- more -->
{% include imported_disclaimer.html %}
<p>This is the first post in a series that I am writing that focuses on some interesting finds from different code bases I&rsquo;ve seen over my years looking at lots of different software projects. Code Audits are one place where lots of interesting bits of code can be found, since you're combing through an entire software system. I will be explaining what I&rsquo;ve seen, why it&rsquo;s wrong, and usually the better approach if it&rsquo;s not obvious.</p>
<h3>URL Parameters</h3>
<p>URLs let you control the navigation as your user navigates around your site. Users may not know what URLs mean or how they work, but most people browsing the web know that URLs exist. A good number of them know that modifying that URL will take them to different pages. Even my mother knows that much about URLs.</p>
<p>It&rsquo;s not just a tech savvy computer programmer or hacker who can figure out that changing the URL might get them to a page they&rsquo;re trying to see. This is sometimes useful on site&rsquo;s whose navigation is somewhat lacking. It&rsquo;s also often possible to guess the page you&rsquo;re looking for by adding &ldquo;/login&rdquo; or some other common word to find a page whose link you&rsquo;re not seeing.</p>
<h3>The Bad</h3>
<p>On web sites that have user accounts associated with multiple accounts, it&rsquo;s quite common for the current account that the user is viewing to be specified in the address bar using a query string parameter. Normally, this means that there will be something along the lines of &ldquo;?AccountId=123456&rdquo; on the end of the URL. It&rsquo;s also very common for those to be built in as &ldquo;subfolders&rdquo; like this &ldquo;/Account/123456/&rdquo;. Either way, it&rsquo;s easily visible, modifiable information presented directly to the user.</p>
<p>As I am sure most of you can predict, I am going to point out that I&rsquo;ve seen some code that didn&rsquo;t do the proper protection to make sure that only an allowed user can access any given AccountId. The site will only display the links to the allowed accounts, but the site itself does not protect against a user changing that AccountId.</p>
<p>If you want to get to another user&rsquo;s account, you can just type in another AccountId into the URL and the site will take you there&hellip;</p>
<p>The circumstances where these mostly come up is when 1 user account is allowed to have access to more than one account. It&rsquo;s on these sites that the user will need to be able to change accounts, and sometimes users keep multiple accounts open at the same time, so the URL is needed to keep both open at the same time. It&rsquo;s important, however, that we maintain at least some level of security here.</p>
<h3>The Better</h3>
<p>When we build sites, it&rsquo;s extremely important that we validate inputs given by users to make sure that they&rsquo;re valid. It&rsquo;s also important to make sure that users have access to the information they&rsquo;re requesting.</p>
<p>The first thing you do when you receive user input is to validate that input. Obviously if you consider a URL to be user input, you would validate that immediately as well. This means that either directly or through some layer of abstraction, your code should be verifying a user has access to any information being requested.</p>
<h3>Citigroup</h3>
<p>There was a big fiasco last year related to Citigroup. (<a href="http://www.nytimes.com/2011/06/14/technology/14security.html">http://www.nytimes.com/2011/06/14/technology/14security.html</a>) The rumor is that they had a security breach based on this type of issue. I have no real, credible information about this, but it makes for a good example even if it&rsquo;s only rumor.</p>
<p>From the New York Times article we get these:</p>
<blockquote>
<p>Once inside, they leapfrogged between the accounts of different Citi customers by inserting vari-ous account numbers into a string of text located in the browser&rsquo;s address bar.</p>
</blockquote>
<p>That sure sounds to me like what I just described. If it is what I described, then this security expert stretched the truth quite a bit based on what is in that same article.</p>
<blockquote>
<p>One security expert familiar with the investigation wondered how the hackers could have known to breach security by focusing on the vulnerability in the browser. &ldquo;It would have been hard to prepare for this type of vulnerability,&rdquo; he said. The security expert insisted on anonymity because the inquiry was at an early stage.</p>
</blockquote>
<p>It&rsquo;s not hard to prepare for that kind of vulnerability. I guess if you have it, it&rsquo;s hard to track and log the issue. What&rsquo;s easy is not having the issue to begin with. It&rsquo;s a simple policy of making sure that all inputs are validated for permissions before being executed. Also, that is not a &ldquo;vulnerability in the browser&rdquo;.</p>
<h3>More Code Audit Nuggets</h3>
<p>Keep watching for more interesting nuggets of stuff that I&rsquo;ve seen in codebases.</p>
