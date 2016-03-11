---
layout: post
title:  Models and tests in Django
tags:
- Blog
- Post
---
We discussed <a href="https://docs.djangoproject.com/en/1.9/topics/db/models/">Models</a> and <a href="https://docs.djangoproject.com/en/1.9/topics/db/models/">testing</a> in Django over our, at this point, regular Skype session with Maksim.

During our conversation I discovered <a href="https://www.linuxmint.com/">Linux MINT</a> would be something to try for development Desktop OS.

Django testing is an excellent way to test models and views in Django. I wrote a few RequestFactory and Client tests in ```qcapp/tests.py```.

RequestFactory and <a href="https://docs.djangoproject.com/en/1.8/topics/testing/tools/#the-test-client">Client</a> have some very different use-cases. To put it in a single sentence: RequestFactory returns a request, while Client returns a response.
The RequestFactory does what it says - it's a factory to create request objects. Nothing more, nothing less.
The Client is used to fake a complete request-response cycle. It will create a request object, which it then passes through a WSGI handler. This handler resolves the url, calls the appropriate middleware, and runs the view. It then returns the response object. It has the added benefit that it gathers a lot of extra data on the response object that is extremely useful for testing.
The RequestFactory doesn't actually touch any of your code, but the request object can be used to test parts of your code that require a valid request. The Client runs your views, so in order to test your views, you need to use the Client and inspect the response.

This behavior is best noted in the code below where RequestFactory for AnonymousUser returns a redirect (302) while Client returns a page not found (404)
 when accessing a ```/qcapp/```, a view that does not exist in the app.

<pre>
<code>
def test_our_view(self):
      factory = RequestFactory()

      # Create an instance of a GET request.
      request = factory.get('/qcapp/')

      # Or you can simulate an anonymous user by setting request.user to
      # an AnonymousUser instance.
      request.user = AnonymousUser()

      # Test my_view() as if it were deployed at /customer/details
      response = index(request)
      print(response)

      # Test the response status code here, verify it is a redirect
      print(response.status_code)
      self.assertEqual(response.status_code, 302)

  def setUp(self):
      # Every test needs a client.
      self.client = Client()

  def test_with_client(self):
      # Issue a GET request. Making a GET request to the same directory as above /qcapp/
      response = self.client.get('/qcapp/')

      # Check that the response is 404 instead of 302 since the view /qcapp/ does not exist.
      self.assertEqual(response.status_code, 404)
</code>
</pre>

I also noted (through Skye share desktop session with Maksim) that I can configure my <a href="https://atom.io/"">ATOM</a> better.

Configure ATOM-> Packages → Settings View → and then follow this <a href="http://www.marinamele.com/install-and-configure-atom-editor-for-python">tutorial</a>.

The atom packages I added ```linter``` and ```linter-flake8``` follow PEP8 standard for python code -- <a href="https://www.python.org/dev/peps/pep-0008/Style"> Guide for Python Code.</a>

My code was checked against PEP8 and several ```docstring error message D100 Missing docstring in public module``` appeared.

Following the Django docs <a href="https://docs.djangoproject.com/en/1.9/intro/tutorial02/">tutrial</a> I added my SimpleItem model from ```qcapp/models.py``` to
the Django Admin.

By adding the following code in the ```qcapp/admin.py``` Django knows to display SimpleItem in the Django admin index page.
<pre>
<code>
from .models import SimpleItem
admin.site.register(SimpleItem)
</code>
</pre>
