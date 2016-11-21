---
layout: post
title:  Pagination using CBV
tags:
- Blog
- Post
---

I was able to transform my Reagents All view that uses pagination to CBV using
this excellent article from <a href="https://ana-balica.github.io/2015/01/29/pagination-in-django/"> Ana Balica</a>.

<b>reagent_view.py</b>
<pre>
<code>
class ReagentAllView(ListView):
    model = Reagent
    paginate_by = 4
    template_name = 'reagents.html'

    def get_context_data(self, **kwargs):
        context = super(ReagentAllView, self).get_context_data(**kwargs)
        context['active_page'] = 'reagent'
        reagent_list = Reagent.objects.all()
        paginator = Paginator(reagent_list, self.paginate_by)
        page = self.request.GET.get('page')
        try:
            reagent_list = paginator.page(page)
        except PageNotAnInteger:
            reagent_list = paginator.page(1)
        except EmptyPage:
            reagent_list = paginator.page(paginator.num_pages)

        return context

    def get_queryset(self):
        queryset = Reagent.objects.all()
        sort_by = self.request.GET.get('sortBy')
        if sort_by == 'expiryDate':
            queryset = queryset.order_by('expiry')
        elif sort_by == 'entryDate':
            queryset = queryset.order_by('created_at')
        elif sort_by == 'lot':
            queryset == queryset.order_by('lot')
        return queryset

reagent_view = login_required(ReagentAllView.as_view())
</code>
</pre>

<b>pagination.html snippet included in reagents.html</b>
<pre>
<code>
{# my_library/templates/snippets/pagination.html #}
{% if is_paginated %}
  <nav>
    <ul class="pagination">
      {% if page_obj.has_previous %}
        <li>
          <a href="?page={{ page_obj.previous_page_number }}">
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
          <a href="?page={{ page }}">{{ page }}</a>
        </li>
      {% endfor %}

      {% if page_obj.has_next %}
        <li>
          <a href="?page={{ page_obj.next_page_number }}">
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
