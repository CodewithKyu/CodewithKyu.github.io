---
layout: default
title: Posts
permalink: /posts/
---

<div class="thinking-box">

  <div class="thinking-header">
    <span class="terminal-symbol">&gt;_</span>
    <span class="thinking-title">Still Thinking</span>
    <span class="thinking-dots">
      <span>.</span><span>.</span><span>.</span>
    </span>
  </div>

  <div class="thinking-tagline">
    Somewhere between a conjecture and a segmentation fault.
  </div>

  <div class="thinking-time" id="thinking-clock"></div>

</div>


<div class="posts-section">

  <h2>Posts</h2>

  {% if site.posts.size > 0 %}

    {% for post in site.posts %}

      <div class="post-item">

        <span class="post-date">
          {{ post.date | date: "%d %b %Y" }}
        </span>

        <a class="post-title" href="{{ post.url | relative_url }}">
          {{ post.title }}
        </a>

      </div>

    {% endfor %}

  {% else %}

    <div class="no-posts">
      No notes have escaped the notebook yet.
    </div>

  {% endif %}

</div>


<script>
function updateThinkingClock() {

    const now = new Date();

    const days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday"
    ];

    const months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December"
    ];

    let hours = now.getHours();
    const minutes = String(now.getMinutes()).padStart(2, "0");
    const seconds = String(now.getSeconds()).padStart(2, "0");

    const ampm = hours >= 12 ? "PM" : "AM";

    hours = hours % 12;
    hours = hours ? hours : 12;

    hours = String(hours).padStart(2, "0");

    const date =
        days[now.getDay()] + ", " +
        String(now.getDate()).padStart(2, "0") + " " +
        months[now.getMonth()] + " " +
        now.getFullYear();

    const time =
        hours + ":" +
        minutes + ":" +
        seconds + " " +
        ampm;

    document.getElementById("thinking-clock").textContent =
        "[" + date + ", " + time + "]";
}

updateThinkingClock();
setInterval(updateThinkingClock, 1000);
</script>