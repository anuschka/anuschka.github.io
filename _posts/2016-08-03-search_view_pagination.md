---
layout: post
title:  Search View pagination
tags:
- Blog
- Post
---


With Django's Pagination in the Search view I had to find the way how to preserve the GET parameters.
Withouth that I was replacing the URL with `?page=`.

First copy the GET params to a variable (in view):

`GET_params = request.GET.copy()`

and send it to the template in via context dictionary:
<pre>
<code>
return render_to_response(template,
                        {'request': request, 'contact': contact, 'GET_params':GET_params}, context_instance=RequestContext(request))
</code>
</pre>

Second thing you need to do is use it, specify it in the url calls (href) in the template - an example (extending the basic pagination html to handle extra param condition):
<pre>
<code>
{% if contacts.has_next %}
    {% if GET_params %}
        <a href="?{{GET_params.urlencode}}&amp;page={{ contacts.next_page_number }}">next</a>
    {% else %}
        <a href="?page={{ contacts.next_page_number }}">next</a>
    {% endif %}
{% endif %}
</code>
</pre>
