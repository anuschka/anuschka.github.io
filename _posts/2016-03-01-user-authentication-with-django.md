---
layout: post
title:  User Authentication With Django and deploying the app
tags:
- Blog
- Post
---
To get started I created a new Django project called ```qcapp```.
<pre>
<code>
python manage.py startapp qcapp
python manage.py migrate
</code>
</pre>

The migrate command looks at the INSTALLED_APPS in ```mysite/settings.py``` and creates any necessary database tables according to the database settings
 in your ```mysite/settings.py``` file and the database migrations shipped with the app.
To create a user who can login to the admin site run the following command: ```python manage.py createsuperuser```

Since I forgot the password for the superuser I had to change it with the following command: ```python manage.py changepassword admin```

To get me started with a basic Django view I followed this <a href="https://docs.djangoproject.com/en/1.9/intro/tutorial01/">tutorial</a>.

The idea was to create a home page that directs users to the web portal which is for authenticated users only. There is a login page, a logout page, and a basic web portal home page.

I used the following tutorial that clearly explained the <a href="https://www.rdegges.com/2010/user-authentication-with-django/">built in django authenticaiton</a>.

To deploy the app to github I returned to the well known <a href="http://tutorial.djangogirls.org/en/deploy/index.html">djangogirls tutorial</a>.

The simple Django site that (for now) demonstrates Django authentication is deployed <a href="https://github.com/anuschka/QCapp">here</a>. 
