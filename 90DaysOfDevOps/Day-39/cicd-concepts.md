# Day 39 – What is CI/CD?

## Challenge Tasks

### Task 1: The Problem

Think about a team of 5 developers all pushing code to the same repo manually deploying to production.

1. What can go wrong?

Ans. Many things can break when multiple developers deploy manually:

- Code conflicts : Two developers may deploy different versions of code and overwrite each other’s changes.
- Human error : Someone might forget a step (run migrations, install dependencies, restart services, etc.).
- Wrong version deployed : A developer might accidentally deploy an old branch instead of the latest code.
- Downtime : Incorrect deployment steps can crash the production server.
- Untracked changes : Someone may modify files directly on the server and the repo no longer matches production.
- No rollback strategy : If the deployment breaks the system, it may take time to manually fix or revert.
- Dependency mismatch : Production environment may not have the same packages or versions.

2. What does "it works on my machine" mean and why is it a real problem?

Ans. “It works on my machine” means:
> The code runs correctly on the developer’s computer but fails on another developer’s system or in production.

This happens because environments are different.
Examples:
- Different OS (Windows vs Linux)
- Different library versions
- Missing environment variables
- Different Node/Python/Java versions
- Missing dependencies

3. How many times a day can a team safely deploy manually?

Ans. Usually very few times. Typical manual deployment limits: 1–2 deployments per day safely
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

1. **Continuous Integration**

Continuous Integration is the practice where developers frequently merge their code into a shared repository, often multiple times a day. Each merge automatically triggers builds and automated tests to detect integration errors early. It helps catch bugs, build failures, and code conflicts quickly.

Example: A team uses GitHub Actions to automatically run tests every time code is pushed to the main branch.

2. **Continuous Delivery** — how it's different from CI, what "delivery" means

Continuous Delivery extends CI by ensuring the application is always in a deployable state. After code passes automated tests, it is automatically built and prepared for release, but deployment to production usually requires manual approval.

Example: After CI tests pass, a pipeline prepares a Docker image and pushes it to a registry, waiting for a developer to approve deployment.

3. **Continuous Deployment** — how it differs from Delivery, when teams use it

Continuous Deployment goes one step further than Continuous Delivery by automatically deploying every change that passes tests directly to production without human intervention. It requires strong automated testing and monitoring.

Example: Companies like Netflix automatically deploy code to production once it passes all automated pipeline tests.

---

### Task 3: Pipeline Anatomy

1. **Trigger** — A Trigger is the event that starts the pipeline. It can be things like pushing code to a repository, creating a pull request, or manually starting the workflow.

Example: A push to the main branch triggers a GitHub Actions pipeline.

2. **Stage** — A Stage is a logical phase of the pipeline that groups related jobs together, such as build, test, or deploy. Stages help organize the workflow and usually run in sequence.

Example: A pipeline may have three stages: build → test → deploy.

3. **Job** — A Job is a unit of work inside a stage that runs on a runner. Each job contains multiple steps and performs a specific task like compiling code or running tests.

Example: A test job runs automated unit tests.

4. **Step** — A Step is a single command or action executed inside a job. Steps run sequentially and can execute scripts or use predefined actions.

Example: Running a command like npm install or npm test.

5. **Runner** — A Runner is the machine (virtual machine or server) that actually executes the pipeline jobs. It provides the environment where the code is built and tested.

Example: GitHub-hosted runners like ubuntu-latest.

6. **Artifact** — An Artifact is a file or output produced by a job that can be saved and used later in the pipeline. Artifacts are often build outputs such as compiled binaries or packaged applications.

Example: A built .jar file or compiled website files stored after the build stage.

---

### Task 4: Draw a Pipeline

Draw a CI/CD pipeline for this scenario:

> A developer pushes code to GitHub. The app is tested, built into a Docker image, and deployed to a staging server.

```
Developer
   │
   │  Push Code
   ▼
GitHub Repository
   │
   │ (Trigger Pipeline)
   ▼
CI/CD Pipeline
   │
   ├── Stage 1: Test
   │       Run automated tests
   │       (unit tests / linting)
   │
   ├── Stage 2: Build
   │       Build Docker image
   │       docker build -t app-image .
   │
   ├── Stage 3: Push Image
   │       Push Docker image to registry
   │       (Docker Hub / ECR / GHCR)
   │
   └── Stage 4: Deploy
           Pull image on staging server
           Run container

                 ▼
           Staging Server
           (App running)
```

---

### Task 5: Explore in the Wild

1. Open any popular open-source repo on GitHub.

I opened Kubernetes github repsitory: https://github.com/facebook/react

2. Find their `.github/workflows/` folder
3. Open one workflow YAML file

I have opened ".github/workflows/compiler_discord_notify.yml" file.

4. Write in your notes:
   - What triggers it?
   ANS. This workflow is triggered by a Pull Request event
   
   - How many jobs does it have?
   ANS. 3 Jobs

   - What does it do?
   ANS. When a pull request is opened, the workflow gets triggered, which then checks if PR author is a member or a collaborator. In the next job, it checks if the quthor is reactcore  maintainer or not. If true, send notification to discord webhook.

---
