# Day 47 – Advanced Triggers: PR Events, Cron Schedules & Event-Driven Pipelines

---

## Challenge Tasks

### Task 1: Pull Request Event Types
Create `.github/workflows/pr-lifecycle.yml` that triggers on `pull_request` with **specific activity types**:
1. Trigger on: `opened`, `synchronize`, `reopened`, `closed`
2. Add steps that:
   - Print which event type fired: `${{ github.event.action }}`
   - Print the PR title: `${{ github.event.pull_request.title }}`
   - Print the PR author: `${{ github.event.pull_request.user.login }}`
   - Print the source branch and target branch
3. Add a conditional step that only runs when the PR is **merged** (closed + merged = true)

<img width="893" height="771" alt="image" src="https://github.com/user-attachments/assets/1ddf6fd4-b8bf-4a4a-bf68-ffdbd19c6dfd" />

Test it: create a PR, push an update to it, then merge it. Watch the workflow fire each time with a different event type.

<img width="1099" height="864" alt="image" src="https://github.com/user-attachments/assets/aebd3db4-3b9d-4dcf-8786-82719d55515f" />

---

### Task 2: PR Validation Workflow
Create `.github/workflows/pr-checks.yml`.
1. Trigger on `pull_request` to `main`
2. Add a job `file-size-check` that:
   - Checks out the code
   - Fails if any file in the PR is larger than 1 MB
3. Add a job `branch-name-check` that:
   - Reads the branch name from `${{ github.head_ref }}`
   - Fails if it doesn't follow the pattern `feature/*`, `fix/*`, or `docs/*`
4. Add a job `pr-body-check` that:
   - Reads the PR body: `${{ github.event.pull_request.body }}`
   - Warns (but doesn't fail) if the PR description is empty

<img width="833" height="881" alt="image" src="https://github.com/user-attachments/assets/bb800642-0922-42c0-af16-201ca8225ee3" />

---

### Task 3: Scheduled Workflows (Cron Deep Dive)
Create `.github/workflows/scheduled-tasks.yml`:
1. Add a `schedule` trigger with cron: `'30 2 * * 1'` (every Monday at 2:30 AM UTC)
2. Add **another** cron entry: `'0 */6 * * *'` (every 6 hours)
3. In the job, print which schedule triggered using `${{ github.event.schedule }}`
4. Add a step that acts as a **health check** - curl a URL and check the response code

Write in your notes:
- The cron expression for: every weekday at 9 AM IST : `30 3 * * 1-5`
- The cron expression for: first day of every month at midnight : `0 0 1 * *`
- Why GitHub says scheduled workflows may be delayed or skipped on inactive repos?

Ans: GitHub runs scheduled workflows on shared infrastructure across millions of repos. During high-load periods, jobs are queued and run when capacity is available - there is no SLA on exact execution time. Delays of 15–60 minutes are common.

More critically: if a public repo has had no activity for 60 days, GitHub automatically disables its scheduled workflows entirely to conserve resources. 

**Important:** Also add `workflow_dispatch`.

<img width="871" height="705" alt="image" src="https://github.com/user-attachments/assets/38fb4191-58db-4553-89a5-46655166da95" />

<img width="937" height="673" alt="image" src="https://github.com/user-attachments/assets/5864ead5-0d8d-4754-ad65-bcb59feb17ef" />

---

### Task 4: Path & Branch Filters
Create `.github/workflows/smart-triggers.yml`:
1. Trigger on push but **only** when files in `src/` or `app/` change:
   ```yaml
   on:
     push:
       paths:
         - 'src/**'
         - 'app/**'
   ```
2. Add `paths-ignore` in a second workflow that skips runs when only docs change:
   ```yaml
   paths-ignore:
     - '*.md'
     - 'docs/**'
   ```
3. Add branch filters to only trigger on `main` and `release/*` branches
4. Test it: push a change to a `.md` file — does the workflow skip?

<img width="717" height="428" alt="image" src="https://github.com/user-attachments/assets/89f922a1-1d49-4930-9096-8b54135c6080" />

<img width="679" height="448" alt="image" src="https://github.com/user-attachments/assets/552918df-9d7b-468e-96ab-8bb040a2c6d5" />

<img width="943" height="682" alt="image" src="https://github.com/user-attachments/assets/dba3c1d7-83cc-4214-b37b-0c800a8ad172" />

*Que.* When would you use `paths` vs `paths-ignore`?

*Ans.* When only a few dirs should trigger the workflow, 'paths:' should be used.

When almost everything should trigger, except a few dirs; 'paths-ignore:' should be used.

---

### Task 5: `workflow_run` — Chain Workflows Together
Create two workflows:
1. `.github/workflows/tests.yml` — runs tests on every push
2. `.github/workflows/deploy-after-tests.yml` — triggers **only after** `tests.yml` completes successfully:
   ```yaml
   on:
     workflow_run:
       workflows: ["Run Tests"]
       types: [completed]
   ```
3. In the deploy workflow, add a conditional:
   - Only proceed if the triggering workflow **succeeded** (`${{ github.event.workflow_run.conclusion == 'success' }}`)
   - Print a warning and exit if it failed

<img width="661" height="502" alt="image" src="https://github.com/user-attachments/assets/1f46af1d-19ef-4f3a-95fe-8b8dd8577261" />

<img width="904" height="760" alt="image" src="https://github.com/user-attachments/assets/583ff193-b78b-441f-9946-29705acaa808" />

**Verify:**
-

<img width="921" height="702" alt="image" src="https://github.com/user-attachments/assets/5b7bafa3-32be-4df4-9b25-f39f2b718fd7" />

<img width="926" height="773" alt="image" src="https://github.com/user-attachments/assets/dd209bdd-c997-4bf7-a151-d0b7beeb63bd" />

---

### Task 6: `repository_dispatch` — External Event Triggers
1. Create `.github/workflows/external-trigger.yml` with trigger `repository_dispatch`
2. Set it to respond to event type: `deploy-request`
3. Print the client payload: `${{ github.event.client_payload.environment }}`
4. Trigger it using ` Invoke-RestMethod` :
```bash
  Invoke-RestMethod `
  -Method POST `
  -Uri "https://api.github.com/repos/<owner>/<repo>/dispatches" `
  -Headers @{
    "Authorization" = "Bearer <your_token>"
    "Accept"        = "application/vnd.github+json"
  } `
  -ContentType "application/json" `
  -Body '{"event_type":"deploy-request","client_payload":{"environment":"production"}}'
  
```

<img width="1858" height="945" alt="image" src="https://github.com/user-attachments/assets/fcaec351-acdf-43a3-bc59-20b6608fde42" />

-

*Que.* When would an external system (like a Slack bot or monitoring tool) trigger a pipeline?

*Ans.* When a git event (push/PR) isn't the trigger - instead, something external decides when the pipeline should run:

- Slack bot — /deploy production triggers a workflow
- Monitoring tool — Datadog detects errors → triggers auto-rollback
- External CI — Jenkins finishes a build → hands off to GitHub Actions
- Precise scheduling — AWS EventBridge fires at exact times (more reliable than GitHub's schedule)
- Third-party webhook — CMS publishes content → triggers a build


---
