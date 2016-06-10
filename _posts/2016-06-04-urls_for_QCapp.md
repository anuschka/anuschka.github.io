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

To display Yes/No in a table depending on the value of a field I use:


{% highlight %}{% if reagent.requiresIDcard %} Yes {% else %} No {% endif %}{% endhighlight %}
