---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

[Download my CV](/Colin_Beniyaz_Billhardt_CV.pdf)

## Education

* MSc Data Science (distinction), University of Bath
* BSc Computer Science with Management, King's College London

## Work Experience

* Your work experience here

## Skills

* Your skills here

## Publications

{% for post in site.publications reversed %}
  {% include archive-single-cv.html %}
{% endfor %}

## Talks

{% for post in site.talks reversed %}
  {% include archive-single-talk-cv.html %}
{% endfor %}

## Teaching

{% for post in site.teaching reversed %}
  {% include archive-single-cv.html %}
{% endfor %}
