---
layout: default
---

<div class="jumbotron">
  <div class="container">
    <h1>{{ site.description }}</h1>
  </div>
</div>

<div class="container">
  {% for post in site.posts %}
  <div>

    <div>
      <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>
      <p><i class="fa fa-clock-o fa-fw" aria-hidden="true"></i> {{ post.date | date: '%B %d, %Y' }}</p>
    </div>

    <div>
      <a href="{{ site.baseurl }}{{ post.url }}" class="btn btn-primary btn-simple">Read More</a>
    </div>

  </div>
  {% endfor %}
</div>
