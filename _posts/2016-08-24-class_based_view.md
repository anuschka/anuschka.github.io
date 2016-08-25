---
layout: post
title:  Class based view
tags:
- Blog
- Post
---

Use decorator for class based view that requires login reagent_new_view = login_required(ReagentNewView.as_view()).
This is equivalent to
<pre>
<code>
@login_required
def ...
</code>
</pre>
in function based views.

Detailed descriptions, with full methods and attributes, for each of Django's class-based generic views. -> http://ccbv.co.uk/
We looked through reagents_view.py and reviewed which views do I translate from function based to class based.

reagent_view leave as function
reagentnewview is already a class based view
reagent_edit_view translate to a Class based FormView
delete_record_view leave as Function View but add decorator @require.POST. This is a decorator to require that a view accepts only the POST method.
get_search_results organize the code into separate functions:
<pre>
<code>
class SearchFormView(LoginRequredView):
   def _get_search_results(self, request):
       form = SearchForm(request.GET)
       print(request)
       print(form.errors)

       # Check that form is valid.
       if not form.is_valid():
           context = {
               'active_page': 'reagent',
               'form': form
           }
           return TemplateResponse(
               request, 'reagents_search.html', context)

       # Now, form is valid.
       # if 'keyword' in request.POST and request.POST['keyword']:
       q = form.cleaned_data['keyword']
       print(q)
       reagents_filtered = Reagent.objects.filter(
           Q(type__icontains=q) | Q(lot__icontains=q) |
           Q(manufacturer__icontains=q)
       )
       reagents = reagents_filtered

       # Pagination
       paginator = Paginator(reagents, 4)  # Show 4 reagents per page
       page = request.GET.get('page')
       if page:
           try:
               reagents = paginator.page(page)
           except PageNotAnInteger:
               # If page is not an integer, deliver first page.
               reagents = paginator.page(1)
           except EmptyPage:
               # If page is out of range (e.g. 9999), deliver last
               # page of results.
               reagents = paginator.page(paginator.num_pages)
       else:
           reagents = paginator.page(1)

       context = {
           'active_page': 'reagent',
           'form': form,
           'reagents': reagents,
           'reagents_filtered': reagents_filtered,
           'paginator': paginator,
           'GET_params': request.GET.copy(),
           'query': q
       }
       return TemplateResponse(
           request, 'reagents_search.html', context)

   def get(self, request):
       if 'keyword' in request.GET:
           return self._get_search_results(request)
       form = SearchForm()
       context = {
           'active_page': 'reagent',
           'form': form
       }
       return TemplateResponse(request, 'reagents_search.html', context)

</code>
</pre>

_get_search_result is a notation of my own *not Django function

Class based views are good for inheritance. Here is an example how to use inheritance:
<pre>
<code>
class LoginRequiredView(View):
   def dispatch(request, *args, **kwargs):
       if not request.user.is_authenticated():
           return HttpResponseRedirect('/login/')

       super().dispatch(request, *args, **kwargs):
</code>
</pre>
Use django_bootstrap3 to clean templates for reagents using template tags.
