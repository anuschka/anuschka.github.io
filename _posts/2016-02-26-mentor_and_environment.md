---
layout: post
title:  Mentor and setup Python environment
tags:
- Blog
- Post
---
I got a mentor through <a href="http://www.huffingtonpost.com/jonha-revesencio/building-a-community-of-d_b_8279244.html">Kenan Salihbegovic</a>, Head of Community at Toptal.  Kenan got introduced to my current mentor, <a href="https://www.toptal.com/resume/maksim-sipos">Maksim Sipos</a>. He is extremely knowledgeable in Python (and many other languages and technologies) and a great communicator and I am very lucky to be working with him.

We discussed how I will approach my project and learn through doing it. Through the Toptal mentorship project I would like to build an application for
supporting a quality control process in a lab. I will use Python 3.0 and Django to do that.


Maksim suggested that I start my project with a first step that would consist of bulding a website with only one page with mandatory login. I would build it
locally usind the Django internal DB and then move it on git so that Maksim can look at the code.

On Ubuntu 14.04 Python 3.4 is installed by default.

<pre>
<code>
Python -V
returns Python 3.4.3
</code>
</pre>

I needed to setup virtualenv to run a django project.
In simple terms, virtualenv creates a folder that stores a private copy of python, pip, and other Python packages. You can then enable this private folder while working a project. By using the virtual environment, you can use different versions of Python and Python packages on a per project basis.

<pre>
<code>
sudo apt-get install python-pip
sudo pip install virtualenv
</code>
</pre>

I created a new directory for my project ```mkdir qcapp```

```virtualenv venv``` will create a folder in the current directory which will contain the Python executable files, and a copy of the pip library which you can use to install other packages. The name of the virtual environment (in my case, it was venv) can be anything; omitting the name will place the files in the current directory instead.

```Virtualenv –python=python3 venv``` creates a copy of Python in whichever directory you ran the command in, placing it in a folder named venv.

<p style="text-align:left"><img src="../assets/images/virtualenv.png" alt="virtualenv" /></p>

```source venv/bin/activate``` will activate the virtual environment. This is a good command to remember <i class="fa fa-thumbs-o-up"></i>

The (venv) before the prompt indicates that you are working in the virtual environment.
<p style="text-align:left"><img src="../assets/images/venvprompt.png" alt="venvprompt" /></p>

Python interactive interpreter will work when typing ```python``` at the command prompt. This is very useful for testing the code.

```Pip install django``` installed django 1.9.2 in the virtual environment.

```Sudo apt-get install ipython3``` installed ipython which, from what I understand, enchances the interactive python environment. The model ipython uses is called REPL, or Read-Eval-Print-Loop.

```ipython3``` opens the ipython interactive shell.
<pre>
<code>
Print ([x for x in range(4)])
</code>
</pre>
will output an array [0,1,2,3] in the ipython interactive shell.

To verify that Django can be seen by python type in the interactive shell:

<pre>
<code>
import django
print(django.get_version())
1.9.2
</code>
</pre>

With Python and Django environment setup I was ready to start a Django project. For that  I followed the <a href="https://docs.djangoproject.com/en/1.9/intro/tutorial01/"tutorial</a>.

This command created a django project ```django-admin startproject mysite```.
To verify that the django project really works run from the mysite project directory:
<pre>
<code>
python manage.py runserver
</code>
</pre>

The last command is also one to remember <i class="fa fa-thumbs-o-up"></i>
