---
title: "컴퓨터 과학"
layout: archive
permalink: /CS
author_profile: true
sidebar_main: true
sidebar:
    nav: "sidebar-category"
---


{% assign posts = site.categories.CS %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}