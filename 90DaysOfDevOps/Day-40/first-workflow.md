# Day 40 – Your First GitHub Actions Workflow

## Challenge Tasks

### Task 1: Set Up
1. Create a new **public** GitHub repository called `github-actions-practice`
2. Clone it locally
3. Create the folder structure: `.github/workflows/`

<img width="1156" height="1024" alt="image" src="https://github.com/user-attachments/assets/aa7bd1ce-5de1-4921-9a71-74782a4729d2" />


---

### Task 2: Hello Workflow
Create `.github/workflows/hello.yml` with a workflow that:
1. Triggers on every `push`
2. Has one job called `greet`
3. Runs on `ubuntu-latest`
4. Has two steps:
   - Step 1: Check out the code using `actions/checkout`
   - Step 2: Print `Hello from GitHub Actions!`

Push it. Go to the **Actions** tab on GitHub and watch it run.

<img width="944" height="999" alt="image" src="https://github.com/user-attachments/assets/889f445b-7e2c-43c0-8920-ab9abc1dd9c2" />

<img width="958" height="768" alt="image" src="https://github.com/user-attachments/assets/ca81eb01-2d1c-4f40-8332-cb4f386641c2" />

---

### Task 3: Understand the Anatomy
In a workflow file, what each key does:
- `on:` this key defines what event triggers that workfile.
- `jobs:` jobs are the activities/tasks which is to be performed when the workflow is triggered.
- `runs-on:` specifies the type of runner (machine) that executes a job.
- `steps:` steps are the sequence of actions/commands inside a job.
- `uses:` runs a pre-built GitHub Action created by someone.
- `run:` executes a shell command directly on the runnner.
- `name:` (on a step) - gives a readable label to a step.

---

### Task 4: Add More Steps
Update `hello.yml` to also:
1. Print the current date and time
2. Print the name of the branch that triggered the run
3. List the files in the repo
4. Print the runner's operating system

<img width="1063" height="990" alt="image" src="https://github.com/user-attachments/assets/cb9fc340-c32d-45ed-9d3b-15df9d96edea" />

<img width="954" height="852" alt="image" src="https://github.com/user-attachments/assets/11dac8b2-454f-4ad5-933a-2f90d1716e56" />

---

### Task 5: Break It On Purpose
1. Add a step that runs a command that will **fail**
2. Push and observe what happens in the Actions tab
3. Fix it and push again

---
