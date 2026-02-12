# Day 13 – Linux Volume Management (LVM)

## Challenge Tasks

### Task 1: Check Current Storage
Run: `lsblk`, `pvs`, `vgs`, `lvs`, `df -h`

<img width="881" height="592" alt="image" src="https://github.com/user-attachments/assets/d88fa4f9-a3a7-4f35-b52a-0ac8e6cf6e4d" />

---

### Task 2: Create Physical Volume
```bash
pvcreate /dev/sdb   # or your loop device
pvs
```


---

### Task 3: Create Volume Group
```bash
vgcreate devops-vg /dev/sdb
vgs
```


---

### Task 4: Create Logical Volume
```bash
lvcreate -L 500M -n app-data devops-vg
lvs
```


---

### Task 5: Format and Mount
```bash
mkfs.ext4 /dev/devops-vg/app-data
mkdir -p /mnt/app-data
mount /dev/devops-vg/app-data /mnt/app-data
df -h /mnt/app-data
```


--- 

### Task 6: Extend the Volume
```bash
lvextend -L +200M /dev/devops-vg/app-data
resize2fs /dev/devops-vg/app-data
df -h /mnt/app-data
```


---
