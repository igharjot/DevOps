# Day 46 – Reusable Workflows & Composite Actions

---

## Challenge Tasks

### Task 1: Understand `workflow_call`

1. What is a **reusable workflow**?

*Ans:* A reusable workflow is a pre-defined workflow file that can be called by other workflows.


2. What is the `workflow_call` trigger?

*Ans:* It's the event that marks a workflow as reusable. Adding it to on: exposes the workflow so other workflows can invoke it.
It also lets us declare inputs and secrets that callers can pass.


3. How is calling a reusable workflow different from using a regular action (`uses:`)?

*Ans:* Reusable Workflow:
- Runs an entire workflow (multiple jobs).
- 'uses:' placement is at the job level.
- Defined as a .yml workflow file.
- Can have multiple jobs.
- Secrets must be explicitly passed via 'secrets: inherit'.

Regular Action:
- Runs a single step
- 'uses:' placement is at the step level.
- Defined as action.yml + code (JS/Docker/composite).
- Can not have multiple jobs.
- Secrets are inherited automatically.


4. Where must a reusable workflow file live?

*Ans:* The reusable workflow file must be in .github/workflows/ of the GitHub repository.
To call it from another repo, that repo must be:
- Public, or
- In the same organization (with Actions sharing enabled), or
- The same repo


---

### Task 2: Create Your First Reusable Workflow
Create `.github/workflows/reusable-build.yml`:
1. Set the trigger to `workflow_call`
2. Add an `inputs:` section with:
   - `app_name` (string, required)
   - `environment` (string, required, default: `staging`)
3. Add a `secrets:` section with:
   - `docker_token` (required)
4. Create a job that:
   - Checks out the code
   - Prints `Building <app_name> for <environment>`
   - Prints `Docker token is set: true`

<img width="897" height="766" alt="image" src="https://github.com/user-attachments/assets/0bfa8335-c795-4601-aacc-6eb99637534a" />

---

### Task 3: Create a Caller Workflow
Create `.github/workflows/call-build.yml`:
1. Trigger on push to `main`
2. Add a job that uses your reusable workflow:
   ```yaml
   jobs:
     build:
       uses: ./.github/workflows/reusable-build.yml
       with:
         app_name: "my-web-app"
         environment: "production"
       secrets:
         docker_token: ${{ secrets.DOCKER_TOKEN }}
   ```
3. Push to `main` and watch it run

<img width="722" height="451" alt="image" src="https://github.com/user-attachments/assets/b4f8d532-d600-44d6-991a-c410dc88ab68" />

<img width="927" height="775" alt="image" src="https://github.com/user-attachments/assets/145e996a-99fc-43c5-8e21-2e9dbadd19cc" />

---

### Task 4: Add Outputs to the Reusable Workflow
Extend `reusable-build.yml`:
1. Add an `outputs:` section that exposes a `build_version` value
2. Inside the job, generate a version string (e.g., `v1.0-<short-sha>`) and set it as output
3. In your caller workflow, add a second job that:
   - Depends on the build job (`needs:`)
   - Reads and prints the `build_version` output

<img width="792" height="833" alt="image" src="https://github.com/user-attachments/assets/37b965ce-001d-4c88-b3ec-faebab35d60d" />

<img width="785" height="514" alt="image" src="https://github.com/user-attachments/assets/782876c4-9ff8-49af-be55-7645847df357" />

**Verify:**
<img width="913" height="822" alt="image" src="https://github.com/user-attachments/assets/bd886a90-d1e1-41ff-b290-dcd2e61b723f" />

<img width="946" height="541" alt="image" src="https://github.com/user-attachments/assets/3e8547e5-3029-4946-afe3-d8c2a8212ef0" />

---

### Task 5: Create a Composite Action
Create a **custom composite action** in your repo at `.github/actions/setup-and-greet/action.yml`:
1. Define inputs: `name` and `language` (default: `en`)
2. Add steps that:
   - Print a greeting in the specified language
   - Print the current date and runner OS
   - Set an output called `greeted` with value `true`
3. Use the composite action in a new workflow with `uses: ./.github/actions/setup-and-greet`

**Verify:** Does your custom action run and print the greeting?

---

### Task 6: Reusable Workflow vs Composite Action

|                              |             Reusable Workflow          | Composite Action                 |
|------------------------------|----------------------------------------|----------------------------------|
| Triggered by                 | `workflow_call`                        | `uses:` in a step                |
| Can contain jobs?            | Yes                                    | No                               |
| Can contain multiple steps?  | Yes(per job)                           | Yes                              |
| Lives where?                 | .github/workflows/*.yml                | root action.yml                  |
| Can accept secrets directly? | Yes, via secrets:                      | No, must be passed as inputs:    |
| Best for                     | Full pipelines (build → test → deploy) | Reusable step logic within a job |

---
