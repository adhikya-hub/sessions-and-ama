# AMA

## 1. Why is Kubernetes called K8s?

"K8s" is a numeronym for **Kubernetes**. The word **Kubernetes** has 10 letters. The first letter is **K**, the last letter is **s**, and there are **8 letters** in between, so it is shortened to **K8s**.

---

## 2. What are Generic Views (Generic Classes) in DRF?

Generic Views are pre-built class-based views in Django REST Framework that provide common CRUD operations with minimal code. They combine generic behavior with mixins, reducing boilerplate code.

**Examples:**
- `ListAPIView`
- `CreateAPIView`
- `RetrieveAPIView`
- `UpdateAPIView`
- `DestroyAPIView`
- `ListCreateAPIView`

---

## 3. What is the use of decorators?

Decorators modify or extend the behavior of a function or class without changing its code.

**Common uses in Django/DRF:**
- Restrict HTTP methods (`@api_view`)
- Require authentication (`@login_required`)
- Check permissions (`@permission_classes`)
- Cache responses (`@cache_page`)

---

## 4. What are Mixins in DRF?

Mixins are reusable classes that provide specific functionality like listing, creating, updating, or deleting objects. They are combined with Generic Views to build APIs.

**Examples:**
- `ListModelMixin`
- `CreateModelMixin`
- `RetrieveModelMixin`
- `UpdateModelMixin`
- `DestroyModelMixin`

---

## 5. Why is a Foreign Key called a one-to-many relationship in Django?

A Foreign Key creates a one-to-many relationship because one parent object can be related to many child objects, while each child object belongs to only one parent.

**Example:**
One department can have many employees, but each employee belongs to only one department.

---

## 6. Difference between Function-Based Views (FBVs) and Class-Based Views (CBVs)

| Function-Based Views | Class-Based Views |
|----------------------|-------------------|
| Written as functions | Written as classes |
| Good for simple APIs | Better for large applications |
| More code repetition | More reusable and organized |
| Easy to understand | Supports inheritance and mixins |
| Manual handling of HTTP methods | Uses methods like `get()`, `post()`, `put()`, `delete()` |

---

## 7. What is a Router in DRF?

A Router automatically generates URL patterns for ViewSets, so you don't need to define each URL manually.

**Example:**
```python
router = DefaultRouter()
router.register("employees", EmployeeViewSet)

urlpatterns = router.urls
```

---

## 8. What is the use of Django REST Framework (DRF)?

DRF is used to build RESTful APIs quickly and efficiently. It provides features like serialization, authentication, permissions, pagination, filtering, throttling, and browsable APIs.

---

## 9. What are URL patterns and the `urls.py` file?

The `urls.py` file maps URL paths to views. URL patterns tell Django which view should handle a particular request.

**Example:**
```python
from django.urls import path
from .views import EmployeeList

urlpatterns = [
    path("employees/", EmployeeList.as_view()),
]
```

---

## 10. What is Throttling in DRF?

Throttling limits the number of API requests a client can make within a specific time period. It helps prevent abuse, protects the server from overload, and ensures fair API usage.

**Example:**
A user may be allowed only **100 requests per hour**.
