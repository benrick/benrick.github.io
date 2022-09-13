---
layout: post
title: "Linking to the \"I'm Feeling Lucky\" Google Search"
date: 2008-03-26 19:33:00 -0400
comments: true
published: true
categories: ["blog", "archives"]
tags: ["Orcs Goblins  and .NET"]
permalink: "/post/Linking-to-the-Im-Feeling-Lucky-Google-Search"
---
<!-- more -->



<p>So one thing I've always loved about Google is the I'm feeling lucky search feature. Most of the time I know that the top result is the one I need. Earlier today, I was googling for how to link directly to the Google results using an "I'm Feeling Lucky" search, and I found one interesting thing. I am not sure how accurate the information is, but it seems that <a href="http://valleywag.com/tech/google/im-feeling-lucky-button-costs-google-110-million-per-year-324927.php" target="_blank">Google loses $110 million per year because of the "I'm feeling lucky" button</a>. Clicking the button means you see no ads from Google, so Google effectively does not get any money from a user who clicks that button.</p>
<p>OK, so by now I would hope that someone is wondering why I would want to create a link which points to an "I'm Feeling Lucky" result. Well it is quite obvious that I want to hide the eventual destination of the link. I am assuming that people will notice that it goes to Google, but will not notice the part of the query string where it really doesn't send them to Google.</p>
<p>So I found out that all you have to add into the querystring is <strong>btnI=745</strong>. Yes, it is that easy, so Here is a nice example of a link I believe you should all see.</p>
<p><a title="http://www.google.com/search?hl=en&amp;q=french+military+victories&amp;btnI=745" href="http://www.google.com/search?hl=en&amp;q=french+military+victories&amp;btnI=745">http://www.google.com/search?hl=en&amp;q=french+military+victories&amp;btnI=745</a></p>
<p><img src="http://static.flickr.com/3148/2364635618_67bf9e743d.jpg" border="0" alt="Google-FrenchMilitary" /></p>
<p>Following the link I have listed above is the same as doing what my screen shot illustrates.</p>
<p>Yes, I think it is a very funny joke. That site has been the top result on Google for that search for a looong time. It is the top result for "french military victories", and is quite a funny result. It could use an update to look like the current version of the Google results page, but it is still pretty nice. I could also link to this site, and send people through Google to get there.</p>
<p><a href="http://www.google.com/search?hl=en&amp;q=Orcs+Goblins+.NET&amp;btnI=745" target="_blank">Orcs Goblins and .NET</a></p>
<p>Have a great day, and don't use this for anything nefarious!</p>
