---
layout: post
title:  Django pagination preserving the GET parameters
tags:
- Blog
- Post
---

With Django's Pagination - preserving the GET params is simple.

First copy the GET params to a variable (in view):
<pre>
<code>
GET_params = request.GET.copy()
</code>
</pre>

and send it to the template in via context dictionary:

<pre>
<code>
context = self.get_context_data(form=form, object_list=self.object_list,
  active_page='reagent' ,query=self.request.GET.get('keyword'), GET_params=GET_params)
</code>
</pre>

Second thing you need to do is use it specify it in the url calls (href) in the template - an example (extending the basic pagination html to handle extra param condition):

<pre>
<code>
{% if is_paginated %}
  <nav>
    <ul class="pagination">
      {% if page_obj.has_previous %}
        <li>
          <a href="?{{GET_params.urlencode}}&page={{ page_obj.previous_page_number }}">
            <span>Previous</span>
          </a>
        </li>
      {% else %}
        <li class="disabled">
          <a href="#">
            <span>Previous</span>
          </a>
        </li>
      {% endif %}

      {% for page in paginator.page_range %}
        <li {% if page == page_obj.number %}class="active"{% endif %}>
          <a href="?{{GET_params.urlencode}}&page={{ page }}">{{ page }}</a>
        </li>
      {% endfor %}

      {% if page_obj.has_next %}
        <li>
          <a href="?{{GET_params.urlencode}}&page={{ page_obj.next_page_number }}">
            <span>Next</span>
          </a>
        </li>
      {% else %}
        <li {% if not page_obj.has_next %}class="disabled"{% endif %}>
          <a href="#">
            <span>Next</span>
          </a>
        </li>
      {% endif %}
    </ul>
  </nav>
{% endif %}
</code>
</pre>
