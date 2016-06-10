---
layout: post
title:  Reviewing Balsamiq wireframes
tags:
- Blog
- Post
---

During our weekly Skype meeting Maksim reviewed the <a href="../assets/QCApp.pdf"> wireframes</a> I created for the application in <a href="https://balsamiq.com/">Balsamiq</a>.

Maksim thought I did a good job with the wireframes and suggested I follow the <a href="https://en.wikipedia.org/wiki/Create,_read,_update_and_delete"> CRUD</a> approach when creating the frontend  and the backend for the app.

We decided it would be best to create all the URLs, views and templates for the reagent object:

* view all reagents
* enter a new reagent
* edit or delete a reagent


I setup the static files directory in settings.py

<pre>
<code>
STATIC_URL = '/static/'
STATICFILES_DIRS = (os.path.join(BASE_DIR, "static"),)
</code>
</pre>

and links for JavaScript, JQuery and CSS in the base.html:
```
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
```
```
<script type="text/javascript" src="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js"></script>
```

I already had Bootstrap included in my base.html and was ready to create my html-s (reagents.html and reagents_new.html) for the app following the design created in the <a href="../assets/QCApp.pdf"> wireframes</a>.
