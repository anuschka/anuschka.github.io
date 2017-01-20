---
layout: post
title:  Django_bootstrap3, using absolute paths and password reset
tags:
- Blog
- Post
---

On our Skype meeting Maksim and I discussed Django_bootstrap3 template tags. So far
I used <b>bootstrap_form</b>. Beside this one Maksim pointed out django_fields when I
want to organize fields in different columns. Widgets and pagination also work well
with Django_bootstrap3.

Maksim also showed me how bootstrap-messages work. These are so called flash messages.

This is how to use them on the <a href="https://docs.djangoproject.com/en/1.10/ref/contrib/messages/#using-messages-in-views-and-templates">
Django side</a>.

This is how <a href="https://django-bootstrap3.readthedocs.io/en/latest/templatetags.html#bootstrap-messages">
it is done in bootstrap</a>.

Maksim suggested I use absolute paths in views and in general (ex. qcapp.views).

We also briefly talked about <a href="http://www.django-rest-framework.org/"> Rest Django framework</a>.

At the end of our Skype session we discussed how to solve password reset for the application.

--------------
password reset:

VIEW /password/forgotten/

  email:  __something@domain.com_______________  [SUBMIT]


Sends email:


    Go here:

       /reset/password/327893718937897198798fsf89028930/


VIEW /reset/password/([a-z]+)/

- is the parameter valid
- if it is, login user and redirect to "change password" form
- if it is not, redirect user outside the app


--------------------------

For tokens use:

django.contrib.auth.tokens.PasswordResetTokenGenerator
