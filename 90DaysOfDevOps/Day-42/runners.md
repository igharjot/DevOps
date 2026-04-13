# Day 42 – Runners: GitHub-Hosted & Self-Hosted

## Challenge Tasks

### Task 1: GitHub-Hosted Runners
1. Create a workflow with 3 jobs, each on a different OS:
   - `ubuntu-latest`
   - `windows-latest`
   - `macos-latest`
2. In each job, print:
   - The OS name
   - The runner's hostname
   - The current user running the job
3. Watch all 3 run in parallel

<img width="781" height="771" alt="image" src="https://github.com/user-attachments/assets/9d6ba278-a9f5-4906-b687-85f5f8288238" />

<img width="951" height="647" alt="image" src="https://github.com/user-attachments/assets/54660754-9a8c-4e6d-a81b-e4008330cb5a" />

What is a GitHub-hosted runner? Who manages it?
Ans: GitHub-hosted runners are the different runners provided by the github only, for example- ubuntu, macOS, windows, etc.

These are fully managed by the github actions only.

---

### Task 2: Explore What's Pre-installed
1. On the `ubuntu-latest` runner, run a step that prints:
   - Docker version
   - Python version
   - Node version
   - Git version
  
<img width="748" height="466" alt="image" src="https://github.com/user-attachments/assets/980c3301-2cb2-416a-bd11-4023f8bb8770" />



2. Look up the GitHub docs for the full list of pre-installed software on `ubuntu-latest`

Why does it matter that runners come with tools pre-installed?
Ans: This helps the developer provide pre-installed environment to exucute its work freely without installing the packages before.

---

### Task 3: Set Up a Self-Hosted Runner
1. Go to your GitHub repo → Settings → Actions → Runners → **New self-hosted runner**
2. Choose Linux as the OS
3. Follow the instructions to download and configure the runner on:
   - Your local machine, OR
   - A cloud VM (EC2, Utho, or any VPS)
4. Start the runner — verify it shows as **Idle** in GitHub

**Verify:**

<img width="648" height="251" alt="image" src="https://github.com/user-attachments/assets/960fb637-a930-46da-b738-dfbef7dd4bc4" />


---

### Task 4: Use Your Self-Hosted Runner
1. Create `.github/workflows/self-hosted.yml`
2. Set `runs-on: self-hosted`
3. Add steps that:
   - Print the hostname of the machine (it should be YOUR machine/VM)
   - Print the working directory
   - Create a file and verify it exists on your machine after the run
4. Trigger it and watch it run on your own hardware

**Verify:**

---

### Task 5: Labels
1. Add a **label** to your self-hosted runner (e.g., `my-linux-runner`)
2. Update your workflow to use `runs-on: [self-hosted, my-linux-runner]`
3. Trigger it — does it still pick up the job?

Why are labels useful when you have multiple self-hosted runners?

---

### Task 6: GitHub-Hosted vs Self-Hosted
Fill this in your notes:
```
|                     | GitHub-Hosted | Self-Hosted |
|---------------------|---------------|-------------|
| Who manages it?     | ?             |             |
| Cost                | ?             | ?           |
| Pre-installed tools | ?             | ?           |
| Good for            | ?             | ?           |
| Security concern    | ?             | ?           |
```
---
