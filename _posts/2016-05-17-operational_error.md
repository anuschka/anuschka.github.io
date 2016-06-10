---
layout: post
title:  Django operational error
tags:
- Blog
- Post
---

After setting up my new development machine I had an operational error on the QCapp.

Login worked fine but when I browse to http://127.0.0.1:8000/portal/ it gives me OperationalError:

<pre>
<code>
no such table: qcapp_cellpanel

Request Method:  GET
Request URL:  http://127.0.0.1:8000/portal/
Django Version:  1.9.6
Exception Type:  OperationalError
Exception Value:  

no such table: qcapp_cellpanel

Exception Location:  /home/asustic/qcapp/venv/local/lib/python3.5/site-packages/django/db/backends/sqlite3/base.py in execute, line 323
Python Executable:  /home/asustic/qcapp/venv/bin/python
Python Version:  3.5.1
Python Path:  

['/home/asustic/qcapp/QCapp',
 '/home/asustic/qcapp/venv/lib/python35.zip',
 '/home/asustic/qcapp/venv/lib/python3.5',
 '/home/asustic/qcapp/venv/lib/python3.5/plat-x86_64-linux-gnu',
 '/home/asustic/qcapp/venv/lib/python3.5/lib-dynload',
 '/usr/lib/python3.5',
 '/usr/lib/python3.5/plat-x86_64-linux-gnu',
 '/home/asustic/qcapp/venv/local/lib/python3.5/site-packages',
 '/home/asustic/qcapp/venv/lib/python3.5/site-packages']

Server time:  Tue, 17 May 2016 17:36:40 +0200
</code>
</pre>

`python manage.py makemigrations` and `python manage.py migrate` did not help.

Maksim suggested I do `mv db.sqlite3 db.sqlite3.backup` and then `python manage.py migrate` and it worked!
