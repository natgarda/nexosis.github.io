---
title: Guides
description: Guides that explain how to use the Nexosis API
copyright: 2017 Nexosis 
layout: fullwidth
breadcrumb: Guides
exclude_navbreadcrumb: true
exclude_navsidebar: true
exclude_navfooter: true
exclude_from_search: true
---

{% assign rawcats = "" %}
{% for post in site.guides %}
  {% assign tcats = post.category | join:'|' | append:'|' %}
  {% assign rawcats = rawcats | append:tcats %}
{% endfor %}

{% assign rawcats = rawcats | split:'|' | sort %}

{% assign cats = "" %}

{% for cat in rawcats %}
  {% if cat != "" %}

    {% if cats == "" %}
      {% assign cats = cat | split:'|' %}
    {% endif %}

    {% unless cats contains cat %}
      {% assign cats = cats | join:'|' | append:'|' | append:cat | split:'|' %}
    {% endunless %}
  {% endif %}
{% endfor %}

<div class="row">
  <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
    <h1>{{ page.title }}</h1>
    <hr>
    <!-- 
    {% for ct in cats %}
      <a class="badge badge-success" style="margin-left: 10px;" href="#{{ ct | slugify }}"> {{ ct }} </a>
    {% endfor %}
    <hr>
    -->
  </div>
</div>
<!-- New Layout -->
<style>
  h5 {font-size: 1.5em;font-weight: 600;}
</style>

{% for ct in site.guides-category-order %}
<div class="col-md-12">
  <div class="panel">
    <div class="panel-body">
      <div class="row">
        <div class="col-md-5">
          <div class="row">
            <div class="col-md-3">
              <img src="/assets/img/{{ ct | slugify }}.png" style="width: 100px;">
            </div>
            <div class="col-md-9">
              <h5 id="{{ ct | slugify }}" class="jumptarget mt20">{{ ct }}</h5>
              <!-- <p>Description goes here.</p> -->
            </div>
          </div>
        </div>
        <div class="col-md-7 p25 bg-color-lightGray" style="border-radius: 5px;">
          {% assign guides = site.guides | sort: "order" %}
          {% for post in guides %}
            {% if post.category contains ct %}
              <div class="col-md-6">
                <p><strong><a href="{{ site.url }}{{ post.url }}">{{ post.title }}</a></strong></p>
              </div>
            {% endif %}
          {% endfor %}
        </div>
      </div>
    </div>
  </div>
</div>
{% endfor %}