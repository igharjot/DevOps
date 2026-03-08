# Day 41 – Triggers & Matrix Builds

## Challenge Tasks

### Task 1: Trigger on Pull Request
1. Create `.github/workflows/pr-check.yml`
2. Trigger it only when a pull request is **opened or updated** against `main`
3. Add a step that prints: `PR check running for branch: <branch name>`
4. Create a new branch, push a commit, and open a PR
5. Watch the workflow run automatically
   
<img width="950" height="811" alt="image" src="https://github.com/user-attachments/assets/40d31de1-b9ed-474d-81fe-ae7d730633b7" />

<img width="939" height="870" alt="image" src="https://github.com/user-attachments/assets/8a65593d-49db-4f98-bc49-437720bc32dc" />

**Verify:**
<img width="951" height="876" alt="image" src="https://github.com/user-attachments/assets/04ac644d-7cfa-4fb5-bb46-ab34cb4e99be" />

---

### Task 2: Scheduled Trigger
1. Add a `schedule:` trigger to any workflow using cron syntax
2. Set it to run every day at midnight UTC

<img width="692" height="494" alt="image" src="https://github.com/user-attachments/assets/100db5e7-a02f-4870-8366-a8269abdc747" />

3. What is the cron expression for every Monday at 9 AM?
Ans.
```
on:
  schedule:
    - cron: '0 9 * * 1'
```
---

### Task 3: Manual Trigger
1. Create `.github/workflows/manual.yml` with a `workflow_dispatch:` trigger
2. Add an **input** that asks for an `environment` name (staging/production)
3. Print the input value in a step
4. Go to the **Actions** tab → find the workflow → click **Run workflow**

<img width="1200" height="1002" alt="image" src="https://github.com/user-attachments/assets/a1845c88-768f-4f76-8906-596636044a97" />

**Verify:**

<img width="956" height="873" alt="image" src="https://github.com/user-attachments/assets/d1b69eff-7be7-4000-bebe-4995f8ea0159" />

<img width="958" height="863" alt="image" src="https://github.com/user-attachments/assets/d1a55f03-b92c-44a0-b2fe-85faad62629e" />

---

### Task 4: Matrix Builds
Create `.github/workflows/matrix.yml` that:
1. Uses a matrix strategy to run the same job across:
   - Python versions: `3.10`, `3.11`, `3.12`
2. Each job installs Python and prints the version
3. Watch all 3 run in parallel

<img width="963" height="629" alt="image" src="https://github.com/user-attachments/assets/eecdaae9-0007-4ad0-895f-8220d023236f" />

<img width="958" height="877" alt="image" src="https://github.com/user-attachments/assets/f644fa0c-be9c-45cb-8cd4-36b148174151" />

Then extend the matrix to also include 2 operating systems.

<img width="960" height="1014" alt="image" src="https://github.com/user-attachments/assets/329c39f5-f4fe-4fef-b897-b58b3452c281" />

<img width="956" height="878" alt="image" src="https://github.com/user-attachments/assets/778777f9-8e95-454f-8a25-7a28ccefe655" />

---

### Task 5: Exclude & Fail-Fast
1. In your matrix, **exclude** one specific combination (e.g., Python 3.10 on Windows)
2. Set `fail-fast: false` — trigger a failure in one job and observe what happens to the rest

<img width="942" height="807" alt="image" src="https://github.com/user-attachments/assets/eaa36122-3188-4dc2-aa31-37524eabb7a2" />

<img width="929" height="873" alt="image" src="https://github.com/user-attachments/assets/c9566849-8233-4c42-aa72-79967e90269e" />

3. What does `fail-fast: true` (the default) do vs `false`?
Ans.
*fail-fast: true (default)*
- If one job in the matrix fails,
- GitHub cancels all remaining running and queued jobs.
- Purpose: Save CI time and resources.

*fail-fast: false*
- If one job fails,
- Other jobs continue running until all finish.
- Purpose: Useful when testing across many environments and you want full results.

---
