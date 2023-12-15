# Tool Learning Log

Tool: Django

Project: **X**

---

10/27/23:
* To first start off, I used the [w3school DJango website](https://www.w3schools.com/django/)
* Before we start, we had to decide whether or not we wanted to make an app or website using Django. Ultimately, we chose that we wanted to make an app.
* Since DJango uses python, it was a challenge to learn something that I don't have any experience in using.

10/30/23:
* [Video Tutorial](https://www.youtube.com/watch?v=nGIg40xs9e4)
* Django is a powerful web framer for Python
* DJango is compatible with many different databases
* Has been used to build websites like instagram, spotify, and dropbox
* When in Python, use  `pip 20.2.3 from c:\python39\lib\site-packages\pip (python 3.9)` to download django into it
* `django-admin startproject projectName` - creates a project directory with files inside it
* `_init_.py` is a file that tells python to treat this directory like a python package
* `asgi.py` and `wsgi.py` does not need to be touched, let's DJango communicate with the webcircle.
* `settings.py` is a setting, will mostly go into to install different DJango applications, plugins, change some of the middleware, and modify the database engines
* `urls.py` use to help configure different URL routes that can be route or direct to different DJango applications
* `manage.py` acts like a command line tool that allows us to run special commands, do things like make database migrations, run our python server and all kinds of other things like creating users for our DJango admin panel

11/15/23:
* [Video tutorial](https://www.youtube.com/watch?v=rHux0gMZ3Eg&t=188s)
* very popular because can make a website in less time and less code
* dajango features:
   * admin site - manages data
   * Object-relational mapper (ORM) - abstracts the database so we can query or persist data without writing a lot of sql code
   * authentication - for identifying users
   * caching - for caching data and more

11/19/23:
* in views.py you can return a name input into the html.
```
def say_hello(request):
  return render(request, 'hello.html', {'name': 'Mosh'})
```
* render can be used to render a template and return the html markup to the client
* output:
```html
<h1>Hello {{ name }} </h1>
```
* can also use a if statement in html to make it say "Hello World" if there is no name
```html
{% if name %}
<h1>Hello {{ name }} </h1>
{% else %}
<h1>Hello World</h1>
{% endif %}
```
* Django can replace django default template engine with a preferred template engine
* use Django to build api to return data

12/12/23:
* [Python Django Tutorial: Full-Featured Web App Part 2 - Applications and Routes](https://www.youtube.com/watch?v=a48xeeo5Vnk&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=2)
* [Setting Django into Replit](https://docs.djangoproject.com/en/2.0/intro/tutorial01/)
* `python -m django --version` - used to check what version of django I have
* `django-admin startproject mysite` - a code used to establish a django project, a collection of instance of django, including database configuration, Django-specific options and application-specific settings.
* `python manage.py runserver` - use to see if the django project works.

12/14/23:
* `from django.shortcuts import render` - combines a template with a context dictionary and returns an HttpResponse object with the rendered text.
* `from django.http import HttpResponse` - uses request and response objects to pass state through the system.
```python
def home(request):
  return HttpResponse("<h1>Home</h1>")
```
* `def` = define
  * used to define a function or method
* `HttpRequest` - use to access a resource on the server
* `request` - a type of argument
  * Argument types specifies the type of argument the definition contains.
* `return HttpResponse("<h1>Home</h1>")` - a `HttpResponse` that says that we are on the home page

<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
