# Day 18 – Shell Scripting: Functions & Slightly Advanced Concepts

## Challenge Tasks

### Task 1: Basic Functions
1. Create `functions.sh` with:
   - A function `greet` that takes a name as argument and prints `Hello, <name>!`
   - A function `add` that takes two numbers and prints their sum
   - Call both functions from the script

<img width="769" height="375" alt="image" src="https://github.com/user-attachments/assets/5ed338b0-ef93-44ff-ba56-78b1c0c2a884" />

<img width="580" height="410" alt="image" src="https://github.com/user-attachments/assets/834ce490-1754-4a10-a001-b53c33d8c433" />

---

### Task 2: Functions with Return Values
1. Create `disk_check.sh` with:
   - A function `check_disk` that checks disk usage of `/` using `df -h`
   - A function `check_memory` that checks free memory using `free -h`
   - A main section that calls both and prints the results

<img width="759" height="577" alt="Screenshot 2026-02-26 033542" src="https://github.com/user-attachments/assets/2089a311-d5de-4bd0-8ccf-a0aee070548e" />

<img width="846" height="736" alt="Screenshot 2026-02-26 033656" src="https://github.com/user-attachments/assets/189d4c04-dd4d-46a9-bb38-70dac79907e8" />

---

### Task 3: Strict Mode — `set -euo pipefail`
1. Create `strict_demo.sh` with `set -euo pipefail` at the top
2. Try using an **undefined variable** — what happens with `set -u`?
3. Try a command that **fails** — what happens with `set -e`?
4. Try a **piped command** where one part fails — what happens with `set -o pipefail`?

**Document:** What does each flag do?
- `set -e` → Exit on error: The script immediately stops if any command returns a non-zero exit status (i.e., fails).
Prevents the script from continuing in a broken state.

- `set -u` → Treat unset variables as an error: If you use a variable that was never defined, the script exits. Helps catch typos and logical mistakes.

- `set -o pipefail` → Catch failures in pipelines: Normally, in a pipeline (cmd1 | cmd2 | cmd3), Bash only checks the last command’s exit status. With pipefail, the pipeline fails if any command in it fails.

<img width="952" height="735" alt="image" src="https://github.com/user-attachments/assets/52cfe3ec-7c11-4927-b64b-b7549f7663fc" />
<img width="934" height="164" alt="image" src="https://github.com/user-attachments/assets/5e3d5fa9-2aae-4b43-8795-7ecc9e3db944" />
<img width="922" height="182" alt="image" src="https://github.com/user-attachments/assets/e07ccb6a-52db-4c4e-aa80-d9fd215fa97b" />

---
### Task 4: Local Variables
1. Create `local_demo.sh` with:
   - A function that uses `local` keyword for variables
   - Show that `local` variables don't leak outside the function
   - Compare with a function that uses regular variables



---

### Task 5: Build a Script — System Info Reporter
Create `system_info.sh` that uses functions for everything:
1. A function to print **hostname and OS info**
2. A function to print **uptime**
3. A function to print **disk usage** (top 5 by size)
4. A function to print **memory usage**
5. A function to print **top 5 CPU-consuming processes**
6. A `main` function that calls all of the above with section headers
7. Use `set -euo pipefail` at the top



---

