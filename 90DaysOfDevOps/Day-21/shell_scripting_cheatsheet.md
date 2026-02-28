# Day 21 – Shell Scripting Cheat Sheet: Build Your Own Reference Guide

## CHEETSHEET SUMMARY TABLE
```
| Topic    | Key Syntax               | Example                            |
|----------|--------------------------|------------------------------------|
| Variable | `VAR="value"`            | `NAME="DevOps"`                    |
| Argument | `$1`, `$2`               | `./script.sh arg1`                 |
| If       | `if [ condition ]; then` | `if [ -f file ]; then`             |
| For loop | `for i in list; do`      | `for i in 1 2 3; do`               |
| Function | `name() { ... }`         | `greet() { echo "Hi"; }`           |
| Grep     | `grep pattern file`      | `grep -i "error" log.txt`          |
| Awk      | `awk '{print $1}' file`  | `awk -F: '{print $1}' /etc/passwd` |
| Sed      | `sed 's/old/new/g' file` | `sed -i 's/foo/bar/g' config.txt`  |
```

## Challenge Tasks

### Task 1: Basics
1. Shebang (`#!/bin/bash`) —
    ✔ Tells system to execute script using Bash interpreter.
    ✔ Must be first line.
    ✔ Ensures correct shell is used.
    
2. Running a script —
    `chmod +x         # make executable`
    `./script.sh      # run directly`
    `bash script.sh   # run with bash`

3. Comments —
   ```bash
   # This is a single-line comment
   echo "Hello"  # Inline comment
   ```

4. Variables —
   ```bash
   NAME="Harjot"
   echo $NAME     # Expands variable
   echo "$NAME"   # Safe expansion
   echo '$NAME'   # Literal, no expansion
   ```

5. Reading user input — 
   ```bash
   read -p "Enter your name: " NAME
   echo "Hello $NAME"
   ```

6. Command-line arguments —
   ```bash
   echo "Script name: $0"
   echo "First arg: $1"
   echo "Total args: $#"
   echo "All args: $@"
   echo "Last exit code: $?"
   ```

---

### Task 2: Operators and Conditionals
1. String comparisons —
```bash
[ "$a" = "$b" ]
[ "$a" != "$b" ]
[ -z "$a" ]   # empty
[ -n "$a" ]   # not empty
```
   
2. Integer comparisons —
```bash
[ $a -eq $b ]
[ $a -ne $b ]
[ $a -lt $b ]
[ $a -gt $b ]
[ $a -le $b ]
[ $a -ge $b ]
```

3. File test operators — 
```bash
[ -f file ]   # regular file
[ -d dir ]    # directory
[ -e file ]   # exists
[ -r file ]   # readable
[ -w file ]   # writable
[ -x file ]   # executable
[ -s file ]   # not empty
```

4. `if`, `elif`, `else` syntax
```bash
if [ -f file.txt ]; then
    echo "File exists"
elif [ -d folder ]; then
    echo "Directory exists"
else
    echo "Not found"
fi
```

5. Logical operators — `&&`, `||`, `!`
```bash
[ -f file ] && echo "Exists"
[ -f file ] || echo "Missing"
! [ -f file ]
```

6. Case statements — `case ... esac`
```bash
case $1 in
    start) echo "Starting" ;;
    stop) echo "Stopping" ;;
    *) echo "Usage: start|stop" ;;
esac
```

---

### Task 3: Loops
1. `for` loop — list-based and C-style
```bash
for i in 1 2 3
do
    echo $i
done

for ((i=1; i<=5; i++))
do
    echo $i
done
```

2. `while` loop
```bash
i=1
while [ $i -le 5 ]
do
    echo $i
    ((i++))
done
```

3. `until` loop
```bash
i=1
until [ $i -gt 5 ]
do
    echo $i
    ((i++))
done
```

4. Loop control — `break`, `continue`
```bash
break
continue
```

5. Looping over files — `for file in *.log`
```bash
for file in *.log
do
    echo "$file"
done
```

6. Looping over command output — `while read line`
```bash
for file in *.log
do
    echo "$file"
done
```
---

### Task 4: Functions
1. Defining a function — `function_name() { ... }`
```bash
greet() {
    echo "Hello $1"
}
```

2. Calling a function
```bash
greet Harjot
```

3. Passing arguments to functions — `$1`, `$2` inside functions
```bash
echo $1
echo $2
```

4. Return values — `return` vs `echo`
```bash
add() {
    return 5   # only 0–255
}

get_name() {
    echo "Harjot"
}
```

5. Local variables — `local`
```bash
myfunc() {
    local name="DevOps"
}
```
---

### Task 5: Text Processing Commands
1. `grep` — search patterns, `-i`, `-r`, `-c`, `-n`, `-v`, `-E`
```bash
grep "error" file
grep -i "error" file     # case insensitive
grep -r "error" .        # recursive
grep -c "error" file     # count
grep -n "error" file     # line number
grep -v "error" file     # invert
grep -E "err|fail" file  # regex
```

2. `awk` — print columns, field separator, patterns, `BEGIN/END`
```bash
awk '{print $1}' file
awk -F: '{print $1}' /etc/passwd
awk '/error/ {print $0}' file
awk 'BEGIN {print "Start"} END {print "Done"}'
```

3. `sed` — substitution, delete lines, in-place edit
```bash
sed 's/old/new/g' file
sed -i 's/old/new/g' file
sed '/pattern/d' file
```

4. `cut` — extract columns by delimiter
```bash
cut -d: -f1 /etc/passwd
```

5. `sort` — alphabetical, numerical, reverse, unique
```bash
sort file
sort -n file
sort -r file
sort -u file
```

6. `uniq` — deduplicate, count
```bash
uniq file
uniq -c file
```

7. `tr` — translate/delete characters
```bash
tr 'a-z' 'A-Z'
tr -d '\n'
```

8. `wc` — line/word/char count
```bash
wc -l file
wc -w file
wc -c file
```

9. `head` / `tail` — first/last N lines, follow mode
```bash
head -n 10 file
tail -n 10 file
tail -f logfile
```
---

### Task 6: Useful Patterns and One-Liners
1. Delete files older than 7 days: `find . -type f -mtime +7 -delete`
2. Count lines in all .log files: `wc -l *.log`
3. Replace string in multiple files: `sed -i 's/old/new/g' *.txt`
4. Check if service running: `systemctl is-active nginx`
5. Monitor disk usage > 80%: `df -h | awk '$5+0 > 80 {print $0}'`
6. Tail and filter errors: `tail -f app.log | grep --line-buffered "ERROR"`
---

### Task 7: Error Handling and Debugging
1. Exit codes — `echo $?`, `exit 0` and `exit 1`
2. `set -e` — exit on error
3. `set -u` — treat unset variables as error
4. `set -o pipefail` — catch errors in pipes
5. `set -x` — debug mode (trace execution)
6. Trap — `trap 'echo "Cleaning up"; rm -f temp.txt' EXIT`

---

---
