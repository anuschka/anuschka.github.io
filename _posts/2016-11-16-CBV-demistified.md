---
layout: post
title:  Class based views demystified
tags:
- Blog
- Post
---

I finally got a hang of CBV - Class Based Views in Django.
The function based view for <b>editing an existing reagent</b> is above and the CBV is below.  
<pre>
<code>
# @login_required
# def reagent_edit_view(request, id):
#
#     if request.method == 'GET':
#         print('edit', id)
#         obj = get_object_or_404(Reagent.objects.filter(id=id))
#         form = ReagentForm(instance=obj)
#         context = {
#             'active_page': 'reagent',
#             'id': id,
#             'form': form
#         }
#         return TemplateResponse(request, 'reagents_edit.html', context)
#     elif request.method == 'POST':
#         obj = get_object_or_404(Reagent.objects.filter(id=id))
#
#         form = ReagentForm(request.POST, instance=obj)
#         print(form.errors)
#         if form.is_valid():
#             form.save()
#             return HttpResponseRedirect('/reagent/')
#         context = {
#             'active_page': 'reagent',
#             'id': id,
#             'form': form
#         }
#         return TemplateResponse(request, 'reagents_edit.html', context)

class ReagentEditView(FormView):
    template_name = 'reagents_edit.html'
    form_class = ReagentForm

    def get_form(self, form_class):
        """
        Check if the user already saved reagent details. If so, then show
        the form populated with those details, to let user change them.
        """
        try:
            reagent = Reagent.objects.get(id=self.args[0])
            return form_class(instance=reagent, **self.get_form_kwargs())
        except Reagent.DoesNotExist:
            return form_class(**self.get_form_kwargs())

    def form_valid(self, form, **kwargs):
        form.save()
        return HttpResponseRedirect('/reagent/')

reagent_edit_view = login_required(ReagentEditView.as_view())

</code>
</pre>

In order to present some extra information in the context beyond that provided by the generic view
I followed the documentation <a href="https://docs.djangoproject.com/en/1.10/topics/class-based-views/generic-display/#adding-extra-context/">here</a> and
used the get_context_data method:

<pre>
<code>
def get_context_data(self, **kwargs):
      context = super(ReagentEditView, self).get_context_data(**kwargs)
      context['active_page'] = 'reagent'
      return context
</code>
</pre>

I still need to figure out how to:

* why the checkbox value for RequiresIDCard does not get populated in the form
