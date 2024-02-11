# Entry 3
##### 2/5/24

Since the last blog entry, I continued to watch the Python Django Tutorial, this time watching part 3 and 4. Also, I looked at other sites to find any tips about Django being:

* [tips for Django](https://medium.com/analytics-vidhya/7-tips-and-more-to-ensure-a-successful-django-project-331a8d5746a3)
* [Django philosophies](https://docs.djangoproject.com/en/2.1/misc/design-philosophies/)
* [Django packages](https://djangopackages.org/)
* [Django Tutorial for custom user model](https://learndjango.com/tutorials/django-custom-user-model)

These helped to figure out some tips or small info when it comes to Django.

Still, the main focus that I put with was [Python Django Tutorial: Full-Featured Web App Part 3 - Templates](https://www.youtube.com/watch?v=qDwdMDQ8oX4&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=3) and [Python Django Tutorial: Full-Featured Web App Part 4 - Admin Page](https://www.youtube.com/watch?v=1PkNiYlkkjo&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=4) as they were both a continuation of part 2.

Part 3 was the introduction of templates. It lets me create html files and connect it to views.py to make a whole webpage. I would firstly create a html and add a app configuration in `settings.py` so that it allows django to search the templated and for database. The `apps.py` should have:

```python
class BlogConfig(AppConfig):
  name = 'blog'
```

This allows `BlogConfig` to inherit the `AppConfig` class and then inside the `settings.py` file in the `INSTALLED_APPS` array, add `'blog.apps.BlogConfig',` to get it working.

By using `django.shortcuts import reader`, it lets me make a shortcut to make a seemingly long code to make `HttpResponse` connect with a file in one piece of code: `return render(request, 'blog/home.html')`. With it, it lets me to pass information into our template.

An example for that is a blog post. Inside `views.py`, I can make a array list and have it pass into the template file while still being in `views.py`. 

```python
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

By creating a dictionary inside `def home(request):` which would have the template file:

```python
context = {
  'posts': posts
}
```

This lets me be able to use the array list while in the html file. Codes like `{{ post.title }}` inside the html file lets me grab the array list with the `title` and output it into the template.

So, the code:

```html
{% for post in posts %}
  <h1>{{ post.title }}</h1>
  <p>By {{ post.author }} on {{ post.date_posted }}</p>
  <p>{{ post.content }}</p>
{% endfor %}
```

will be the same as:

```html
<h1>Blog Post 1</h1>
<p>By Name1 on 1/13/24</p>
<p>first post content</p>

<h1>Blog Post 2</h1>
<p>By Name2 on 12/20/23</p>
<p>second post content</p>
```

The video part 3 also introduces the code `{% block content %}{% endblock %}`, which is a section where child templates can override. By getting rid of all the code in the html file like the `<html>`, `<head>`, and `<body>` except the ones that made it unique and using `block`, it can allow coders to use less code than necesarry. So, the output would be:

```html
{% extends "blog/base.html" %}
{% block content %}
  {% for post in posts %}
    <h1>{{ post.title }}</h1>
    <p>By {{ post.author }} on {{ post.date_posted }}</p>
    <p>{{ post.content }}</p>
  {% endfor %}
{% endblock content %}
```

The `{% extends "blog/base.html" %}` allows it to use `base.html` template by extending it. Also, to load a `css` file from the `static` directory, I would have to use the code `{% load static %}`. `static` generates an absolute URL of the `static` file and access the `blog/main.css`.

This can be used as: `<a class="nav-item nav-link" href="{% url 'blog-home' %}">Home</a>`. The `{% url 'blog-home' %}` would go to the `urls.py` where it would get the name of the home url pattern. Essentially, it goes: `base.html` --> `urls.py` - finds `blog-home` --> `home.html`.

Part 4 was a shorter video, which introduces me to the admin page. With the admin page, it lets me to see my site and also a nice GUI (Graphical User Interface) for creating, updating, or deleting that data. The video first guided me to create a admin account to be able to access my admin page, and shown me a quick tour around what it contains. I can also add other user and either make them a "staff status" which lets them be able to log in to the admin site or a "superuser status" which allows them to have all of the permissions.

The skills that I've used for this time was "Attention to detail" and "Time Management". Since the part 3 video was a very long video, I had to manage my time so that I would not be overloaded with knowledge. With it, I try to seperate my time I spent with the video to learn bit by bit. First to spent a day learning about the html templates and then another day learning about the css templates. Attention to detail is also essential to this as I had to carefully analysis each code that the person introduced such as the `{% block content %}` while also making sure that I can understand what each of the code will do. If I were to just listen to the video without paying attention to what each code are used for, I may never understood what to do and instead just learn nothing at all.

After this, I intend to continue watching the next few parts of the video from the same youtuber, as they were a essential help in learning bits and pieces about django. As I continue with it, I hope to gain more extensive knowledge that can help benefit me on my freedom project.

[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
