# Day 10 – File Permissions & File Operations Challenge

## Challenge Tasks

### Task 1: Create Files

1. Create empty file `devops.txt` using `touch`
2. Create `notes.txt` with some content using `cat` or `echo`
3. Create `script.sh` using `vim` with content: `echo "Hello DevOps"`

<img width="704" height="332" alt="image" src="https://github.com/user-attachments/assets/2ed239b5-6686-483b-bd09-9952228cd0f4" />

<img width="838" height="670" alt="image" src="https://github.com/user-attachments/assets/973309e5-21ac-405a-8627-83f37ba3708a" />

---

### Task 2: Read Files

1. Read `notes.txt` using `cat`
2. View `script.sh` in vim read-only mode
3. Display first 5 lines of `/etc/passwd` using `head`
4. Display last 5 lines of `/etc/passwd` using `tail`

<img width="742" height="344" alt="image" src="https://github.com/user-attachments/assets/9e9373e4-2a5b-4069-8dda-47e0907a3b9a" />

<img width="734" height="230" alt="image" src="https://github.com/user-attachments/assets/19abc832-9b82-435e-babd-909a618822c6" />


---

### Task 3: Understand Permissions

Format: `rwxrwxrwx` (owner-group-others)
- `r` = read (4), `w` = write (2), `x` = execute (1)

<img width="755" height="342" alt="image" src="https://github.com/user-attachments/assets/329c2976-f05e-446f-8f78-5c6f66db1d20" />

---

### Task 4: Modify Permissions

1. Make `script.sh` executable → run it with `./script.sh`
2. Set `devops.txt` to read-only (remove write for all)
3. Set `notes.txt` to `640` (owner: rw, group: r, others: none)
4. Create directory `project/` with permissions `755`

<img width="915" height="641" alt="image" src="https://github.com/user-attachments/assets/927164d3-a382-4c3b-9f21-5a1f4472ebd5" />

---

### Task 5: Test Permissions

1. Try writing to a read-only file - what happens?
2. Try executing a file without execute permission
3. Document the error messages

<img width="673" height="279" alt="image" src="https://github.com/user-attachments/assets/f1cd1ac1-b775-4178-b3d0-ab87d7138b8a" />

<img width="935" height="678" alt="image" src="https://github.com/user-attachments/assets/4f3386aa-3780-43a6-994b-3d2a8608f14d" />

---
