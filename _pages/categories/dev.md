---
title: "dev"
layout: archive
permalink: /dev
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.dev %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}