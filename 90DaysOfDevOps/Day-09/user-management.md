# Day 09 – Linux User & Group Management Challenge

## Task 1: Create Users

### Commands used are-
- sudo useradd tokyo
- sudo useradd berlin
- sudo useradd professor
- cat /etc/passwd

<img width="1249" height="729" alt="image" src="https://github.com/user-attachments/assets/27a392e4-a6a8-4a59-80d7-771967277fac" />
<img width="847" height="321" alt="image" src="https://github.com/user-attachments/assets/8351743d-e261-4d98-8296-33d0069ded82" />

---

## Task 2: Create Groups

### Commands used are-
- sudo groupadd developers
- sudo groupadd admins
- cat /etc/group

<img width="833" height="419" alt="image" src="https://github.com/user-attachments/assets/98049a3b-1504-4596-8165-263fa39600ae" />
<img width="828" height="426" alt="image" src="https://github.com/user-attachments/assets/a983408e-66d6-4dd0-8f69-2e574d780efa" />

---

## Task 3: Assign to Groups

### Commands used are-
- sudo gpasswd -a tokyo developers
- sudo gpasswd -a berlin developers
- sudo gpasswd -a berlin admins
- sudo gpasswd -a professor admins
- cat /etc/group

<img width="824" height="286" alt="image" src="https://github.com/user-attachments/assets/1ee32dcc-8c5f-408d-9540-b3003b1b2952" />
<img width="805" height="314" alt="image" src="https://github.com/user-attachments/assets/09370b45-0ef5-4ecc-b6ca-6db47e413575" />


---

## Task 4: Shared Directory

### Commands used are-
- sudo mkdir /opt/dev-project
- sudo chown root:developer /opt/dev-project
- sudo chmod 775 dev-project
- su tokyo
- su berlin
- ls -l

<img width="880" height="731" alt="image" src="https://github.com/user-attachments/assets/2a826155-69c1-482d-8b0e-ba43d989a32b" />


---

## Task 5: Team Workspace

### Commands used are-
- sudo useradd -m nairobi
- sudo groupadd project-team
- cat /etc/group
- cat /etc/passwd
- sudo usermod -aG project-team tokyo
- sudo usermod -aG project-team nairobi
- sudo mkdir /opt/team-workspace
- sudo chown root:team-project /opt/team-workspace
- ls -l
- sudo chmod 775 team-workspace

<img width="927" height="655" alt="image" src="https://github.com/user-attachments/assets/5a295cc8-d76d-419c-8183-3ac7bd0dbfa7" />


---
