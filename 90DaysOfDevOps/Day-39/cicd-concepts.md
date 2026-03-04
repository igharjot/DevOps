# Day 39 – What is CI/CD?

## Challenge Tasks

### Task 1: The Problem

Think about a team of 5 developers all pushing code to the same repo manually deploying to production.

Write in your notes:

1. What can go wrong?
Many things can break when multiple developers deploy manually:

- Code conflicts : Two developers may deploy different versions of code and overwrite each other’s changes.
- Human error : Someone might forget a step (run migrations, install dependencies, restart services, etc.).
- Wrong version deployed : A developer might accidentally deploy an old branch instead of the latest code.
- Downtime : Incorrect deployment steps can crash the production server.
- Untracked changes : Someone may modify files directly on the server and the repo no longer matches production.
- No rollback strategy : If the deployment breaks the system, it may take time to manually fix or revert.
- Dependency mismatch : Production environment may not have the same packages or versions.

2. What does "it works on my machine" mean and why is it a real problem?
“It works on my machine” means:
> The code runs correctly on the developer’s computer but fails on another developer’s system or in production.

This happens because environments are different:
Examples:
- Different OS (Windows vs Linux)
- Different library versions
- Missing environment variables
- Different Node/Python/Java versions
- Missing dependencies

3. How many times a day can a team safely deploy manually?
Usually very few times. Typical manual deployment limits: 1–2 deployments per day safely
Each deployment requires:
- coordination
- testing
- monitoring
  
*Why manual deployments don’t scale:*
- Time consuming
- High risk of mistakes
- Requires human supervision

**With CI/CD automation, teams can deploy: 10–100+ times per day, safely and consistently**

Example: companies like Netflix, Amazon, and Google deploy thousands of times per day using automated pipelines.

---

### Task 2: CI vs CD

Research and write short definitions (2-3 lines each):

1. **Continuous Integration** — what happens, how often, what it catches
2. **Continuous Delivery** — how it's different from CI, what "delivery" means
3. **Continuous Deployment** — how it differs from Delivery, when teams use it

Write one real-world example for each.

---

### Task 3: Pipeline Anatomy

A pipeline has these parts — write what each one does:

- **Trigger** — what starts the pipeline
- **Stage** — a logical phase (build, test, deploy)
- **Job** — a unit of work inside a stage
- **Step** — a single command or action inside a job
- **Runner** — the machine that executes the job
- **Artifact** — output produced by a job

---

### Task 4: Draw a Pipeline

Draw a CI/CD pipeline for this scenario:

> A developer pushes code to GitHub. The app is tested, built into a Docker image, and deployed to a staging server.

Include at least 3 stages. Hand-drawn and photographed is perfectly fine.

---

### Task 5: Explore in the Wild

1. Open any popular open-source repo on GitHub (Kubernetes, React, FastAPI — pick one you know)
2. Find their `.github/workflows/` folder
3. Open one workflow YAML file
4. Write in your notes:
   - What triggers it?
   - How many jobs does it have?
   - What does it do? (best guess)

---
