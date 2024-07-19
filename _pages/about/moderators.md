---
permalink: /about/moderators/
title: "VSec Moderators"
toc: false

sidebar:
  nav: sidebar-about
---

Need any form of help regarding VSec or the moderation of the VSec community, please reach out to one of our moderators.

{% assign moderators = site.profiles | where:'role', 'moderator' | sort: 'order'  %}

{% for moderator in moderators %}
## {{moderator.title}}

 {% if moderator.worktitle %}{{ moderator.worktitle }}{% endif %} {% if moderator.workplace %} @ {{ moderator.workplace }}{% endif %}
<ul class="author__urls social-icons member__socials">
  {% for social in moderator.socials %}
  
  {% case social[0] %}
    {% when "mail" %}
<li><a href="mailto:{{ social[1] }}"><i class="fas fa-fw fa-envelope-square"></i><span class="label">Mail</span></a></li>

    {% when "linkedin" %}
<li><a href="https://www.linkedin.com/in/{{ social[1] }}/"><i class="fab fa-fw fa-linkedin"></i><span class="label">LinkedIn</span></a></li>

    {% when "twitter" %}
<li><a href="https://twitter.com/{{ social[1] }}"><i class="fab fa-fw fa-twitter-square"></i><span class="label">Twitter</span></a></li>

    {% when "mastadon" %}
      {% assign mastodon = social[1] | split:'@' %}
<li><a href="https://{{ mastodon[1] }}/@{{ mastodon[0] }}"><i class="fab fa-fw fa-mastodon"></i><span class="label">Mastodon</span></a></li>

    {% when "github" %}
<li><a href="https://github.com/{{ social[1] }}"><i class="fab fa-fw fa-github"></i><span class="label">GitHub</span></a></li>

    {% when "gitlab" %}
<li><a href="https://gitlab.com/{{ social[1] }}"><i class="fab fa-fw fa-gitlab"></i><span class="label">GitLab</span></a></li>

    {% when "web" %}
<li><a href="{{ social[1] }}"><i class="fas fa-fw fa-link"></i><span class="label">Personal</span></a></li>

  {% endcase %}
  {% endfor %}
</ul>
{% endfor %}
