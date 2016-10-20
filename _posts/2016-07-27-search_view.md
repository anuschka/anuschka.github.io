---
layout: post
title:  Search view
tags:
- Blog
- Post
---


I was developing the search view and template for the reagents model and had the following questions for Maksim:
* What is the best way to do form validation for the search form (consists of one search field)
* Should I include error in context and pass it to the template
* Can I generalize search for the whole app or each model has its own search view/template
* Code-review the CRUD for reagents

Once you’ve created your data models, Django automatically gives you a database-abstraction API that lets you create,
retrieve, update and delete objects. This document explains how to use this API. Refer to the data model reference for
full details of all the various model lookup options.

A Q() object, like an F object, encapsulates a SQL expression in a Python object that can be used in database-related operations.

In general, Q() objects make it possible to define and reuse conditions. This permits the construction of complex database queries
using | (OR) and & (AND) operators; in particular, it is not otherwise possible to use OR in QuerySets.
Here is the example Maksim suggested for the search view:


reagents_filtered = Reagent.objects.filter(
            Q(type__icontains=q) | Q(lot__icontains=q) |
            Q(manufacturer__icontains=q)
        )
