# Entry 5
##### 5/5/24

While I did finish watching [Python Django Tutorial: Full-Featured Web App Part 6 - User Registration](https://www.youtube.com/watch?v=q4jPR-M0TAQ&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=6), majority of my time was to complete the freedom project. Since there was at least a month away from the due date, Vivian and I put most of our efforts to completing it.

Part 6 was a very important video that was essential for the freedom project and helped me learn more about my tool. It is the introduction to user registration, which allows me to create login webpages for people to sign into our site. It introduces me a lot of codes that django has such as `from django.contrib.auth.forms import UserCreationForm` which lets me import a user creation form that is given from django to make it easier for me to make the register. With this, I was able to start my journey on creating a login, logout, and signup form for our freedom project.

While in the development part of our project, we had done many testings regarding where we wanted to create our freedom project on. Originally, we wanted to make it on replit since it already had it's own django installed. Later on, Vivian exclaimed that she was recommended to use code.cs50 instead. After a bit of testing on both replit and code.cs50, we ultimately decided that our finished project would be on code.cs50. For the reason why, for some reason the codes I was using for django did not work on replit for some reason, but when it was written on code.cs50, it worked well so we decided to choose that in the end.

Vivian focused more on creating the html where the flashcard of our project would work. She made it so that you can add as many of them as you want, and have it conceal the answer to the question until it is clicked on to reveal. With it, we technically have done what we intended the project to do and now needed to implement the tool with it.

I focused more on our tool django as I was the one more comfortable with it while Vivian had some trouble understanding it. I fiddled around with the codes a bit to try and figure out how I can use django to my advantage while using the "Python Django Tutorial" I was so used to. There were two specific files that I have used often during that time, being `urls.py` and `settings.py`. `urls.py` allows me to route through the html, allowing me to make it so that I can make the login html go to the home html.

```python
from django.contrib import admin
from django.urls import path, include
from django.views.generic.base import TemplateView

urlpatterns = [
    path("admin/", admin.site.urls),
    path("accounts/", include("accounts.urls")),
    path("accounts/", include("django.contrib.auth.urls")),
    path("", TemplateView.as_view(template_name="home.html"), name="home"),
]
```

The codes with the `from` allows me to import things that django already provides, like the `from django.urls import path, include` allows me to import paths that leads to the html page. The `path("", TemplateView.as_view(template_name="home.html"), name="home"),` makes it so that the moment someone would see the preview, the first page they would see if the home page, which is where the flashcards would be.

In `settings.py`, I am able to make it so that I could redirect both the login and logout pages into the home page. By using the code `LOGIN_REDIRECT_URL = "home"` inside `settings.py`, it tells django that once the user were to login, they would be directed into the home page.

With the code `path("accounts/", include("django.contrib.auth.urls")),`, django is able to provide me with login templates that I am able to use, while using the minimum amount of code that I can for html. The end result would look like this:

```html
{% extends "base.html" %}

{% block title %}Login{% endblock %}

{% block content %}
<h2>Log In</h2>
<form method="post">
  {% csrf_token %}
  {{ form }}
  <button type="submit">Log In</button>
</form>
<form action="{% url 'signup' %}" method="post">
  {% csrf_token %}
  <button type="submit">Signup</button>
</form>
{% endblock %}
```

The `{{ form }}` would output a login form that django has for me to use, which makes it so that when done correctly, it would automatically bring the user to the home page. The form for the sign up was something I personally made by using `<form action="{% url 'signup' %}" method="post">` so that it would bring the user to the sign up form in case they have not created a account.

When making the home page, I used the codes Vivian made for the flashcard, and included some things that django provided. For example, the code `{% if user.is_authenticated %}` is used so that it tells the computer that if the user was authenticated and could log in to the home page, then it would show the flashcard page. If the user is not logged in, then it would show the page that would direct them to the login form instead.

One thing that posed some trouble was making the `css` and `js` files work so that the flashcard page is fully functional. Inside `settings.py`, I would need to input:

```python
STATICFILES_DIRS = [
    "static",
]
```

This tells django that inside the `static` folder, there would be additional static files besides the ones that came with the django app installed. By inputting `{% load static %}` at the very top of the page at the home html, I would just have to route some codes to target the `css` and `js` files inside the `static` folder and then it would fully work.

From this duration, I had used the skills of communication and attention to detail. Since Vivian and I are partners, we usually spend our time communicating on what we want to do and the progress we are currently at. Knowing what the other is doing and being able to communicate to work together to solve a problem was very important in this project, as without it we may not know what we may be doing. Attention to detail is very important when dealing with django. Since django was a tool that is used on python which I am not familiar with, I would need to put a great deal in noticing any details that so that I could properly use django correctly. I needed this skill to be able to notice any small detail of errors as since I am both unfamiliar with django and python, I have to be extra careful on what I am coding so that there will be no errors.

Overall this freedom project was a stressfull project for both me and Vivian to do. Though there were many things we wanted to implement, we believed that it was best if we were to first complete the bare minimum of what is required. Overall, this project was something that we had some difficulties with since it was the use of django and python, both being something that we were not familiar with. In the beginning it was a rough time as django was incredibly confusing for the both of us, and now I believe that I was only able to reach the surface level of understanding of our tool. Though there may be some things we may want to add more into, I believe that we are both satisfied with what we have made.

[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
