---
layout: default
---

<article itemscope itemtype="http://schema.org/BlogPosting">
    <header>
        <h1>{{ page.title }}</h1>
        <p><i class="fa fa-clock-o fa-fw" aria-hidden="true"></i> {{ page.date | date: '%B %d, %Y' }}</time>
        </p>
    </header>

    <div itemprop="articleBody">
        {% if page.summary %}
        <div>{{page.summary}}</div>
        {% endif %}

        {{ content }}
    </div>
</article>
