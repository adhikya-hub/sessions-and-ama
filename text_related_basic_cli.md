# Basic Linux Commands – Text Related

## `cat` – Display File Content

Used to view, combine, or create files.

```bash
cat file.txt
```

Displays the content of `notes.txt`.

```bash
cat file1.txt file2.txt
```

Displays both files together.

```bash
cat > newfile.txt
```

Creates a new file and lets you type content.

Ctrl + D to save and exit.

```bash
cat .git/HEAD
```

- `cat -n file.txt` Show line numbers
- `cat -b file.txt` Number non-empty lines only

---

## `less` – View Large Files

Better for large files because it allows scrolling.

```bash
less file.txt
```

- `Space`  Next page
- `b` Previous page
- `/word` Search for word
- `q` Quit

---

## `more` – Simple File Viewer

Displays file content one screen at a time.

```bash
more data.txt
```

- `Space` Next page
- `Enter` Next line
- `q` Quit

---

## `tail` – See End of File

Used to see the last lines of a file.

```bash
tail file.txt
```

Shows last 10 lines by default.

- `tail -n 20 file.txt` Show last 20 lines
- `tail -f file.txt` Live updates as file changes

---

## `grep` – Search Text Inside Files

Searches for words or patterns.

```bash
grep "word" filename
```

- `grep -i`  Ignore case
- `grep -n`  Show line numbers
- `grep -r`  Recursive search in folders
- `grep -v`  Show non-matching lines

---

## `sort` – Sort Lines in a File

Sorts text alphabetically or numerically.

```bash
sort file.txt
```

- `sort -r file.txt` Reverse order
- `sort -n file.txt` Numeric sort
- `sort -u file.txt` Remove duplicates
- `sort -k 2 -nr data.txt` Sort by second column

---

## `wc` – Count Lines, Words, and Characters

`wc` stands for word count.

```bash
wc file.txt
```

Output:

```bash
lines words characters filename
```

- `wc -l file.txt` Count lines
- `wc -w file.txt` Count words
- `wc -c file.txt` Count characters
