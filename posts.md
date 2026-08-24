---
layout: default
title: Posts
permalink: /posts/
---

# Posts

<div class="thinking-box terminal">
  <div class="prompt">$ research --status</div>

  <h2 class="thinking-title">
    Still Thinking<span class="thinking-dots">...</span>
  </h2>

  <div id="live-datetime" class="live-datetime"></div>

  <p>Somewhere between a conjecture and a segmentation fault.</p>
</div>


<div class="posts-list">

{% for post in site.posts %}

<article class="post-preview">

  <div class="post-date">
    {{ post.date | date: "%B %d, %Y" }}
  </div>

  <h2>
    <a href="{{ post.url | relative_url }}">
      {{ post.title }}
    </a>
  </h2>

  <div class="post-excerpt">
    {{ post.excerpt }}
  </div>

  <a class="read-more" href="{{ post.url | relative_url }}">
    Read more →
  </a>

</article>

{% endfor %}

</div>


<script>
function updateDateTime() {

    const now = new Date();

    const options = {
        weekday: 'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric',
        hour: '2-digit',
        minute: '2-digit',
        second: '2-digit'
    };

    document.getElementById("live-datetime").textContent =
        now.toLocaleString(undefined, options);
}

updateDateTime();

setInterval(updateDateTime, 1000);
</script>