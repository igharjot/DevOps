# Day 13 – Linux Volume Management (LVM)

## Challenge Tasks

### Task 1: Check Current Storage
Run: `lsblk`, `pvs`, `vgs`, `lvs`, `df -h`

<img width="881" height="592" alt="image" src="https://github.com/user-attachments/assets/d88fa4f9-a3a7-4f35-b52a-0ac8e6cf6e4d" />

<img width="835" height="743" alt="image" src="https://github.com/user-attachments/assets/350968a4-3a55-44d6-b0d4-afd0bed02272" />

---

### Task 2: Create Physical Volume
```bash
pvcreate /dev/nvme1n1
pvdisplay
pvs
```
<img width="742" height="360" alt="image" src="https://github.com/user-attachments/assets/5fb44764-784f-45f9-b09a-667e11b501dc" />

---

### Task 3: Create Volume Group
```bash
vgcreate my_vol_grp /dev/nvme1n1
pvdisplay
vgs
```
<img width="716" height="251" alt="image" src="https://github.com/user-attachments/assets/b03f94cb-f4ba-4804-9d29-70a8b21592f5" />

---

### Task 4: Create Logical Volume
```bash
lvcreate -L 7.5g my_vol_grp -n log_vol_1
lvcreate -L 4g my_vol_grp -n log_vol_2
lvdisplay
lvs
```
<img width="866" height="741" alt="image" src="https://github.com/user-attachments/assets/5a5e78f1-ed9d-4502-9bad-b30584fb5d60" />

---

### Task 5: Format and Mount
```bash
mkfs.ext4 /dev/my_vol_grp/log_vol_1
mkfs.ext4 /dev/my_vol_grp/log_vol_2

mkdir -p /mnt/log_vol_1
mkdir -p /mnt/log_vol_2

mount /dev/my_vol_grp/log_vol_1 /mnt/log_vol_1
mount /dev/my_vol_grp/log_vol_2 /mnt/log_vol_2

df -h
```
<img width="762" height="301" alt="image" src="https://github.com/user-attachments/assets/711cd153-3b52-4bdc-97e2-87eadb96e401" />

--- 

### Task 6: Extend the Volume
```bash
sudo su
lvm       # entering lvm command line
lvextend -L +200M /dev/my_vol_grp/log_vol_2
exit      # exit lvm command line
resize2fs /dev/devops-vg/app-data
df -h /mnt/app-data
```
<img width="865" height="735" alt="image" src="https://github.com/user-attachments/assets/351cf238-00a0-4071-82a9-3d1639d6f085" />

---
