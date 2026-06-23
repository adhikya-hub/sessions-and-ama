# AMA

## 1. Does `get()` return `None`?

No. `get()` does not return `None`.

* If exactly one object is found, it returns that object.
* If no object is found, it raises `DoesNotExist`.
* If multiple objects are found, it raises `MultipleObjectsReturned`.

Example:

```python
user = User.objects.get(id=1)
```

---

## 2. How do we use Group By in Django ORM?

Django performs SQL `GROUP BY` using `values()` and `annotate()`.

Example:

```python
from django.db.models import Count

result = (
    Employee.objects
    .values("department")
    .annotate(total=Count("id"))
)
```

Equivalent SQL:

```sql
SELECT department, COUNT(*)
FROM employee
GROUP BY department;
```

---

## 3. What is the use of the migrations folder?

The `migrations` folder stores migration files that track changes made to Django models.

Uses:

* Creates database tables.
* Modifies existing tables.
* Adds or removes columns.
* Keeps database schema synchronized with models.
* Allows version control of database changes.

Commands:

```bash
python manage.py makemigrations
python manage.py migrate
```

---

## 4. What are some common Django model fields?


| Field             | Purpose                   |
| ----------------- | ------------------------- |
| `CharField`       | Short text                |
| `TextField`       | Long text                 |
| `IntegerField`    | Integer values            |
| `FloatField`      | Decimal numbers           |
| `BooleanField`    | True/False values         |
| `DateField`       | Date only                 |
| `DateTimeField`   | Date and time             |
| `EmailField`      | Email validation          |
| `URLField`        | URL validation            |
| `ImageField`      | Image uploads             |
| `FileField`       | File uploads              |
| `ForeignKey`      | Many-to-one relationship  |
| `OneToOneField`   | One-to-one relationship   |
| `ManyToManyField` | Many-to-many relationship |

---

## 5. What is the use of `get_object_or_404()`?

`get_object_or_404()` retrieves an object and automatically raises a 404 error if the object does not exist.

Example:

```python
from django.shortcuts import get_object_or_404

book = get_object_or_404(Book, id=1)
```

Equivalent to:

```python
try:
    book = Book.objects.get(id=1)
except Book.DoesNotExist:
    raise Http404()
```

---

## 6. Should we commit the migrations folder or not?

Yes, migration files should generally be committed to version control.

Reasons:

* Keeps database schema changes consistent across environments.
* Allows teammates to apply the same database changes.
* Helps deploy changes safely.

---

## 7. Do we need to create a unique ID for models?

Usually no.

Django automatically creates an `id` field as the primary key:

```python
id = models.BigAutoField(primary_key=True)
```

Create your own primary key only when you have specific requirements:

```python
employee_id = models.CharField(
    max_length=20,
    primary_key=True
)
```

---

## 8. What is the purpose of the `__str__()` method in models?

The `__str__()` method defines the human-readable representation of a model object.

Example:

```python
class Book(models.Model):
    title = models.CharField(max_length=100)

    def __str__(self):
        return self.title
```

Without `__str__()`:

```text
Book object (1)
```

With `__str__()`:

```text
Harry Potter
```

Useful in Django Admin, Shell, and debugging.

---

## 9. What are the default apps in Django?

A new Django project typically includes these default apps:

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

Purpose:

* `admin` → Admin panel
* `auth` → Authentication and permissions
* `contenttypes` → Generic relationships
* `sessions` → Session management
* `messages` → Flash messages
* `staticfiles` → Static file handling

---

## 10. What does `exclude()` do in Django ORM?

`exclude()` returns all objects except those matching the given condition.

Example:

```python
students = Student.objects.exclude(age=18)
```

Equivalent SQL:

```sql
SELECT *
FROM student
WHERE age != 18;
```

Multiple conditions:

```python
Student.objects.exclude(
    age=18,
    city="Hyderabad"
)
```

This excludes records where both conditions are true.

---

## 11. What is Context in Django?

Context is a dictionary used to pass data from a view to a template.

Example:

```python
def home(request):
    context = {
        "name": "John",
        "age": 25
    }
    return render(request, "home.html", context)
```

Template:

```html
<h1>{{ name }}</h1>
<p>{{ age }}</p>
```

Output:

```html
John
25
```

Context acts as the bridge between views and templates.
