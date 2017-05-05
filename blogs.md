---
layout: post
permalink: blogs
date:   2017-01-10 15:50:06 +0530
sitemap:
    priority: 1.0
    changefreq: 'monthly'
    lastmod: 2017-01-06 15:50:06 +0530
---

<div class="panel-group" id="accordion" role="tablist" aria-multiselectable="true">
{% for post in site.posts %}
  <div class="panel panel-default post-preview">
        <a role="button" data-toggle="collapse" data-parent="#accordion" href="#collapse{{ post.permalink }}" aria-expanded="true" aria-controls="collapse{{ post.permalink }}">
          <div class="panel-heading post-preview" role="tab" id="heading{{ post.permalink }}">
          <h2 class="panel-title post-title">
              {{ post.title }}
          </h2>
          </div>
        </a>
    <div id="collapse{{ post.permalink }}" class="panel-collapse collapse" role="tabpanel" aria-labelledby="heading{{ post.permalink }}">
      <div class="panel-body post-preview">
            {% if post.content contains '<!--more-->' %}
             {% assign sec = post.content | split:'<!--more-->' %}
             {{ sec[1] }}
            {% else %}
             {{ post.excerpt }}
            {% endif %}
          <p class="readmore">
            <a href="{{ post.url }}" target="_blank">
              Read this article <i class="glyphicon glyphicon-chevron-right" aria-hidden="true"></i>
            </a>
          </p>
          {% assign words = post.content | number_of_words %}
            {% if words < 360 %}
              <p class="post-meta">
                <span class="pull-left">Posted on {{ post.date | date: '%B %d, %Y' }}</span>
                <span class="pull-right">1 min to read</span>
              </p>
            {% else %}
              <p class="post-meta">
                <span class="pull-left">Posted on {{ post.date | date: '%B %d, %Y' }}</span>
                <sapn class="pull-right">~ {{ words | divided_by:360 }} mins to read</span>
              </p>
              <div class="clearfix"></div>
            {% endif %}

      </div>
    </div>
  </div>
{% endfor %}
</div>
