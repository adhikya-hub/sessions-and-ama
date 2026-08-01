# AMA

## 1. What is CSRF in Django?

CSRF (Cross-Site Request Forgery) is a security attack where a malicious website tricks a logged-in user into performing unwanted actions on another website. Django protects against CSRF using a **CSRF token**, which must be included in forms that make POST, PUT, PATCH, or DELETE requests.

Example:
```html
<form method="post">
    {% csrf_token %}
</form>
```

---

## 2. What is XSS?

XSS (Cross-Site Scripting) is a security vulnerability where an attacker injects malicious JavaScript into a web page viewed by other users.

---

## 3. What is a ViewSet in Django REST Framework?

A ViewSet is a DRF class that combines multiple related views (such as list, create, retrieve, update, and delete) into a single class, reducing code duplication.

Example:
```python
from rest_framework.viewsets import ModelViewSet

class ProductViewSet(ModelViewSet):
    queryset = Product.objects.all()
    serializer_class = ProductSerializer
```

---

## 4. What is the `login_required` decorator?

`login_required` is a Django decorator that restricts access to authenticated users. If an unauthenticated user tries to access the view, they are redirected to the login page.

Example:
```python
from django.contrib.auth.decorators import login_required

@login_required
def dashboard(request):
    return render(request, "dashboard.html")
```

---

## 5. What are TCL Commands?

TCL (Transaction Control Language) commands are SQL commands used to manage database transactions.

Common TCL commands:
- **COMMIT** – Saves the transaction permanently.
- **ROLLBACK** – Undoes changes since the last commit.
- **SAVEPOINT** – Creates a checkpoint within a transaction.
- **SET TRANSACTION** – Sets transaction properties.

Example:
```sql
BEGIN;

UPDATE employees
SET salary = salary + 5000
WHERE id = 1;

COMMIT;
```

---

## 6. How do you optimize a React application?

Common React optimization techniques include:

- Use `React.memo()` to prevent unnecessary re-renders.
- Use `useMemo()` to memoize expensive calculations.
- Use `useCallback()` to memoize functions.
- Implement lazy loading with `React.lazy()` and `Suspense`.
- Code splitting using dynamic imports.
- Optimize images and static assets.
- Avoid unnecessary state updates.
