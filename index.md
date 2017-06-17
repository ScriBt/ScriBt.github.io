---
layout: default
---
<div id="scribtLogo">
    <img alt="ScriBt" src="https://cloud.githubusercontent.com/assets/14874906/25773497/ea75ad0e-329b-11e7-92fb-e373d11fdd4b.png" title="ScriBt">
    <h1>{{ site.description }}</h1>
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
