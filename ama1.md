# CLI & Git

## 1. Difference Between `grep` and `find`

- `grep`: Searches for text inside files
- `find`: Searches for files or directories based on name, type, etc.

```bash
find . -type f -exec awk '/pattern/ {print FILENAME ": " $0}' {} +
```

[https://www.redhat.com/en/blog/linux-find-command](https://www.redhat.com/en/blog/linux-find-command)

---

## 2. How to Find All Currently Running Processes

```bash
ps aux
```

a for all the users, u for user format, x for processes not attached with the terminal

Or:

```bash
top
```

live processes

---

## 3. Disk Usage

```bash
df -h
```

h for human readable format

---

## 4. Word Occurrence in a Text File

```bash
grep -o "word" file.txt | wc -l
```

"o" gives each match in a new line, so lines give the word occurrence

---

## 5. Connect Git with GitHub

### Add Remote Repository

```bash
git remote add origin https://github.com/username/repository.git
```

### Push Code

```bash
git push -u origin main
```

---

## 6. Open Browser from Terminal

```bash
open https://google.com
```

---

## 7. Change Commit Message

```bash
git commit --amend -m "New commit message"
```

---

## 8. Rename a File

```bash
mv oldname.txt newname.txt
```

---

## 9. Difference Between `less` and `more`

| `less` | `more` |
| --- | --- |
| Can scroll up and down | Mostly forward navigation only |
| More advanced | Simpler |
| Search and better controls | Limited features |

---

## 10. Merge Conflict

A merge conflict happens when Git cannot automatically merge changes from different branches.

---

## 11. Create an Empty File

```bash
touch file.txt
```

---

## 12. Difference Between `Ctrl + Z` and `Ctrl + X`

`Ctrl + Z` Suspends current process
`Ctrl + X` Cuts selected text

---

## 13. Staging Area in Git

The staging area is where changes are prepared before committing.

---

## 14. Remove Git Initialization

```bash
rm -rf .git
```

---

## 15. Numeric Permissions in Linux

| Permission | Number |
| --- | --- |
| Read | 4 |
| Write | 2 |
| Execute | 1 |

### Example

```bash
chmod 755 file.txt
```

- Owner → 7 (`rwx`)
- Group → 5 (`r-x`)
- Others → 5 (`r-x`)
