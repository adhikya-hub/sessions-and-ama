# AMA

## 1. What is the default port of PostgreSQL?

The default port for PostgreSQL is **5432**.

```text
Host: localhost
Port: 5432
Database: mydb
Username: postgres
```

---

## 2. How do we create and activate a Python virtual environment?

### Create a virtual environment

```bash
python -m venv venv
```

### Activate the virtual environment

```bash
source venv/bin/activate
```

### Deactivate the virtual environment

```bash
deactivate
```

---

## 3. What is the use of Django REST Framework (DRF)?

Django REST Framework (DRF) is used to build **RESTful APIs** using Django.

- Converts Django models into JSON using serializers.
- Handles HTTP methods like GET, POST, PUT, PATCH, and DELETE.
- Supports authentication and permissions.
- Provides pagination, filtering, and searching.
- Includes a browsable API for testing.
- Makes it easy for frontend applications (React, Angular, Flutter, mobile apps) to communicate with the backend.

```
Frontend (React)
        ↓
     HTTP Request
        ↓
     Django REST API
        ↓
      Database
```

---

## 4. What is the difference between Authentication and Authorization?

| Authentication | Authorization |
|---------------|---------------|
| Verifies who the user is. | Determines what the user can access. |
| Example: Login using username and password. | Example: Only admins can delete users. |

---

## 5. What are `*args` and `**kwargs` in Python?

### `*args`

Allows a function to accept any number of **positional arguments**.

```python
def add(*args):
    return sum(args)

print(add(1, 2, 3, 4))
```

Output:

```text
10
```

### `**kwargs`

Allows a function to accept any number of **keyword arguments**.

```python
def details(**kwargs):
    print(kwargs)

details(name="Alice", age=22)
```

Output:

```python
{'name': 'Alice', 'age': 22}
```

```python
def func(*args, **kwargs):
    print(args)
    print(kwargs)

func(1, 2, 3, name="John", city="Hyderabad")
```

Output:

```python
(1, 2, 3)
{'name': 'John', 'city': 'Hyderabad'}
```

---

## 6. Explain the Django project directory.

```
myproject/
│
├── manage.py
├── db.sqlite3
├── requirements.txt
│
├── myproject/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── app/
│   ├── migrations/
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   ├── serializers.py
│   ├── tests.py
│   └── templates/
```

| File | Purpose |
|------|---------|
| `manage.py` | Command-line utility for Django |
| `settings.py` | Project configuration |
| `urls.py` | URL routing |
| `wsgi.py` | Used by WSGI servers like Gunicorn |
| `asgi.py` | Used by ASGI servers like Uvicorn/Daphne |
| `models.py` | Database models |
| `views.py` | Business logic |
| `admin.py` | Admin site configuration |

---

## 7. How do you create a Django app?

Create an app:

```bash
python manage.py startapp app_name
```

Example:

```bash
python manage.py startapp students
```

1. Add the app to `INSTALLED_APPS`.
2. Create models.
3. Run migrations.
4. Create views.
5. Configure URLs.

---

## 8. What are static files in Django?

Static files are files that do not change dynamically.

Examples:

- CSS
- JavaScript
- Images
- Fonts

In the template:

```django
{% load static %}

<link rel="stylesheet" href="{% static 'css/style.css' %}">
```

Collect static files for production:

```bash
python manage.py collectstatic
```

---

## 9. What is a Custom User Model in Django?

A custom user model replaces Django's default `User` model so you can add your own fields or customize authentication.

Example:

```python
from django.contrib.auth.models import AbstractUser
from django.db import models

class User(AbstractUser):
    phone_number = models.CharField(max_length=15, blank=True)
```

In `settings.py`:

```python
AUTH_USER_MODEL = "accounts.User"
```

- Add extra fields like phone number or profile picture.
- Use email instead of username for login.
- Customize authentication behavior.
- Avoid future migration issues.

Create the custom user model before running the first migration because changing it later is difficult.
