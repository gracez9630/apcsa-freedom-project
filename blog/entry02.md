# Entry 2
##### 12/17/23

Since deciding to choose to learn Django, there were many challenges that were needed to be overcomed. For instance, to use the tool Django, I had to first learn about Python. That meant that I had to spend a couple of hours first learning the basics of Python before I get into Django just so I could fully understand what it may be saying. I used the video [Python for Beginners - Learn Python in 1 Hour](https://www.youtube.com/watch?v=kqtD5dpn9C8) to get a quick guide on Python just so I can get a grasp of what I need to do.

Afterwards, I had decided on finding multiple different sites and videos that may help me in learning Django in hopes that it could teach me what I can do to implement the tool into my freedom project. Some sites include:

* [Python Django Tutorial: Full-Featured Web App Part 2 - Applications and Routes](https://www.youtube.com/watch?v=a48xeeo5Vnk&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=2)
* [Setting Django into Replit](https://docs.djangoproject.com/en/2.0/intro/tutorial01/)
* [w3school DJango website](https://www.w3schools.com/django/)
* [Learn Django in 20 Minutes!!](https://www.youtube.com/watch?v=nGIg40xs9e4)
* [Python Django Tutorial for Beginners](https://www.youtube.com/watch?v=rHux0gMZ3Eg&t=188s)

When learning my tool, I made sure to atleast learn one section of my tool one at a time. By doing this, I intend to slowly learn more about Django step by step and how I can implement it into my freedom project. For the recent week, I made sure to study on how to route urls to appropriate view functions within a Django application using the url dispatcher. By doing so, I can be able to use Django to make a clean, elegant url scheme like a high-quality web application.

Firstly, there would be 2 different folders, the `django-project` folder where it stores data and would be used to map into the second folder, being the `mySite` folder. Inside the `mySite` folder and into the file `views.py`, I would have to import 2 specific Django applications. The `from django.shortcuts import render` combines a template with a context dictionary and returns an HttpResponse object with the rendered text while the `from django.http import HttpResponses` uses request and response objects to pass state through the system. After that below, I would define a function, and inside it would return a `HttpReponse` to be seen in the home site, indicating that it is on the home page. The outcome would look something like this:

```python
from django.shortcuts import render
from django.http import HttpResponses

def home(request):
  return HttpResponse("<h1>Home</h1>")
```

The `def` helps me define the `home`, with the `request` being a type of argument. By returning the `HttpResponse`, when I were to ever enter the home page, I would see the first header "Home" in it.

From then, I would head into the `urls.py` file inside the `mySite` folder, where I can use it to map into the `views.py` folder. The 2 imports this time is `from django.urls import path` to make it route urls to the appropriate view functions and `from . import views` which can let me input `views.py` into `urls.py`. Afterwards, I would make a `urlpatterns` which lets me match the requested URL to find the correct view. Inside it would be the `path`, being `path('', views.home),` which would tell Django the one that we want to handle that logic at that home page route. With it, the `urls.py` would be able to route all the way to `views.py`. The end result would look like this:

```python
from django.urls import path
from . import views

urlpatterns = [ 
path('', views.home, name='blog-home'), 
] 
```

Lastly, I would enter the `django-project` folder instead and into it's own `urls.py` file, to map it into the `mySite` `urls.py` file and finally into the `views.py` file. While I would also include `from django.urls import path` into the `urls.py` file, I would add onto it with `include`, being another type of function. And instead of writing the same `urlpatterns`, I would instead in the beginning, write `'mySite/' instead of keeping it blank. This names the url of what it would be, and by using `include`, it would map into the `mySite` `urls.py` file. Inside that file, it would be:

```python
from django.urls import path, include

urlpatterns = [ 
path('admin/', admin.site.urls), 
path('mySite/', include('mySite.urls')),
] 
```

During these weeks, I made sure to use skills like "How to Google" and "Embracing Failure" while learning Django. "How to Google" was very helpful as there were times in videos where they may have used a code I may not have known, and by googling it I would be able to gain a understanding of how and why I may need it for future codings. "Embracing Failure" made it so even if I was struggling a few times and realizing some errors that I made, especially when it come to making my `mySite` folder, I would learn from that mistake and try to adapt to it while learning about the mistakes that I've made. With the many different sites and videos, I have been learning django by trying pieces of it in replit. Since to learn a thing I would have to first know how it may be used, I tried to practice a bit during the days.

[Replit image](img/capture.PNG)

During the winter break, my goal would be continuing to watch the rest of the parts from [Python Django Tutorial: Full-Featured Web App Part 2 - Applications and Routes](https://www.youtube.com/watch?v=a48xeeo5Vnk&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=2) since it was a very helpful guide to me. With it, I intend to take as much notes as I can about it and to see if there are any useful methods I may be able to use into my freedom project.


[Previous](entry01.md) | [Next](entry03.md)

[Home](../README.md)
