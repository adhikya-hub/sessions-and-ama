# AMA

## RAG vs MCP

- **RAG:** Retrieves relevant information from external documents/data to help the AI answer.
- **MCP:** Allows AI to connect to and use external tools, data sources, and services.
- RAG = **retrieve information** MCP = **connect and use tools/data**.

## `useParams` Hook

- `useParams` is a React Router hook used to get **dynamic values from the URL**.
- Example: `/users/25` → `useParams()` gives `{ id: "25" }`.
- Mainly used to fetch data based on an ID.

## Blue Team vs Red Team

- **Red Team:** Acts like an attacker and tries to find security weaknesses.
- **Blue Team:** Acts like a defender and protects against attacks.

## Prompt Caching

- Prompt caching stores frequently reused parts of a prompt.
- It avoids processing the same content repeatedly.
- This can make AI requests **faster and cheaper**.

## Flexible Schema: SQL vs NoSQL

- **NoSQL** generally has a more flexible schema.
- **SQL:** Usually has a predefined structure with tables and columns.
- **NoSQL:** Can allow different records/documents to have different fields.
- **Answer:** **NoSQL**.

## `WHERE` vs `HAVING`

- **WHERE:** Filters rows **before** grouping.
- **HAVING:** Filters groups **after** `GROUP BY`.

```sql
SELECT department, COUNT(*)
FROM employees
WHERE salary > 30000
GROUP BY department
HAVING COUNT(*) > 5;
