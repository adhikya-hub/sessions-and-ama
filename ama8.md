# AMA

**1. Can Django modules be written in languages other than Python?**

No. Django models, views, and apps have to be Python — the framework is built around Python's object system. But you can still use other languages *around* Django:
- Run another program via `subprocess`
- Call a C/Rust library using `ctypes`
- Write a separate service in another language and talk to it over HTTP

The Django part itself stays Python though.

---

**2. What is WSGI?**

Short for **Web Server Gateway Interface**. It's a standard way for a web server (like Gunicorn) to talk to a Python web app (like Django). It's just a common "language" so any WSGI server can run any WSGI app. Django's `wsgi.py` file is what servers use to actually run your project.

---

**3. What is the use of inlines in Django admin?**

Inlines let you edit related objects on the same admin page as the main object, instead of opening a separate page for them.

Example: editing a movie's cast list directly on the Movie admin page, instead of going to a separate Credit admin page.

```python
class CreditInline(admin.TabularInline):
    model = Credit

class MovieAdmin(admin.ModelAdmin):
    inlines = [CreditInline]
```

---

**4. What is a document in Elasticsearch?**

A document is one unit of data in Elasticsearch — basically a JSON object. It's similar to a row in a normal database table, but more flexible (fields can vary between documents).

---

**5. What is a foreign key in Django?**

A field that links one model to another — a "many can point to one" relationship. Example: many movies can have the same director, so `Movie` has a `ForeignKey` to `Director`.

```python
class Movie(models.Model):
    director = models.ForeignKey(Person, on_delete=models.CASCADE)
```

---

**6. What is the use of `get_or_create()`?**

It tries to find an object matching what you give it. If found, it returns it. If not, it creates a new one. It returns two things: the object, and `True`/`False` for whether it was just created.

```python
rating, created = MovieRating.objects.get_or_create(user=user, movie=movie)
```

Saves you from writing a manual "check if it exists, else create it" block.

---

**7. What is context (in Django templates)?**

It's the data you send from your view to your template — a dictionary of variable names and values. The template uses this to show dynamic content.

```python
return render(request, "movie_detail.html", {"movie": movie})
```

In the template, `{{ movie.title }}` comes from this context.

---

**8. What is the use of the `@receiver` decorator?**

It connects a function to a signal — basically says "run this function when this event happens." It's a shortcut instead of manually calling `signal.connect()`.

```python
@receiver(post_save, sender=Movie)
def do_something(sender, instance, **kwargs):
    ...
```

This function now runs every time a `Movie` is saved.

---

**9. Difference between BaseSignalProcessor and RealTimeSignalProcessor**

(This is from `django-elasticsearch-dsl`, which keeps Elasticsearch in sync with your Django database.)

- **BaseSignalProcessor** — the basic blueprint. It knows *how* to update Elasticsearch when something changes, but doesn't connect itself to Django's save/delete events automatically. It's meant to be extended.
- **RealTimeSignalProcessor** — takes that blueprint and actually connects it to Django's save/delete signals, so Elasticsearch updates immediately, right when you save something.

The downside of "real time" is that it's synchronous — your request has to wait for Elasticsearch to update before finishing. That's why bigger projects often use a Celery-based version instead, which updates Elasticsearch in the background instead of making the user wait.

---

**10. What is the N+1 query problem, and how do you fix it?**

It happens when you fetch a list of N items, and then for each item you make a separate query to get related data — so instead of 1 query, you end up making N+1 queries total.

```python
movies = Movie.objects.all()      # 1 query
for movie in movies:
    print(movie.director.name)    # 1 more query, for EACH movie
```

**How to fix it:**
- `select_related("director")` — for one-to-one or foreign key relations. Joins the related table in the same query.
- `prefetch_related("credits")` — for many-to-many or reverse foreign key relations. Runs one extra query and combines the results in Python.

```python
movies = Movie.objects.select_related("director").prefetch_related("credits")
```

Now it's just 1–2 queries total, no matter how many movies there are.
