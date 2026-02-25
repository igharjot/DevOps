# Day 17 – Shell Scripting: Loops, Arguments & Error Handling

## Challenge Tasks

### Task 1: For Loop
1. Create `for_loop.sh` that:
   - Loops through a list of 5 fruits and prints each one
  
<img width="859" height="627" alt="image" src="https://github.com/user-attachments/assets/04cf379f-4c22-46e5-ac08-8eb5b5034b9c" />

<img width="758" height="289" alt="image" src="https://github.com/user-attachments/assets/d5d21faf-cb0f-4edb-98fd-ea0b5a892982" />


2. Create `count.sh` that:
   - Prints numbers 1 to 10 using a for loop

<img width="646" height="277" alt="image" src="https://github.com/user-attachments/assets/f807ad9e-610d-43cd-94c8-84e7cb9e5e69" />

<img width="329" height="232" alt="image" src="https://github.com/user-attachments/assets/9f2255bd-0959-484a-af3c-a91bd675d01e" />

---

### Task 2: While Loop
1. Create `countdown.sh` that:
   - Takes a number from the user
   - Counts down to 0 using a while loop
   - Prints "Done!" at the end

<img width="866" height="746" alt="image" src="https://github.com/user-attachments/assets/a722456b-9c21-4b81-8191-3fd22863acdb" />

<img width="932" height="678" alt="image" src="https://github.com/user-attachments/assets/3d29466c-1464-47d4-8517-0be6c0bec405" />

---

### Task 3: Command-Line Arguments
1. Create `greet.sh` that:
   - Accepts a name as `$1`
   - Prints `Hello, <name>!`
   - If no argument is passed, prints "Usage: ./greet.sh <name>"

<img width="572" height="358" alt="image" src="https://github.com/user-attachments/assets/bc42aa88-15a7-4a63-bfa7-64b6c8f286c9" />

<img width="740" height="430" alt="image" src="https://github.com/user-attachments/assets/5893f79b-9848-4a5c-9e74-f76259358c08" />

2. Create `args_demo.sh` that:
   - Prints total number of arguments (`$#`)
   - Prints all arguments (`$@`)
   - Prints the script name (`$0`)

<img width="534" height="330" alt="image" src="https://github.com/user-attachments/assets/d57eb56e-f85b-4cdd-9d62-de9621dea445" />

<img width="739" height="341" alt="image" src="https://github.com/user-attachments/assets/2dafe904-8113-456f-9304-3ac7558a050e" />

---

### Task 4: Install Packages via Script
1. Create `install_packages.sh` that:
   - Defines a list of packages: `nginx`, `curl`, `wget`
   - Loops through the list
   - Checks if each package is installed (use `dpkg -s` or `rpm -q`)
   - Installs it if missing, skips if already present
   - Prints status for each package

> Run as root: `sudo -i` or `sudo su`

<img width="926" height="710" alt="image" src="https://github.com/user-attachments/assets/41e06caa-0c8a-4738-b50d-be6c50c68243" />

<img width="717" height="494" alt="image" src="https://github.com/user-attachments/assets/bdaa09b5-6041-4687-ab99-7dd10cdb26c3" />

---

### Task 5: Error Handling
Create `safe_script.sh` that:
   - Uses `set -e` at the top (exit on error)
   - Tries to create a directory `/tmp/devops-test`
   - Tries to navigate into it
   - Creates a file inside
   - Uses `||` operator to print an error if any step fails

<img width="621" height="363" alt="image" src="https://github.com/user-attachments/assets/e0c5ae5c-053b-419b-be75-77ac96161c8e" />

<img width="765" height="388" alt="image" src="https://github.com/user-attachments/assets/c3914747-380e-45d9-a213-c4094526804e" />

---
