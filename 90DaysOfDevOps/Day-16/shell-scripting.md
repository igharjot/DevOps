# Day 16 – Shell Scripting Basics

## Challenge Tasks

### Task 1: Your First Script
1. Create a file `hello.sh`
2. Add the shebang line `#!/bin/bash` at the top
3. Print `Hello, DevOps!` using `echo`
4. Make it executable and run it

<img width="586" height="210" alt="image" src="https://github.com/user-attachments/assets/e26669be-d959-4523-8ef8-519c077cebf8" />

<img width="830" height="544" alt="image" src="https://github.com/user-attachments/assets/e62cee05-35c3-41f2-9aed-3d6c9396fa68" />
.
**Document:** What happens if you remove the shebang line?
Without shebang:

- System uses parent shell/default shell
- Bash-specific features may break:
    - arrays
    - [[ ]]
    - brace expansion
    - source

---

### Task 2: Variables
1. Create `variables.sh` with:
   - A variable for your `NAME`
   - A variable for your `ROLE` (e.g., "DevOps Engineer")
   - Print: `Hello, I am <NAME> and I am a <ROLE>`
2. Try using single quotes vs double quotes — what's the difference?

<img width="723" height="286" alt="image" src="https://github.com/user-attachments/assets/7d4fd24c-86aa-4724-87fe-01a25b611327" />

<img width="820" height="551" alt="image" src="https://github.com/user-attachments/assets/70a6a77b-4ff7-400b-ab26-a8fd4c0a7d6c" />

---

### Task 3: User Input with read
1. Create `greet.sh` that:
   - Asks the user for their name using `read`
   - Asks for their favourite tool
   - Prints: `Hello <name>, your favourite tool is <tool>`


---

### Task 4: If-Else Conditions
1. Create `check_number.sh` that:
   - Takes a number using `read`
   - Prints whether it is **positive**, **negative**, or **zero**

2. Create `file_check.sh` that:
   - Asks for a filename
   - Checks if the file **exists** using `-f`
   - Prints appropriate message



---

### Task 5: Combine It All
Create `server_check.sh` that:
1. Stores a service name in a variable (e.g., `nginx`, `sshd`)
2. Asks the user: "Do you want to check the status? (y/n)"
3. If `y` — runs `systemctl status <service>` and prints whether it's **active** or **not**
4. If `n` — prints "Skipped."



---
