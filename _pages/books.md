---
title: "Book Notes"
layout: single
entries_layout: list
classes: wide
permalink: /books/
author_profile: true
taxonomy: book notes
---
<style type="text/css" media="screen">
        .gr_grid_container {
          /* customize grid container div here. eg: width: 500px; */
        }
        .archive__item-teaser {
            flex: 0 0 20%;
            padding-top: 4%;
            padding-bottom: 4%;
            padding-right: 7%;
        }
        .archive__item {
          display: flex;
          align-items: center;
        }
      </style>
{%- for post in site.categories[{{page.taxonomy}}] -%}
{%- unless post.hidden -%}
{% if post.header.teaser %}
{% capture teaser %}{{ post.header.teaser }}{% endcapture %}
{% else %}
{% assign teaser = site.teaser %}
{% endif %}

{% if post.id %}
{% assign title = post.title | markdownify | remove: "<p>" | remove: "</p>" %}
{% else %}
{% assign title = post.title %}
{% endif %}

<div class="{{ include.type | default: 'list' }}__item">
  <article class="archive__item" itemscope itemtype="https://schema.org/CreativeWork">
    {% if teaser %}
    <div class="archive__item-teaser">
      <img src="{{ teaser | relative_url }}" alt="">
    </div>
    {% endif %}
    <div class="archive__item-text-right">
    <h2 class="archive__item-title no_toc" itemprop="headline">
      {% if post.link %}
      <a href="{{ post.link }}">{{ title }}</a> <a href="{{ post.url | relative_url }}" rel="permalink"><i
          class="fas fa-link" aria-hidden="true" title="permalink"></i><span class="sr-only">Permalink</span></a>
      {% else %}
      <a href="{{ post.url | relative_url }}" rel="permalink">{{ title }}</a>
      {% endif %}
    </h2>
    {% include page__meta.html type=include.type %}
    {% if post.excerpt %}<p class="archive__item-excerpt" itemprop="description">
      {{ post.excerpt | markdownify | strip_html | truncate: 160 }}</p>{% endif %}
  </div>
  </article>
</div>
{%- endunless -%}
{%- endfor -%}