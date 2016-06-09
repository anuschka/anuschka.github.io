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
* render form error messages as described <a href="https://docs.djangoproject.com/en/1.9/topics/forms/">here</a> or use  django_bootstrap3 as an alternative solution. django_bootstrap3
*
* Item 1
* Item 2
  * Item 2a
  * Item 2b
