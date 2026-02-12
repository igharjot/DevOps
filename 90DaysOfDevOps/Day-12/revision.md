# Day 12 – Breather & Revision (Days 01–11)

**1) Which 3 commands save you the most time right now, and why?**

   Ans- The three commands which saves me the most time are :
   - chmod-easier to change permissions of any file or directory.
   - sudo su-don't need to write 'sudo' before every root command after executing this command.
   - cd & ls-most time-saving and important command. 

---

**2) How do you check if a service is healthy? List the exact 2–3 commands you’d run first.**
   Ans- Linux commands to check if a service is healthy or not are :
   - systemctl status <service-name>
   - journalctl -u <service-name>
   - ss -tulnp | grep <port>

---

**3) How do you safely change ownership and permissions without breaking access? Give one example command.**
   Ans- We can achieve this by using 'chown' and 'chmod' linux commands.
   - sudo chown -R <owner>:<group> <file-or-dir-name> OR sudo chown <owner>:<group> <path-to-file-or-folder>
   - sudo chmod 764 <file-or-dir-name>

---

**4) What will you focus on improving in the next 3 days?**
   Ans- I will focus on the volume attchment to the server by mounting using 'mount' and 'mkfs' commands. I will also practice the physical and logical volumes creation on the server using 'lvm'.

---

## Revision Practice Screenshots:

<img width="928" height="562" alt="image" src="https://github.com/user-attachments/assets/ef6f4f2c-a311-425b-a2d7-3558c4fe570c" />

<img width="673" height="279" alt="Screenshot 2026-02-11 001722" src="https://github.com/user-attachments/assets/6958da27-ba0b-4b8d-8b5e-8ec37d4c8a9e" />

<img width="704" height="332" alt="Screenshot 2026-02-11 000133" src="https://github.com/user-attachments/assets/e186343d-7f95-4afd-b6d2-b2be0e429cee" />

<img width="847" height="321" alt="Screenshot 2026-02-09 000903" src="https://github.com/user-attachments/assets/3ae5c8eb-6a4a-4d78-995c-00e2c381201b" />

<img width="938" height="644" alt="Screenshot 2026-02-05 192641" src="https://github.com/user-attachments/assets/4aa044c5-b9a9-4d0f-a4a0-8871b9a629f5" />


---
