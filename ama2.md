# AMA

## How to rename current branch?
```bash
git branch -m new-branch-name
```

---

## What are git tags?
Git tags are labels used to mark important commits, usually for releases like `v1.0`.

Example:
```bash
git tag v1.0
```

---

## What are git hooks?
Git hooks are scripts that run automatically before or after Git events like commit, push, or merge.

Examples:
- `pre-commit`
- `post-merge`

---

## How to check Git HEAD?
```bash
git branch
```

```bash
git log --oneline -1
```

```bash
cat .git/HEAD
```

---

## How to discard all changes from working directory in Git?
```bash
git restore .
```

To remove untracked files too:
```bash
git clean -fd
```

---

## What is OFFSET in SQL?
`OFFSET` skips a number of rows before returning results.

---

## What is git revert?
`git revert` creates a new commit that undoes changes from a previous commit.

---

## How to check IP address of PC?

### Mac
```bash
ipconfig getifaddr en0
```

```bash
ifconfig
```

Or:
```bash
ip addr
```

---

## Difference between nslookup and ping

| Command | Purpose |
|---|---|
| `ping` | Checks connectivity to another system |
| `nslookup` | Finds DNS/IP information of a domain |

---

## How to resolve merge conflict?

Steps:
```bash
git pull
```

1. Open conflicted file
2. Edit and remove conflict markers
3. Save file

Then:
```bash
git add .
git commit
```

---

## How to remove a user from a particular group? (Linux)
```bash
sudo gpasswd -d username groupname
```

---

## Types of reset in Git

| Type | Effect |
|---|---|
| `--soft` | Removes commit, keeps staging |
| `--mixed` | Removes commit and unstages changes |
| `--hard` | Removes commit and deletes changes |

Examples:
```bash
git reset --soft HEAD~1
```

```bash
git reset --mixed HEAD~1
```

```bash
git reset --hard HEAD~1
```

---

## What is use of DEFAULT keyword in SQL?
`DEFAULT` gives a default value to a column if no value is provided.

Example:
```sql
CREATE TABLE users (
    name VARCHAR(50),
    country VARCHAR(20) DEFAULT 'India'
);
```

---

## What is PATH?
PATH is an environment variable that tells the operating system where to look for executable files.

Example:
When you type:
```bash
python
```

System searches directories listed in PATH.

Check PATH:
```bash
echo $PATH
```

---

## Can we do method overloading in Python?
Python does not support traditional method overloading like Java or C++.

But similar behavior can be achieved using:
- default arguments
- `*args`
- `**kwargs`

Example:
```python
class Demo:
    def add(self, a, b=0):
        return a + b
```
