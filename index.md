---
layout: default
---
<div id="scribtLogo">
    <img alt="ScriBt" src="https://github.com/ScriBt/images/raw/master/ScriBtLogo.png" height="155" width="407" title="ScriBt">
    <h2><span class="symbolGreen">[!]</span> {{ site.description }} <span class="symbolGreen">[!]</span></h2>
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
