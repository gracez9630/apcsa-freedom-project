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

1/16/24:
* continuation of part 3:
  * `'posts'` variable inside `def home(request):` in `views.py` becomes accessible inside the template/file
    * lets the template/file to have access to the `post` array
  * using if:
    * ```python
      {% if title %}
      <title>Django Blog - {{ title }}</title>
      {% else %}
      <title>Django Blog</title>
      {% endif %}
      ```
      * `{% if title %}` - is the `if` statement: asks if the `context` data have a title
        * if so it outputs the title that the `context` have at where `{{ title }}` is at
      * `{% else %} - if the `if` statement becomes false, it goes to this and prints out the other title
        * if there is no title then it will just print out "Django Blog" with no `context` title
      * `{% endif %} - ends the `if` statement
    * in `views.py`, inside `return render(request, 'blog.about/html')`, after `'blog.about/html'` put `{'title': 'About'}` to reach the `title` directory and output `About` on the title.
      * `return render(request, 'blog.about/html', {'title': 'About'})`
      * html -  `<title>Django Blog - About</title>

1/18/24:
* continuation of part 3:
  * `{% block content %}{% endblock %}` - a section where child templates can override
    * inside `base.html` 
    * by getting rid of all the tags except the ones that made it unique and using `block`, it can allow coders to use less code than necesarry
      * `home.html`:
        * ```html
          {% extends "blog/base.html" %}
          {% block content %}
            {% for post in posts %}
              <h1>{{ post.title }}</h1>
              <p>By {{ post.author }} on {{ post.date_posted }}</p>
              <p>{{ post.content }}</p>
            {% endfor %}
          {% endblock content %}
          ```
          * `{% extends "blog/base.html" %} - allows it to use the `base.html` template by extending it
          * does not need the `content` in `{% endblock content %}` but is used to keep in check of each `block` section
      * when previewing to the `home.html` site, would still have the same output as how it was before but with less code
      * if it were to add a tool like bootstrap into `base.html` template and add a `div` over `block`, the other templates that extends to `base.html` template also gets bootstrap
  * `{% load static %}` - lets us load in a `css` file from the `static` directory
    * `<link rel="stylesheet" type="text/css" href="{% static 'blog/main.css' %}">`
      * `static` generates an absolute URL of the `static` file and access the `blog/main.css`
  * `<a class="nav-item nav-link" href="{% url 'blog-home' %}">Home</a>`
    * `{% url 'blog-home' %}` - would go to the `urls.py` where it would get the name of the home url pattern
      * `base.html` --> `urls.py` - finds `blog-home` --> `home.html`

