---
title: "Book Notes"
layout: single
entries_layout: list
classes: wide
permalink: /books/
author_profile: true
taxonomy: book notes
---

This section started off as my own personal notes. After having countless conversations with other entrepreneurs in my friend group, meetups, and accelerator programs; I decided to post my notes online. Now, when I hear another head of an engineering team who needs advice, I can cite my book notes that has helped me overcome a similar situation.

For a more in depth reason on why I put my book notes online, check out [this post]({% post_url 2020-09-06-about-book-summaries %}).
<style type="text/css" media="screen">

  .archive__item-teaser {
    flex: 0 0 20%;
    padding-top: 4%;
    padding-bottom: 4%;
    padding-right: 7%;
  }

  .archive__item.not_search {
    display: flex;
    align-items: center;
  }
</style>

{%- for post in site.categories[page.taxonomy] -%}
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
  <article class="archive__item not_search" itemscope itemtype="https://schema.org/CreativeWork">
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




I haven't put my notes for every book on my site. If you are curious what else I've read here are some links below.

{% include bookshelf-montage.html shelf-name="blog-books" hide_title=true %}

<style type="text/css" media="screen">
  .gr_grid_container {
    /* customize grid container div here. eg: width: 500px; */
    width: 90%;
  }

  .gr_grid_book_container {
    /* customize book cover container div here */
    float: left;
    width: 100px;
    height: 160px;
    padding: 0px 0px;
    overflow: hidden;
  }
</style>

