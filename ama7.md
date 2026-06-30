# AMA

## 1. What are Models in Django?

A **Model** is a Python class that represents a table in the database. Each attribute of the model represents a column, and each object of the model represents a row.

- Define database structure using Python.
- Django automatically creates SQL tables from models.
- Supports CRUD operations.
- Provides validation.
- Works seamlessly with the Django ORM.

---

## 2. What are Signals in Django?

Signals allow different parts of an application to communicate without being tightly coupled.

They are commonly used to perform actions automatically when certain events occur.

Common signals include:

- `pre_save`
- `post_save`
- `pre_delete`
- `post_delete`
- `m2m_changed`

Example:

```python
from django.db.models.signals import post_save
from django.dispatch import receiver
from .models import UserProfile

@receiver(post_save, sender=UserProfile)
def profile_created(sender, instance, created, **kwargs):
    if created:
        print("Profile created")
```

- Send welcome emails
- Create related objects automatically
- Log activities
- Update search indexes

---

## 3. How do Decorators help in Django?

Decorators modify the behavior of a function or class without changing its code.

Common Django decorators:

### Login Required

```python
from django.contrib.auth.decorators import login_required

@login_required
def dashboard(request):
    ...
```

Only authenticated users can access the view.

---

### Permission Required

```python
from django.contrib.auth.decorators import permission_required

@permission_required("movies.add_movie")
def add_movie(request):
    ...
```

Restricts access based on permissions.

---

### Require HTTP Method

```python
from django.views.decorators.http import require_POST

@require_POST
def delete_movie(request):
    ...
```

Allows only POST requests.

---

### CSRF Exempt

```python
from django.views.decorators.csrf import csrf_exempt

@csrf_exempt
def webhook(request):
    ...
```

Disables CSRF protection (use only when necessary).

---

## 4. What is the `humanize` template library?

`humanize` provides filters that make data easier to read.

Load it in a template:

```django
{% load humanize %}
```

Examples:

```django
{{ 1200|intcomma }}
```

Output:

```
1,200
```

```django
{{ 1500000|intword }}
```

Output:

```
1.5 million
```

```django
{{ movie.created_at|naturaltime }}
```

Output:

```
3 minutes ago
```

Common filters:

- `intcomma`
- `intword`
- `naturaltime`
- `naturalday`
- `ordinal`

---

## 5. What is the use of `reverse()`?

`reverse()` generates a URL from its URL pattern name.

Instead of hardcoding URLs:

```python
"/movies/5/"
```

Use:

```python
from django.urls import reverse

url = reverse("movie_detail", kwargs={"pk": 5})
```

- Avoid hardcoded URLs
- Easier maintenance
- URLs automatically update if patterns change

---

## 6. What is the `clean()` method in Django Forms?

The `clean()` method performs validation involving multiple fields.

Example:

```python
class SignupForm(forms.Form):
    password = forms.CharField()
    confirm_password = forms.CharField()

    def clean(self):
        cleaned_data = super().clean()

        if cleaned_data["password"] != cleaned_data["confirm_password"]:
            raise forms.ValidationError("Passwords do not match.")

        return cleaned_data
```

### Validation order

1. Field validation
2. `clean_<field>()`
3. `clean()`

Use `clean()` when validation depends on multiple fields.

---

## 7. What does `on_delete=models.CASCADE` do?

`CASCADE` deletes related objects automatically.

Example:

```python
class Review(models.Model):
    movie = models.ForeignKey(
        Movie,
        on_delete=models.CASCADE
    )
```

If a movie is deleted:

```
Movie
 ├── Review 1
 ├── Review 2
 └── Review 3
```

Deleting the movie also deletes all its reviews.

Other `on_delete` options:

- `CASCADE`
- `SET_NULL`
- `SET_DEFAULT`
- `PROTECT`
- `RESTRICT`
- `DO_NOTHING`

---

## 8. How can we sort data in Django?

### Using `order_by()`

Ascending:

```python
Movie.objects.order_by("title")
```

Descending:

```python
Movie.objects.order_by("-rating")
```

Multiple fields:

```python
Movie.objects.order_by("-rating", "title")
```

---

### Default ordering in the model

```python
class Meta:
    ordering = ["-rating"]
```

---

### Sorting in a ListView

```python
class HomeView(ListView):
    model = Movie
    ordering = ["-popularity"]
```

---

## 9. What is `request.POST`?

`request.POST` is a dictionary-like object containing data submitted through an HTML form using the **POST** method.

Example HTML:

```html
<form method="POST">
    {% csrf_token %}
    <input name="title">
</form>
```

View:

```python
def add_movie(request):
    if request.method == "POST":
        title = request.POST["title"]
```

```python
request.POST["title"]
request.POST.get("title")
request.POST.getlist("genres")
```

It only contains form data, **not uploaded files**.

---

## 10. Which request methods are used for uploading images?

Image uploads are typically handled using the **POST** request method.

Example form:

```html
<form method="POST" enctype="multipart/form-data">
    {% csrf_token %}
    <input type="file" name="poster">
</form>
```

View:

```python
if request.method == "POST":
    image = request.FILES["poster"]
```

Important:

- Use `method="POST"`
- Use `enctype="multipart/form-data"`
- Access uploaded files through `request.FILES`, not `request.POST`

---

## 11. Difference between `select_related()` and `prefetch_related()`

| Feature | `select_related()` | `prefetch_related()` |
|----------|-------------------|----------------------|
| Query type | SQL JOIN | Separate queries |
| Relationships | ForeignKey, OneToOne | ManyToMany, Reverse ForeignKey |
| Number of queries | Usually 1 | Usually 2 or more |
| Performance | Faster for single-valued relationships | Better for many-valued relationships |

### `select_related()` example

```python
reviews = Review.objects.select_related("movie")
```

Django performs a SQL JOIN and fetches both Review and Movie in one query.

---

### `prefetch_related()` example

```python
movies = Movie.objects.prefetch_related("reviews")
```

Django performs:

- One query for movies
- One query for reviews

Then joins them in Python.

---

Use `select_related()` for:

- ForeignKey
- OneToOneField

Use `prefetch_related()` for:

- ManyToManyField
- Reverse ForeignKey
- Reverse ManyToMany

Using the correct method helps reduce the **N+1 query problem** and improves database performance.
