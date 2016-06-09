---
layout: post
title:  Forms in django
tags:
- Blog
- Post
---

During our weekly Skype meeting Maksim and I discussed Forms in Django. Maksim reviewed the new code on git with emphasys on <a href="https://github.com/anuschka/QCapp/blob/master/qcapp/templates/reagents_new.html">the reagents_new</a> form.

My questions for Maksim were related to the form submit/save functionality, form input id's and form validation.

Maksim suggested:

* using Django <a href="https://docs.djangoproject.com/en/1.9/topics/forms/modelforms/">ModelForm</a> since I am using the same fields in the form as I already have defined in the data model (no need to duplicate descriptions)
* use HttpResponseRedirect when the form is valid
<pre>
<code>
if form.is_valid():
        form.save()
        return HttpResponseRedirect('/reagent/')
</code>
</pre>
* render form error messages as described <a href="https://docs.djangoproject.com/en/1.9/topics/forms/">here</a> or use   <a href="https://github.com/dyve/django-bootstrap3"> django_bootstrap3</a> package as an alternative solution. django_bootstrap3 will take care of handling error messages on its own.

I was also wondering how to form a URL for a specific reagent record in the database and how to query it for the reagent_edit_delete template.

His suggestion was to:

* use the get_object_or_404 function in the view since it raises Http404 instead of the model’s DoesNotExist exception.
* user regular expressions to form the url for a specific record `r'^reagent/([0-9]+)/edit/$'`

Since I had trouble sharing my working directory using VMWare Player between my Ubuntu VM and Pinegrow that works on my master WIN10, Maksim suggested I give <a href="https://www.virtualbox.org/VirtualBox"> VirtualBox</a> a try.
