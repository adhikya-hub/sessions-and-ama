# AMA

## 1. What is the use of Kubernetes?

Kubernetes (K8s) is a container orchestration platform used to deploy, manage, and scale containerized applications automatically.

---

## 2. How are elements stored in the browser?

When a web page loads, the browser processes HTML, CSS, and JavaScript to create internal data structures:

- **DOM (Document Object Model):** A tree representing all HTML elements.
- **CSSOM (CSS Object Model):** A tree representing all CSS rules.
- **Render Tree:** Combines the DOM and CSSOM to determine what should be displayed.
- **Layout:** Calculates the size and position of each visible element.
- **Paint:** Draws the elements on the screen.

---

## 3. What is localStorage in the browser?

`localStorage` is a browser feature that stores key-value pairs permanently on the user's device.

```javascript
localStorage.setItem("username", "Alice");

const name = localStorage.getItem("username");

localStorage.removeItem("username");

localStorage.clear();
```

---

## 4. What is Self-Consistency?

Self-Consistency is a prompting technique used with large language models.

Instead of generating only one reasoning path, the model:
1. Produces multiple different reasoning paths for the same question.
2. Compares the final answers.
3. Chooses the answer that appears most frequently.

This improves accuracy for reasoning-heavy tasks like mathematics and logical problems.

---

## 5. How do you delete a Git branch?

### Delete a local branch

```bash
git branch -d branch-name
```

Use `-d` if the branch has already been merged.

### Force delete a local branch

```bash
git branch -D branch-name
```

Deletes the branch even if it hasn't been merged.

### Delete a remote branch

```bash
git push origin --delete branch-name
```

---

## 6. What is a Cross Join?

A **Cross Join** returns the Cartesian product of two tables.

Every row from the first table is combined with every row from the second table.

**Syntax:**

```sql
SELECT *
FROM table1
CROSS JOIN table2;
```

### Example

**Students**

| ID | Name |
|----|------|
| 1  | Alice |
| 2  | Bob |

**Courses**

| Course |
|---------|
| Math |
| Science |

**Result**

| Name | Course |
|------|---------|
| Alice | Math |
| Alice | Science |
| Bob | Math |
| Bob | Science |

If the first table has **m** rows and the second has **n** rows, the result contains **m × n** rows.
