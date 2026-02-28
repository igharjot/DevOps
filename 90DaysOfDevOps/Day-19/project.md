# Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab

## Challenge Tasks

### Task 1: Log Rotation Script
Create `log_rotate.sh` that:
1. Takes a log directory as an argument (e.g., `/var/log/myapp`)
2. Compresses `.log` files older than 7 days using `gzip`
3. Deletes `.gz` files older than 30 days
4. Prints how many files were compressed and deleted
5. Exits with an error if the directory doesn't exist

<img width="941" height="958" alt="image" src="https://github.com/user-attachments/assets/f67a40c4-38ee-41fc-b0df-c2c00a35446d" />
<img width="752" height="377" alt="image" src="https://github.com/user-attachments/assets/a92e350b-6d00-4171-9d96-7eac6980b3e1" />


---

### Task 2: Server Backup Script
Create `backup.sh` that:
1. Takes a source directory and backup destination as arguments
2. Creates a timestamped `.tar.gz` archive (e.g., `backup-2026-02-08.tar.gz`)
3. Verifies the archive was created successfully
4. Prints archive name and size
5. Deletes backups older than 14 days from the destination
6. Handles errors — exit if source doesn't exist

<img width="852" height="427" alt="image" src="https://github.com/user-attachments/assets/98772b9b-eca6-466f-8834-dec1f639ec1f" />

<img width="942" height="968" alt="image" src="https://github.com/user-attachments/assets/937f95aa-d0f2-4f08-8b40-60bb2e265466" />

---
### Task 3: Crontab
Commands:
   - Run `crontab -e` choose 1 and press enter.
   - Run `log_rotate.sh` every day at 2 AM
   - Run `backup.sh` every Sunday at 3 AM
   - Run a health check script every 5 minutes
   - Run `crontab -l`

<img width="943" height="575" alt="image" src="https://github.com/user-attachments/assets/98d4aacc-464e-4727-8f9a-5d556486701e" />

---

### Task 4: Combine — Scheduled Maintenance Script
Create `maintenance.sh` that:
1. Calls your log rotation function
2. Calls your backup function
3. Logs all output to `/var/log/maintenance.log` with timestamps
4. Write the cron entry to run it daily at 1 AM

<img width="790" height="540" alt="image" src="https://github.com/user-attachments/assets/98f4b6e2-9948-4f97-8c66-aeda1b8da763" />

<img width="889" height="255" alt="image" src="https://github.com/user-attachments/assets/85500f15-57b3-4782-b5e4-7a3e50e4f87a" />

---
