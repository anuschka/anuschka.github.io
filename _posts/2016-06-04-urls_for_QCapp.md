---
layout: post
title:  URLs for the app
tags:
- Blog
- Post
---

I was wondering how to form URLs for the application.

Maksim suggested to do something like:

* /reagent/     <- display all reagents
* /reagent/1351/   <- reagent with an ID 1351
* /reagent/new/   <- enter new reagent
* /reagent/edit/1351/    <- edit reagent ID 1351
* /reagent/delete/1351/   <- delete reagent ID 1351
* /reagent/?year=2016    <- filter for reagents

I use the following sintax in the urls.py <code>url(r'^reagent/new/$', views.reagent_new_view, name='reagent_new_view')</code> and can call the page by name in the template
<code>&lt;a href="{% url "reagent_new_view %}"?&gt;</code>
