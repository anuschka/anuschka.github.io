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
<a href="?{{GET_params.urlencode}}&page={{ page_obj.previous_page_number }}">
</code>
</pre>
