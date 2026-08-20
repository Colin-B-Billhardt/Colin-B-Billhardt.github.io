---
layout: archive
title: "Colin Billhardt"
permalink: /
author_profile: false
redirect_from: 
  - /about/
  - /about.html
---

## About Me
{: #about}

I'm Colin Billhardt, a data scientist with an MSc in Data Science (Distinction) from the University of Bath and a BSc in Computer Science with Management from King's College London.

### Research Interests

Besides traditional machine learning and deep learning, I am particularly interested in computer vision and pose estimation projects. My Masters thesis "Towards quantitative analysis for climbing - technique observation using pose estimation" evaluated the accuracy of current pose-estimation models when used in a climbing specific setting. Read more about my masters thesis in the writing section below.

[English CV](/Colin_Beniyaz_Billhardt_CV.pdf)
<br>
[German CV](/Colin_B_Billhardt_Lebenslauf.pdf)

<div class="about-socials" style="display:flex; flex-wrap:wrap; gap:1.25rem; margin:1.5em 0 0 0; font-size:1.6rem;">
{% if site.author.github %}<a href="https://github.com/{{ site.author.github }}" aria-label="GitHub" title="GitHub"><i class="fab fa-fw fa-github"></i></a>{% endif %}
{% if site.author.linkedin %}<a href="https://www.linkedin.com/in/{{ site.author.linkedin }}" aria-label="LinkedIn" title="LinkedIn"><i class="fab fa-fw fa-linkedin"></i></a>{% endif %}
{% if site.author.email %}<a href="mailto:{{ site.author.email }}" aria-label="Email" title="Email"><i class="fas fa-fw fa-envelope"></i></a>{% endif %}
{% if site.author.twitter %}<a href="https://twitter.com/{{ site.author.twitter }}" aria-label="X (Twitter)" title="X (Twitter)"><i class="fab fa-fw fa-x-twitter"></i></a>{% endif %}
{% if site.author.bluesky %}<a href="https://bsky.app/profile/{{ site.author.bluesky }}" aria-label="Bluesky" title="Bluesky"><i class="fab fa-fw fa-bluesky"></i></a>{% endif %}
{% if site.author.orcid %}<a href="{{ site.author.orcid }}" aria-label="ORCID" title="ORCID"><i class="ai ai-orcid ai-fw"></i></a>{% endif %}
{% if site.author.researchgate %}<a href="{{ site.author.researchgate }}" aria-label="ResearchGate" title="ResearchGate"><i class="fab fa-fw fa-researchgate"></i></a>{% endif %}
{% if site.author.googlescholar %}<a href="{{ site.author.googlescholar }}" aria-label="Google Scholar" title="Google Scholar"><i class="ai ai-google-scholar ai-fw"></i></a>{% endif %}
</div>

---

## Writing
{: #writing}

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url | relative_url }})
{% else %}
*No posts yet — check back soon.*
{% endfor %}

---

## Ecological Information & Climate Change Posts
{: #climate}

[Coming soon](#)

---

## Projects
{: #projects}

{% for item in site.portfolio %}
- [{{ item.title }}]({{ item.url | relative_url }})
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
