---
layout: page
title: Certificates
# permalink: /certificates/
description: 
nav: false
nav_order: 3
show: false
display_categories: [NLP, Deep Learning, Machine Learning]
horizontal: false
---
<!-- pages/certificates.md -->

<div class="certificates">
{% if page.display_categories %}
  <!-- Display categorized certificates -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_certificates = site.certificates| where: "category", category %}
  {% assign sorted_certificates = categorized_certificates | sort: "importance" %}
  <!-- Generate cards for each certificate -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for certificate in sorted_certificates %}
      {% include certificates_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for certificate in sorted_certificates %}
      {% include certificates.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display certificates without categories -->

{% assign sorted_certificates = site.certificates | sort: "importance" %}

<!-- Generate cards for each certificate -->

{% if page.horizontal %}

<div class="container">
    <div class="row row-cols-2">
    {% for certificate in sorted_certificates %}
      {% include certificates_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for certificate in sorted_certificates %}
      {% include certificates.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
