# Linux Command Line Basics - Homework 1

**Subject:** CS11117 - Hệ điều hành Linux và ứng dụng - CQ2023/4
**Name:** Huỳnh Trần Ty
**Student ID:** 22120418

---

## Task 1: System Investigation

### Commands:
```bash
pwd
cd Documents
pwd
```

### Explanation:
- `pwd` (Print Working Directory) displays the current directory path
- `cd Documents` changes to the Documents directory using a relative path from home
- `pwd` again confirms the new location

### Output:
![Task 1 - System Investigation](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_1.png)

---

## Task 2: Directory Setup

### Commands:
```bash
mkdir project_logs
cd project_logs
mkdir old_backup archive current
touch temp.txt
ls -la
```

### Explanation:
- `mkdir project_logs` creates the main directory
- `cd project_logs` navigates into it
- `mkdir old_backup archive current` creates three subdirectories at once
- `touch temp.txt` creates an empty file
- `ls -la` lists all contents including hidden files with details

### Output:

![Task 2 - Directory Setup](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_2.png)

---

## Task 3: Log Review

### Commands:
```bash
tail -n 10 /var/log/syslog
head -n 5 /var/log/syslog
tac /var/log/syslog
```

### Explanation:
- `tail -n 10` displays the last 10 lines of the file
- `head -n 5` displays the first 5 lines of the file
- `tac` reverses the file content (cat backwards) - useful for quick scanning from newest to oldest

### Output:
`tail -n 10:`
![Task 3 - Log Review](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_3.1.png)

`head -n 5:`
![Task 3 - Log Review](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_3.2.png)

`tac:`
![Task 3 - Log Review](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_3.3.png)

---

## Task 4: Pattern Search

### Commands:
```bash
grep -i "error" /var/log/syslog > errors.log
wc -l errors.log
```

### Explanation:
- `grep -i "error"` searches for "error" case-insensitively (-i flag)
- `>` redirects output to errors.log (creates or overwrites the file)
- `wc -l` counts the number of lines in the file

### Output:

![Task 4 - Pattern Search](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_4.png)

This means 135 lines containing "error" were found.

---

## Task 5: Stream Redirection

### Commands:
```bash
ls /etc > etc_list.txt
ls /bin >> etc_list.txt
less etc_list.txt
```

### Explanation:
- `ls /etc > etc_list.txt` redirects output to file (overwrites if exists)
- `ls /bin >> etc_list.txt` appends output to the same file
- `less` allows viewing the file one page at a time (use Space for next page, 'q' to quit)


### Ouput:
![Task 5 - Stream Redirection](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_5.1.png)

---

## Task 6: Text Processing

### Commands:
```bash
cat > users.txt << EOF
Alice:Admin
Bob:User
Carol:Guest
EOF

cut -d':' -f1 users.txt | tr '[:upper:]' '[:lower:]' | sort -r
```

### Explanation:
- `cat > users.txt << EOF` creates the file with specified content
- `cut -d':' -f1` extracts first field using ':' as delimiter (usernames only)
- `tr '[:upper:]' '[:lower:]'` translates uppercase to lowercase
- `sort -r` sorts in reverse alphabetical order
- Pipes (`|`) connect commands, passing output of one as input to the next

### Output:

![Task 6 - Text Processing](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_6.png)

---

## Task 7: Cleanup Script

### Commands:
```bash
rmdir old_backup
rm temp.txt
mv report.txt archive/
cp archive/report.txt current/report_backup.txt
```

### Explanation:
- `rmdir` removes empty directories only
- `rm` deletes files
- `mv` moves files (also used for renaming)
- `cp` copies files while preserving the original

### Output:

![Task 7 - Cleanup Script](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_7.png)

---

## Task 8: File Hunting

### Commands:
```bash
find /etc -name "*.conf" -type f
find ~ -perm 755 -type f
find /usr -type d -name "*lib*"
```

### Explanation:
- `find /etc -name "*.conf" -type f` searches for files (-type f) ending with .conf
- `find ~ -perm 755 -type f` finds files with exact 755 permissions in home directory
- `find /usr -type d -name "*lib*"` finds directories (-type d) containing "lib" in name

### Output:

`find /etc -name "*.conf" -type f`:
![Task 8 - File Hunting](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_8.1.png)

`find ~ -perm 755 -type f`:
![Task 8 - File Hunting](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_8.2.png)

`find /usr -type d -name "*lib*"`:
![Task 8 - File Hunting](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_8.3.png)


---

## Task 9: Joining Data

### Commands:
```bash
cat > names.txt << EOF
1 Alice
2 Bob
3 Carol
EOF

cat > roles.txt << EOF
1 Admin
2 User
3 Guest
EOF

join names.txt roles.txt > combined.txt
cat combined.txt
```

### Explanation:
- Creates two files with matching keys (first field)
- `join` merges files based on common field (default: first field)
- Both files must be sorted on the join field (already sorted here)

### Output:

![Task 9 - Joining Data](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_9.png)

---

## Task 10: Line Numbering & Word Counts

### Commands:
```bash
nl users.txt
wc -l users.txt
wc -w users.txt
wc -c users.txt
wc users.txt
```

### Explanation:
- `nl` adds line numbers to file output
- `wc -l` counts lines
- `wc -w` counts words
- `wc -c` counts bytes
- `wc` alone shows all three counts

### Output:

![Task 10 - Line Numbering & Word Counts](https://raw.githubusercontent.com/huynhtranty/CS11117-Linux/main/image/task_10.png)

---
