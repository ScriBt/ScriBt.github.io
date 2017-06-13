---
layout: default
---

<article itemscope itemtype="http://schema.org/BlogPosting">
    <header>
        <h1>{{ page.title }}</h1>
        <p><time datetime="{{ page.date | date_to_xmlschema }}" itemprop="datePublished">{{ page.date | date: "%b %-d, %Y" }}</time>
        </p>
    </header>

    <div itemprop="articleBody">
        {% if page.summary %}
        <div>{{page.summary}}</div>
        {% endif %}

        {{ content }}
    </div>
</article>
