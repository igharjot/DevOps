# Day 43 – Jobs, Steps, Env Vars & Conditionals


## Challenge Tasks

### Task 1: Multi-Job Workflow
Create `.github/workflows/multi-job.yml` with 3 jobs:
- `build` — prints "Building the app"
- `test` — prints "Running tests"
- `deploy` — prints "Deploying"

Make `test` run only **after** `build` succeeds.
Make `deploy` run only **after** `test` succeeds.

<img width="827" height="625" alt="image" src="https://github.com/user-attachments/assets/c97ac65d-6c2e-4982-acad-ffc51acb01d3" />

**Verify:** Check the workflow graph in the Actions tab — does it show the dependency chain?
<img width="945" height="600" alt="image" src="https://github.com/user-attachments/assets/d229739c-fdb9-4bdd-bbd7-678d54e0fa9c" />

---

### Task 2: Environment Variables
In a new workflow, use environment variables at 3 levels:
1. **Workflow level** — `APP_NAME: myapp`
2. **Job level** — `ENVIRONMENT: staging`
3. **Step level** — `VERSION: 1.0.0`

Print all three in a single step and verify each is accessible.

Then use a **GitHub context variable** to print the commit SHA and the actor (who triggered the run).

<img width="824" height="698" alt="image" src="https://github.com/user-attachments/assets/9d7fbcf8-5a47-47d7-ab6a-62c6a280e1ee" />

<img width="956" height="725" alt="image" src="https://github.com/user-attachments/assets/10683e77-ae72-442d-8e3e-6cd0004586d8" />

---

### Task 3: Job Outputs
1. Create a job that **sets an output** — e.g., today's date as a string
2. Create a second job that **reads that output** and prints it
3. Pass the value using `outputs:` and `needs.<job>.outputs.<name>`

<img width="917" height="567" alt="image" src="https://github.com/user-attachments/assets/f8856c73-8ba8-4407-a778-ccda0ef7ef62" />

<img width="939" height="684" alt="image" src="https://github.com/user-attachments/assets/0438af1d-a4f9-4397-8c68-523476ef2949" />

Que: Why would you pass outputs between jobs?

Ans: Jobs run in complete isolation. They don't share memory, filesystem or environment. So if Job 2 needs a value that Job 1 calculated, outputs are the only way to pass it.

---

### Task 4: Conditionals
In a workflow, add:
1. A step that only runs when the branch is `main`
2. A step that only runs when the previous step **failed**
3. A job that only runs on **push** events, not on pull requests
4. A step with `continue-on-error: true`

<img width="958" height="946" alt="image" src="https://github.com/user-attachments/assets/407ff49a-c469-4ce6-81b0-8650e9d10f91" />

<img width="929" height="788" alt="image" src="https://github.com/user-attachments/assets/53a6a5e0-a99c-4ddc-89c7-be9a67c63f9e" />

<img width="939" height="517" alt="image" src="https://github.com/user-attachments/assets/5d77dc03-f2ea-4784-9255-0d6505636ca3" />

---
### Task 5: Putting It Together
Created `.github/workflows/smart-pipeline.yml` that:
1. Triggers on push to any branch
2. Has a `lint` job and a `test` job running in parallel
3. Has a `summary` job that runs after both, prints whether it's a `main` branch push or a feature branch push, and prints the commit message

<img width="836" height="693" alt="image" src="https://github.com/user-attachments/assets/ec8b39bc-1bc0-4360-b288-2834fbe35d44" />

<img width="940" height="602" alt="image" src="https://github.com/user-attachments/assets/a6574a93-afea-4acd-9f37-e4a5471ef5ba" />

<img width="932" height="587" alt="image" src="https://github.com/user-attachments/assets/a67bec6a-1794-40bc-9923-3fdeb0d44798" />

---
