# Day 11 – File Ownership Challenge

## Challenge Tasks

### Task 1: Understanding Ownership

1. Run `ls -l` in your home directory
2. Identify the **owner** and **group** columns
3. Check who owns your files

 <img width="577" height="190" alt="image" src="https://github.com/user-attachments/assets/ae4cf83a-74c8-41bf-afc0-236f43ab1453" />

---

### Task 2: Basic chown Operations

1. Create file `devops-file.txt`
2. Check current owner: `ls -l devops-file.txt`
3. Change owner to `tokyo`
4. Change owner to `berlin`
5. Verify the changes

<img width="856" height="422" alt="image" src="https://github.com/user-attachments/assets/b85b6bb2-40d7-4a77-b8d2-50e5b3d6388f" />

---

### Task 3: Basic chgrp Operations (15 minutes)

1. Create file `team-notes.txt`
2. Check current group: `ls -l team-notes.txt`
3. Create group: `sudo groupadd heist-team`
4. Change file group to `heist-team`
5. Verify the change

<img width="821" height="369" alt="image" src="https://github.com/user-attachments/assets/1e9fdebf-80cf-4bf1-ab31-71e36ee07d69" />

---

### Task 4: Combined Owner & Group Change

1. Create file `project-config.yaml`
2. Change owner to `professor` AND group to `heist-team` (one command)
3. Create directory `app-logs/`
4. Change its owner to `berlin` and group to `heist-team`

<img width="883" height="499" alt="image" src="https://github.com/user-attachments/assets/e596dc36-3a1e-4e55-b772-ec41c28ef6cb" />

---

### Task 5: Recursive Ownership

1. Create directory structure:
   ```
   mkdir -p heist-project/vault
   mkdir -p heist-project/plans
   touch heist-project/vault/gold.txt
   touch heist-project/plans/strategy.conf
   ```

2. Create group `planners`: `sudo groupadd planners`

3. Change ownership of entire `heist-project/` directory:
   - Owner: `professor`
   - Group: `planners`
   - Use recursive flag (`-R`)

4. Verify all files and subdirectories changed: `ls -lR heist-project/`

<img width="899" height="608" alt="image" src="https://github.com/user-attachments/assets/6588c57e-a1c2-4d18-8563-096a7398a599" />

---

### Task 6: Practice Challenge

1. Create users: `tokyo`, `berlin`, `nairobi` (if not already created)
2. Create groups: `vault-team`, `tech-team`
3. Create directory: `bank-heist/`
4. Create 3 files inside:
   ```
   touch bank-heist/access-codes.txt
   touch bank-heist/blueprints.pdf
   touch bank-heist/escape-plan.txt
   ```

5. Set different ownership:
   - `access-codes.txt` → owner: `tokyo`, group: `vault-team`
   - `blueprints.pdf` → owner: `berlin`, group: `tech-team`
   - `escape-plan.txt` → owner: `nairobi`, group: `vault-team`

<img width="916" height="777" alt="image" src="https://github.com/user-attachments/assets/d6e2223f-2c7e-4bad-89ef-7ab53524afdf" />

---
