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

12/16/23:
* `from django.urls import path` - makes it route urls to the appropriate view functions within a Django application using the url dispatcher
  * `include` - after `path`, is another type of function
* `urlpatterns` - a set of patterns that Django will try to match the requested URL to find the correct view
  * ```python
    urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('', views.home, name='blog-home'), 
    ] 
    ```
    * `path('admin/', admin.site.urls),` - the view that gets run when we go to /admin
    * `path('', views.home),` - tells Django the one that we want to handle that logic at that home page route
    * `name=blog-home` - is the name for the path
  * ```python
    path('mySite/', include('mySite.urls')),
    ```
    * when type in `/mySite`, will map to our blog folder and into the url file which would then map into the home view.
* `from . import views` - can input `views.py` into the `url.py` file
* back into the `django-project` file, go into their `url.py` file to tell Django which route should get mapped to our blog urls

1/8/24:
* [tips for Django](https://medium.com/analytics-vidhya/7-tips-and-more-to-ensure-a-successful-django-project-331a8d5746a3)
* [Django philosophies](https://docs.djangoproject.com/en/2.1/misc/design-philosophies/)
* [Django packages](https://djangopackages.org/)
* [Django Tutorial for custom user model](https://learndjango.com/tutorials/django-custom-user-model)
  * can help as a blueprint to save time and ensure some safety that the libraries have been tested by multiple Django developers.
* try to use the minimum amount of codes to make it easier to maintain and organize.

1/12/24:
* [Python Django Tutorial: Full-Featured Web App Part 3 - Templates](https://www.youtube.com/watch?v=qDwdMDQ8oX4&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=3)
* A way to create a html template and connect it to `views.py` to make a whole webpage
  * Create a whole new folder that stores all the html files
  * it is recommended to be able to add the application to the list, we first add the app configuration to the `settings.py` module
  * `apps.py` should have:
    * ```python
      class BlogConfig(AppConfig):
        name = 'blog'
      ```
      * `BlogConfig` inherits the `AppConfig` class
  * in `settings.py`, under the `INSTALLED_APPS` list, add `'blog.apps.BlogConfig',`
    * allows Django to correctly search the templates and for databases
    * where Django looks for our models

1/13/24:
* continuation of part 3:
  * `from django.shortcuts import render` is a shortcut that can help make a seemingly long code to make `HttpResponse` connect with a file into one piece of code
    * `return render(request, 'blog/home.html')`
      * `render()` takes the `request` object as it's first argument
      * second object for `render()` is the template name that we want to render
    * overall is a way to pass information into our template
  * to create a blog post:
    * inside `views.py` make a array list:
      * ```python
        posts = [
          {
            'author': 'Name1',
            'title': 'Blog Post 1',
            'content': 'first post content',
            'date_posted': '1/13/24',
          },
          {
            'author': 'Name2',
            'title': 'Blog Post 2',
            'content': 'second post content',
            'date_posted': '12/20/23',
          },
        ]
        ```
    * inside `def home(request):` create a dictionary:
      * ```python
        context = {
          'posts': posts
        }
        ```
    * inside `return render(request, 'blog/home.html')`, after `'blog/home.html'`, add the dictionary `context`
      * third argument that pass the data into the template and let us access it
    * inside the file to add the information from context:
      * ```html
        {% for post in posts %}
          <h1>{{ post.title }}</h1>
          <p>By {{ post.author }} on {{ post.date_posted }}</p>
          <p>{{ post.content }}</p>
        {% endfor %}
        ```
        * `{% for ... %}` is the `for` loop
        * `{% endfor %} ends the `for` loop
        * `{{ post.title }}` - goes throught the dictionary of `post` and grabs the one with the title
      * should print out something that would look like this in source code:
        * ```html
          <h1>Blog Post 1</h1>
          <p>By Name1 on 1/13/24</p>
          <p>first post content</p>

          <h1>Blog Post 2</h1>
          <p>By Name2 on 12/20/23</p>
          <p>second post content</p>
          ```
<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