1/20/24:
* [Python Django Tutorial: Full-Featured Web App Part 4 - Admin Page](https://www.youtube.com/watch?v=1PkNiYlkkjo&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=4)
  * admin page is to see is on your site and also a nice GUI (Graphical User Interface) for creating, updating, or deleting that data
  * your site and then "/admin" to enter the login page for your admin
  * create a admin user:
    * `python manage.py createsuperuser`
      * won't work if it's just by itself because there haven't been a database created for the supposed project yet
      * first: `python manage.py makemigrations`
        * detects teh changes and prepared Django to update the database
        * but doesn't actually run those changes yet
      * `python manage.py migrate`
    * `makemigrations` --> `migrate` --> `createsuperuser`
  * after that would ask for a username, email address, and password for the admin site
  * `python manage.py runserver`
    * runs the actual server/site of the project
  * once logged in, brings you to the default admin site
  * on the "user", can create another one and give them different permissions to have
    * "staff status" - be able to log in to the admin site
    * "superuser status" - allows them to have all of the permissions

2/29/24:
* [Python Django Tutorial: Full-Featured Web App Part 5 - Database and Migrations](https://www.youtube.com/watch?v=aHC3uTkT9r8&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=5)
  * ORM - object relational mapper
    * allows us to access our database and easy to use object oriented way
    * use different database without changing code
  * django ORM allows us to represent our database structure as classes called models
  * `models.py`
    * `class Post(models.Model):`
      * each class will have be it's own table in the database
      * create attribute
        * each attricute will be a different field in the database
        * `title = models.CharField(max_length=100)`
          * a character field
          * inside is used to specify restraints on the field
            * a title that will be a field of our post table in the database
            * title field will be a character field that has a restriction of a max length of 100
        * `context = models.textField()`
          * a text field
            * unrestricted text
          * possibly be lines and lines of texts
        * `date_posted = models.DateTimeField()`
          * a date/time field
          * inside could have `auto_now=True`
            * makes it so it would update the date posted to the current date time every time the post was updated
          * inside could have `auto_now_add=True`
            * set the date posted to the current date time only when the object was created
            * will not allow to update the value of the date posted
  * `from django.utils import timezone`
      * a date time that will take the timezone settings into considerations
        * `date_posted = models.DateTimeField(default=timezone.now)`
          * same as `auto_now_add=True`
          * but also allows the to update the value of the date posted
  * `from django.contrib.auth.models import User`
    * seperate table
    * post model and user model will have a relation
      * called a one-to-many relationship
      * because one user can have multiple post but a post can only have one author/user
    * `author = models.ForeignKey(User, on_delete)
      * `on_delete` is needed to tell django is the user who created the post gets deleted
      * `on_delete=models.CASCADE`
        * tells django is the user who created the post gets deleted to also delete their post

3/2/24:
* continuation of [part 5](https://www.youtube.com/watch?v=aHC3uTkT9r8&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=5)
  * need to run migrations to update the database
    * in the console:
      * `python manage.py makemigrations`
        * inside the `migration` directory, a file would be created by the migration runned on console
        * file contains a lot of information of what it will do once the migrate command is runned
      * `python manage.py migrate`
        * runs the migration for the database to update
    * migrations is useful
      * allows us to change our database after it's created and has data in the database
  * `python manage.py shell` <-- in console
    * allows us to run python codes inside console
    * work with our django objects
      * `from blog.models import Post`
        * imports the post
      * `User.objects.all()`
        * returns a QuerySet
        * returns both of the users that was created at part 3, the array post
      * `User.objects.first()`
        * only returns the first one in the array post that was created at part 3
      * `User.objects.filter(username='TestName')`
        * `<QuerySet [<User: TestName>]>`
        * filter by a field
        * only has one user since the usernames are unique
        * `User.objects.filter(username='TestName').first()`
          * `<User: TestName>`
          * only gets the first user without the QuerySet
          * `user = User.objects.filter(username='TestName').first()`
            * captures the user inside the `user` variable
            * can see the attributes inside the user
            * `user.id`
              * sees the id of the user inside the `user` variable
            * `user.pk`
              * PK = primary key
              * same thing as id
          * `user = User.objects.get(id=1)`
            * gets a user that has a id of 1 into the `user` variable

3/5/24:
* continuation of [part 5](https://www.youtube.com/watch?v=aHC3uTkT9r8&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=5)
  * console:
    * `post.objects.all()`
      * shows the QuerySet
      * if has one, shows:
        * `<QuerySet [<Post: Post object (1)>]>`
    * `post_1 = Post(title='blog 1', content='first post', author=user)`
      * what would show inside the QuerySet
      * no date because have a default date
    * `post_1.save()`
      * saves it into the database

3/9/24:
* continuation of [part 5](https://www.youtube.com/watch?v=aHC3uTkT9r8&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=5)
  * `models.py`:
    * dunder STR method
      * to get the `post` object to be more descriptive by telling what we want to see when printed out
      * also called magic method or special methods
      * dunder = double _ (underscore)
        * ```python
          def __str__(self):
            return self.title
          ```
  * console:
    * `exit()`
      * exits shell
      * by exiting shell, lose user variable
    * `python manage.py shell`
      * runs python shell command
    * import post (3/2/24)
      * `from django.contrib.auth.models import User`
        * imports user model
      * `post.object.all()`
        * ouputs: `<QuerySet [<Post: Blog 1>]>`
        * shows the `return self.title` in console
    * `post = Post.objects.first()`
      * able to access all of the fields of the first post
      * `post.content`
        * outputs: `'First Post Content!'`
      * `post.author`
        * output: `<User: CoreyMS>`
        * returns user object or the entire user object
        * can access the user objects attributes
        * `post.author.email`
          * outputs the user's email

3/10/24:
* continuation of [part 5](https://www.youtube.com/watch?v=aHC3uTkT9r8&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=5)
  * console/shell:
    * `.modelname_set`
      * can get all of the post from the user
      * example: `user.post_set.all()`
        * shows QuerySet of all the post the user creates
      * `user.post_set.create(title='Blog 3', content='Third Post Content')`
        * creates another post with same user
        * doesn't need `author` as django knows that the post is for that user
        * don't need to run `.save()`
  * `views.py`:
    * `from .models import Post`
      * lets them run a query on the post model and pass in all of that data instead into the context
    * inside `def home(request):`
      * ```python
        context = {
          'post': Post.objects.all()
        }
        ```
      * query all the posts from the database like the command line/shell
      * when previewed, should have the data that was made in shell
  * templates --> blog --> `home.html`
    * [Django Date Filters](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#date)
    * `{{ post.date_posted|date:"F d, Y" }}`
      * `date:"F d, Y"` makes it so that it filters the date posted on the server to show the full month, the day, and the year
  * admin panel:
    * `admin.py`:
      * registers model to show up on the admin page
      * import model: `from .models import Post`
      * `admin.site.register(Post)`
        * in admin page would show the `Post` object
    * at the admin page can edit out the blog posts 

3/13/24:
* [Python Django Tutorial: Full-Featured Web App Part 6 - User Registration](https://www.youtube.com/watch?v=q4jPR-M0TAQ&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=6)
  * create a user registration page
  * create account, log in, and make post
  * create new app:
    * `python manage.py startapp users`
      * `project` folder to `settings.py`:
        * in the `INSTALLED_APPS` array, add `'users.app.UserConfig',`
      * in `user` folder to `views.py`:
        * `from django.contrib.auth.forms import UserCreationForm`
          * imports a user creation form that is given from django to make it easier for me to make the register
        * ```python
          def register(request):
            form = UserCreationForm()
          return render(request, 'user/register.html', {'form': form})
          ```
          * `{'form': form}` is the dictionary that is the context of the template

3/17/24:
* Continuation of [Part 6](https://www.youtube.com/watch?v=q4jPR-M0TAQ&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=6)
  * `register.html`:
    * `{% extends "blog/base.html" %}
      * can get information from the `base.html`
      * ```html
        {% extends "blog/base.html %}
          {% block content %}
            <div class="content-section">
              <form method="POST">
                {% csrf_token %}
                <fieldset class="form-group">
                  <legend class="border-bottom mb-4">Join Today</legend>
                  {{ form }}
                </fieldset>
                <div class="form-group>
                  <button class="btn btn-outline-info" type="submit">Sign up</button>
                </div>
              </form>
              <div class="border-top pt-3">
                <small class="text-muted">
                  Already Have An Account?
                  <a class="ml-2"href="#">Sign In</a>
                </small>
              </div>
            </div>
          {% endblock content %}
        ```
        * CSRF Token (`{% csrf_token %}`):
          * a cross-site request forgery token
          * a hidden tag
          * protects form against certain attacks (added security)
          * without it the form will not work
        * fieldset tag (`<fieldset>`):
          * used to group related elements in a form
        * `<legend>`:
          * used to add a caption to a group of related form `<input>` elements that have been grouped together into a `<fieldset>`.
        * `{{ form }}`:
          * prints out form
          * access that `form` variable added on context
          * displays all of the form labels and fields
  * project's `urls.py`:
    * `from users import views as user_views`
    * inside `urlpatterns`:
      * `path('register/', user_views.register, name='register'),`

3/23/24:
* Continuation of [Part 6](https://www.youtube.com/watch?v=q4jPR-M0TAQ&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=6)
  * `register.html` :
    * `{{ form.as_p }}`
      * render the forms in paragraph class
  * `views.py`:
    * to validate the post request
    * ```python
        if request.method == 'POST':
          form = UserCreationForm(request.POST)
        else:
          form = UserCreationForm()
      ```
      * if we get a post request, it will instantiate a user creation form with that post data
      * else it instantiates a empty form
      * inside `if` statement:
        * ```python
            if form.is_valid():
              username = form.cleaned_data.get('username')
          ```
          * `form.is_valid()` tells us if the form is valid when it is submitted
          * `username = form.cleaned_data.get('username')`:
            * validated form data will be in `cleaned_data` which will have nicely converted into python taught types for us from the form
    * `from django.contrib import messages`
      * can import a flash message which lets me send one-time alerts to a template that will only be displayed once and will disappear on the next request
      * types of messages:
        * `messages.debug`
        * `messages.info`
        * `messages.success`
        * `messages.warning`
        * `messages.error`
      * inside `if form.is_valid():`
        * `messages.success(request, f'Account created for {username}!')
    * to make it so the register can redirect to the home page:
      * edit `from django.shortcuts import render` to `from django.shortcuts import render, redirect`
      * inside `if form.is_valid():`
        * `return redirect('blog-home')
          * when registered, should bring them to the home page

3/30/24:
* Continuation of [Part 6](https://www.youtube.com/watch?v=q4jPR-M0TAQ&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=6)
  * flash messages:
    * `html`:
      * ```html
          {% if messages %}
            {% for message in messages %}
              <div class="alert alert-{{  message.tags }}">
                {{ message }}
              </div>
            {% endfor %}
          {% endif %}
        ```
        * `{{  message.tags }}` - can grab the tag from the `messages` in `views.py`
        * flash messages are one time alert, so it will only appeared once when a user logged in and will disappear when the user reload.
  * invalid forms:
    * `views.py`:
      * if `form.is_valid()` becomes false, it goes to `return render(request, 'user/register.html', {'form': form})`
        * since there is no form, it will provide a error, or tells them that it is invalid
  * saving created forms:
    * inside `if form.is_valid():`
      * `form.save()`
        *  saves the created user
    * can go into admin page to check for newly created users

3/31/24:
* Continuation of [Part 6](https://www.youtube.com/watch?v=q4jPR-M0TAQ&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=6)
  * create a new form to add a new field like emails
  * new form will inherit from the user creation form
  * create new file `forms.py`:
    * `from django import forms`
      * improts forms
    * `from django.contrib.auth.models import User`
      * imports user model
    * `from django.contrib.auth.forms import UserCreationForm`
      * import user creation form
    * ```python
      class UserRegisterForm(UserCreationForm):
        email = forms.EmailField():

        class Meta:
          model = User
          fields = ['username', 'email', 'password1', 'password2']
      ```
      * `Meta` gives us a nested name space for configuations and keeps the configurations in one place
      * the configuration is saying that the model that will be affected is the user model
      * so when `form.save()`, it will save the user model
      * fields are what we want in the form and in what order
  * `views.py`
    * `from .forms import UserRegisterForm`
      * inherits the stuff from `UserRegisterForm`
      * replace both `UserCreationForm` with `UserRegisterForm`
      * since we are not using `UserCreationForm` anymore, we can get rid of `from django.contrib.auth.forms import UserCreationForm`

4/6/24:
* Continuation of [Part 6](https://www.youtube.com/watch?v=q4jPR-M0TAQ&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=6)
  * crispy forms
    * allow us to put some simple tags in our template that will style the form in a bootstrap fashion
    * terminal:
      * `pip install django-crispy-forms`
        * installs crispy form
    * `settings.py`:
      * inside `INSTALLED_APPS`
        * `'crispy_forms',
        * very bottom
        * ```python
          CRISPY_TEMPLATE_PACK = 'bootstrap4'
          ```
        * changes the crispy form to have bootstrap 4
    * `login.html`:
      * `{% load crispy_form_tags %}
        * allows me to use crispy filter
      * change `{{ form.as_p }}` into `{{ form|crispy }}`

4/7/24:
* [Python Django Tutorial: Full-Featured Web App Part 7 - Login and Logout System](https://www.youtube.com/watch?v=-JeobI-87Dc)
  * `project/urls.py`:
    * `from django . contrib.auth import views as auth_views`
      * import views as "auth_views"
    * `path('login/', auth_views.LoginView.as_view(), name='login'),`
    * `path('logout/', auth_views.LogoutView.as_view(), name='logout'),`
      * `LoginView` and `LogoutView` are class based views
      * built in views, django will handle it
      * will not handle the templates
      * inside `as_view()`:
        * template_name='users/login.html'
    * django errors are important
      * point us in the direction in what changes we need to make to get it to work

<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
