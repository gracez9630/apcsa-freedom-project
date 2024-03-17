# Entry 4
##### 3/16/24

As of now, my partner and I have decided to use `ide.cs50.io` to create our freedom project. Currently, we only got down the templates in the codes and are still changing a few bits of it to match what we want. Though we haven't done much yet, we intend to continue by later on changing some of the codes in the templates with django and find a way to make a flashcard that keeps data that the user writes as the questions. My goal that I plan to do before the next blog entry is to make a login page that the user would be the one to first see when they open our website.

Besides that, I have been continuing to watch videos made by the same youtuber from the past blog entry. As of now, I have finished taking notes on [Python Django Tutorial: Full-Featured Web App Part 5 - Database and Migrations](https://www.youtube.com/watch?v=aHC3uTkT9r8&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=5) and just recently started watching [Python Django Tutorial: Full-Featured Web App Part 6 - User Registration](https://www.youtube.com/watch?v=q4jPR-M0TAQ&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=6).

Part 5 introduces database, which is a organized collection of structured informations. Django uses ORM (object relational mapper) that allows me to access our database and easy to use object oriented way and use different database without changing code. To create one, I would have to go to `models.py` to create a class that has it's own attributes. Two other codes that was introduced helped as `from django.utils import timezone` allows me to give me a date time that will take the timezone settings into considerations and `from django.contrib.auth.models import User` so that the `post` model, all the blogs posted, will have a relation with the `user` model as 1 user can have multiple posts. The finished product would look something like this:

```python
class Post(models.Model):
  title = models.CharField(max_length=100)
  context = models.textField()
  date_posted = models.DateTimeField(default=timezone.now)
  author = models.ForeignKey(User, on_delete=models.CASCADE)
```

In the `title` attribute, `.CharField(max_length=100)` or character field includes inside a specified restraint on the field in which has a restriction of a max length of 100. For `context`, the `.textField` has unrestricted texts, mostly for lines and lines of texts. `date_posted` features the code that `from django.utils import timezone` imports so that it shows the date posted to the current date time only when the object was created but also allows the to update the value of the date posted. In the `author` attribute, `on_delete=models.CASCADE` makes it so that it tells django if the user who created the post gets deleted, the post also gets deleted.

Migration is to move data or software from one location to another. It allows me allows us to change the database after it's created and have data in the database. By typing `python manage.py makemigrations` in the console, it gives me a `migration` directory that contains a file of informations of what it will do once the migrate command is runned. Also in console, by using `python manage.py shell`, it lets me be able to run python codes while still being in the console. While in shell, I would have to use the code `from blog.models import Post` to import the `post` model and `from django.contrib.auth.models import User` to import the `user` model. By using `User.objects.all()`, it returns a QuerySet of all the user that was made on `views.py` array. `User.objects.filter(username='TestName')` is used to grab all the users that have a name of "TestName" and by adding `.first()` to it, it will only grab the first user. Using `user = User.objects.filter(username='TestName').first()`, I can create a variable that holds information of the first user with the name "TestName". Similar to user, I can create a variable that holds the `post` model: `post = Post(title='blog 1', content='First Post Content!', author=user)`. By doing `post.save()`, I am able to save the variable into the database.

By going inside `models.py`, I can use a dunder STR method which lets me get the `post` object to be more descriptive by telling what we want to see when printed out. By doing so, if I were to go back into shell and use codes like `post.content`, it would output the title "First Post Content!". For this to work, I would have to write:

```python
def __str__(self):
  return self.title
```

By using `.modelname_set` in shell, I can get all of the post from a user. With it, I can essentially have a user get multiple post. `user.post_set.create(title='Blog 3', content='Third Post Content')` allows me to add a `post` object into a user and I don't have to use `.save()` to save it.

In `views.py`, I would have to import `from .models import Post` so that I can lets them run a query on the post model and pass in all of that data instead into the context. For this to work, inside the `def home(request):`, I would have to input:

```python
context = {
  'post': Post.objects.all()
}
```

I can also make it so that the models to show up on the admin page by going to `admins.py`, import `from .models import Post` and write `admin.site.register(Post)`. That way, I can also edit out the posts while being in the admin page.

From these times, I have used skills such as time management and collaboration each for different uses. For the skill time management, I was able to manage the times I spent watching part 5 so that I would not be overloaded with information. Since part 5 was one of the longer videos to watch, I had to make sure to pause in certain time frames and leave it for next time to watch it so I can obtain information much easily than I would if I were to watch it in one sitting. Collaboration was essential during my time working with the freedom project, as I needed to work together with them to assign certain things that we would each do. This is shown through our [MVP Plan](https://docs.google.com/document/d/1raf44sz5qGoUqUhA-P41l--Wilclcsa8TNu88fFAp2I/edit?usp=sharing) where we each have a set of stuff to do. Though there may be times where we do miss the deadline, we are able to collaborate with one another so that we can each do what we are responsible in this freedom project.

Before the next blog post, I aim to finish watching part 6 of the video and also with it create a login page for the freedom project. Since the video in part 6 is guiding me to create a login page, I believe that with it I will be able to accomplish this goal before the next blog post. As we continue working on our MVP, I will continue to gain more understanding about django through other people so that I can put what I have learned into the freedom project.

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
