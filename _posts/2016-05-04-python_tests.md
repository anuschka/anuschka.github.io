---
layout: post
title:  Python tests
tags:
- Blog
- Post
---

I continued writing tests in tests.py. This time I took advantage of the test client which is a Python class that acts as a dummy Web browser, allowing you to test your views and interact with your Django-powered application programmatically.

The idea was to test the portal view.

I wrote the ViewTest class in tests.py and was getting errors when running the test using <code>python manage.py tests</code> while the test was running fine in ipython terminal.

It turned out it is necessary to create the user every time you create a test since the database for each test starts fresh (basically the test class does not know that you created that user in a previous test subclass).

Adding:

<pre>
<code>user = User.objects.create_user('drwho', 'drwho@email.com', 'password')
profile = UserProfile.objects.create(user=user, roles='A')
</code>
</pre>

in each test subclass solved the problem.
