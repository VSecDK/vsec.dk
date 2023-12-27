---
permalink: /about/members/
title: "VSec Members"
toc: false

sidebar:
  nav: sidebar-about
---

Want to become verified and get access to the closed discord channels?
Send a proof containing your handle/nickname, name and current workplace to one of the moderators from either your LinkedIn or Twitter profile.
You can also make a pull request directly from Github to this page as proof.

{% comment %}
    Due to Jekyll Liquid being insane in sorting and data files (array with hash, rather than array of objects)
    The below evil is nesecarry as Ruby's glob fitler sorting is off, and instead of having files named 0001, 0002, etc.
    A ID is required in every yaml and using this for sorting... go figure...
{% endcomment %}

{% assign members = "" | split: "," %}
{% for item in site.data.members -%}
    {% assign value = item[1] %}
    {% assign members = members | push: value %}
{% endfor %}
{% assign members = members | sort:'id' %}

{% for member in members %}
## {{member.name}}{% if member.nickname %} ({{ member.nickname }}){% endif %}

 {% if member.title %}{{ member.title }}{% endif %} {% if member.workplace %} @ {{ member.workplace }}{% endif %}
<ul class="author__urls social-icons member__socials">
  {% for social in member.socials %}
  
  {% case social[0] %}
    {% when "mail" %}
<li><a href="mailto:{{ social[1] }}/"><i class="fas fa-fw fa-envelope-square"></i><span class="label">Mail</span></a></li>

    {% when "linkedin" %}
<li><a href="https://www.linkedin.com/in/{{ social[1] }}/"><i class="fab fa-fw fa-linkedin"></i><span class="label">LinkedIn</span></a></li>

    {% when "twitter" %}
<li><a href="https://twitter.com/{{ social[1] }}"><i class="fab fa-fw fa-twitter-square"></i><span class="label">Twitter</span></a></li>

    {% when "mastadon" %}
      {% assign mastodon = social[1] | split:'@' %}
<li><a href="https://{{ mastodon[1] }}/@{{ mastodon[0] }}"><i class="fab fa-fw fa-mastodon"></i><span class="label">Mastadon</span></a></li>

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
