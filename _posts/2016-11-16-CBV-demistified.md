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

I still need to figure out how to:

* update context for active_page
* why the checkbox value for RequiresIDCard does not get populated in the form
