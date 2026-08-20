---
layout: archive
title: "Colin Billhardt"
permalink: /
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

## About Me
{: #about}

I'm Colin Billhardt, a data scientist with an MSc in Data Science (Distinction) from the University of Bath and a BSc in Computer Science with Management from King's College London.

[Download my English CV](/Colin_Beniyaz_Billhardt_CV.pdf) | [Download my German CV](/Colin_B_Billhardt_Lebenslauf.pdf)

### Research Interests

Besides traditional machine learning and deep learning, I am particularly interested in computer vision and pose estimation projects. My Masters thesis "Towards quantitative analysis for climbing - technique observation using pose estimation" evaluated the accuracy of current pose-estimation models when used in a climbing specific setting. Read more about my masters thesis in the blog section below.

---

## Blog Posts
{: #blog}

{% for post in site.posts %}
- **[{{ post.title }}]({{ post.url | relative_url }})** <span class="page__meta">{{ post.date | date: "%B %-d, %Y" }}</span>
{% else %}
*No blog posts yet — check back soon.*
{% endfor %}

---

## Ecological Information & Climate Change Posts
{: #climate}

{% assign climate_tags = site.posts | where_exp: "post", "post.tags contains 'Climate'" %}
{% assign ecology_tags = site.posts | where_exp: "post", "post.tags contains 'Ecology'" %}
{% assign climate_cats = site.posts | where_exp: "post", "post.categories contains 'Climate'" %}
{% assign ecology_cats = site.posts | where_exp: "post", "post.categories contains 'Ecology'" %}
{% assign climate_posts = climate_tags | concat: ecology_tags | concat: climate_cats | concat: ecology_cats | uniq %}
{% if climate_posts.size > 0 %}
{% for post in climate_posts %}
- **[{{ post.title }}]({{ post.url | relative_url }})** <span class="page__meta">{{ post.date | date: "%B %-d, %Y" }}</span>
{% endfor %}
{% else %}
*Coming soon — posts about ecology and climate change will appear here automatically. Tag a post with `Climate` or `Ecology` in its front matter to have it show up in this section.*
{% endif %}
---

## Technical Projects
{: #projects}

{% for item in site.portfolio %}
### [{{ item.title }}]({{ item.url | relative_url }})
{{ item.excerpt }}

{% else %}
*No projects listed yet.*
{% endfor %}

---

## Books
{: #books}

{% if site.books.size > 0 %}
{% for book in site.books %}
### [{{ book.title }}]({{ book.url | relative_url }})
{{ book.excerpt }}

{% endfor %}
{% else %}
*Coming soon — books I've written or am working on will be listed here.*
{% endif %}

---

## Research Papers
{: #papers}

{% for pub in site.publications %}
- **[{{ pub.title }}]({{ pub.url | relative_url }})** — *{{ pub.venue }}*, {{ pub.date | date: "%Y" }}
{% else %}
*No papers listed yet.*
{% endfor %}
