---
layout: post
title:  UpdateView
tags:
- Blog
- Post
---

Maksim suggested I try the UpdateView instead of the FormView for my CBV to solve
the Boolean field not presenting itself in the Reagent edit template. It is still not working...
<pre>
<code>
class ReagentEditView(UpdateView):
    template_name = 'reagents_edit.html'
    form_class = ReagentForm

    def get_object(self, queryset=None):
        obj = Reagent.objects.get(id=self.args[0])
        return obj

    def get_context_data(self, **kwargs):
        context = super(ReagentEditView, self).get_context_data(**kwargs)
        context['active_page'] = 'reagent'
        return context

    def form_valid(self, form, **kwargs):
        form.save()
        return HttpResponseRedirect('/reagent/')

reagent_edit_view = login_required(ReagentEditView.as_view())
</code>
</pre>
