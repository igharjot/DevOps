# Day 44 – Secrets, Artifacts & Running Real Tests in CI

## Challenge Tasks

### Task 1: GitHub Secrets
1. Go to your repo → Settings → Secrets and Variables → Actions
2. Create a secret called `MY_SECRET_MESSAGE`
3. Create a workflow that reads it and prints: `The secret is set: true`.
4. Try to print `${{ secrets.MY_SECRET_MESSAGE }}` directly.

<img width="740" height="499" alt="image" src="https://github.com/user-attachments/assets/b59a0350-0a5b-4d27-a221-b113793c6bbd" />

<img width="934" height="570" alt="image" src="https://github.com/user-attachments/assets/8ce253ba-66fa-428b-87f1-6eba1ed0ba6b" />

Que: Why should you never print secrets in CI logs?

Ans: One should never expose their sensitive information like secrets in the CI logs as it can be seen by anyone if the repository is public.

---

### Task 2: Use Secrets as Environment Variables
1. Pass a secret to a step as an environment variable
2. Use it in a shell command without ever hardcoding it
3. Add `DOCKER_USERNAME` and `DOCKER_TOKEN` as secrets

<img width="837" height="721" alt="image" src="https://github.com/user-attachments/assets/1f22ee90-11ff-4fb7-a017-101f2fd0feeb" />

<img width="905" height="819" alt="image" src="https://github.com/user-attachments/assets/5de29ba1-c3b1-4cbf-b3dd-8e84c1804125" />

<img width="610" height="473" alt="image" src="https://github.com/user-attachments/assets/597021d4-6428-446e-882d-5b76db210f89" />

---

### Task 3: Upload Artifacts
1. Create a step that generates a file — e.g., a test report or a log file
2. Use `actions/upload-artifact` to save it
3. After the workflow runs, download the artifact from the Actions tab

**Verify:** Can you see and download it from GitHub?

---

### Task 4: Download Artifacts Between Jobs
1. Job 1: generate a file and upload it as an artifact
2. Job 2: download the artifact from Job 1 and use it (print its contents)

When would you use artifacts in a real pipeline?

---
### Task 5: Run Real Tests in CI
Take any script from your earlier days (Python or Shell) and run it in CI:
1. Add your script to the `github-actions-practice` repo
2. Write a workflow that:
   - Checks out the code
   - Installs any dependencies needed
   - Runs the script
   - Fails the pipeline if the script exits with a non-zero code
3. Intentionally break the script — verify the pipeline goes red
4. Fix it — verify it goes green again

---

