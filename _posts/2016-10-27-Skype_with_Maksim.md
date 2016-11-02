---
layout: post
title:  Concept of args and kwargs
tags:
- Blog
- Post
---

Maksim and I disccussed the concept of args and kwargs.

So far I have learned that:

* You would use args when you're not sure how many arguments might be passed to your function, i.e. it allows you pass an arbitrary number of arguments to your function
* kwargs allows you to handle named arguments that you have not defined in advance

More on args and kwargs on SO <a href="http://stackoverflow.com/questions/3394835/args-and-kwargs">here</a>.

We analized django source in <a href="https://github.com/django/django/blob/master/django/views/generic/base.py">base.py</a> for the "view" class and "as_view" method. As_view is a <a href="http://stackoverflow.com/questions/14758483/how-is-djangos-classonlymethod-useful"> classonlymethod </a>.
