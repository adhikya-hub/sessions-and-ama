# AMA

## 1. What is a Producer in RabbitMQ?

A **Producer** is an application or service that **sends messages** to RabbitMQ. It does not send messages directly to a queue. Instead, it sends them to an **Exchange**, which routes the messages to one or more queues based on routing rules.

---

## 2. What is the difference between an Image and a Container in Docker?

| Docker Image | Docker Container |
|--------------|------------------|
| A read-only template used to create containers. | A running instance of an image. |
| Static and cannot be changed while running. | Dynamic and can be started, stopped, or modified. |
| Contains application code, dependencies, and configuration. | Runs the application using the image. |
| Multiple containers can be created from one image. | Each container is an independent runtime environment. |

---

## 3. What is the main purpose of Kubernetes?

**Kubernetes** is a container orchestration platform used to **deploy, manage, scale, and automate containerized applications**.

### Main purposes:
- Automatically deploy containers.
- Scale applications up or down.
- Restart failed containers.
- Load balance traffic.
- Perform rolling updates with minimal downtime.

If a container crashes, Kubernetes automatically creates a new one to keep the application running.

---

## 4. What is Containerization in Docker?

**Containerization** is the process of packaging an application along with all its dependencies, libraries, and configuration into a **container** so it runs consistently across different environments.

---

## 5. What is the difference between DDL and DML?

| DDL (Data Definition Language) | DML (Data Manipulation Language) |
|--------------------------------|----------------------------------|
| Defines or modifies database structure. | Manipulates data stored in tables. |
| Changes schema. | Changes records. |
| Automatically commits changes in most databases. | Requires COMMIT (depending on transaction settings). |
| Used for creating or altering objects. | Used for inserting, updating, deleting, and retrieving data. |

### DDL Commands
- `CREATE`
- `ALTER`
- `DROP`
- `TRUNCATE`
- `RENAME`

### DML Commands
- `INSERT`
- `UPDATE`
- `DELETE`
- `SELECT`

---

## 6. What is a View in SQL?

A **View** is a **virtual table** created using a SQL query. It does not store data itself; instead, it displays data from one or more underlying tables whenever it is queried.

### Example

```sql
CREATE VIEW employee_details AS
SELECT id, name, department
FROM employees;
```

Now you can query the view like this:

```sql
SELECT * FROM employee_details;
```

The data displayed comes from the `employees` table.
