---
layout: page
pagination: 
  enabled: true
---

I'm Brendan Enrick, and I try to leave things better than I found them.

I host the DevChatter live coding streams on Twitch and the videos on YouTube!

{% for post in paginator.posts %}
  <h1>{{ post.title }}</h1>
{% endfor %}
