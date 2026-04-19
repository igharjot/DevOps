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
1. Create a step that generates a file.
2. Use `actions/upload-artifact` to save it.
3. After the workflow runs, download the artifact from the Actions tab.

<img width="867" height="629" alt="image" src="https://github.com/user-attachments/assets/a16af3d8-3b47-4248-bf7f-8d2c86e841e4" />

<img width="922" height="819" alt="image" src="https://github.com/user-attachments/assets/4c55b8a8-7075-489f-b578-623e2ffe060d" />

**Verify:** Can you see and download it from GitHub?
<img width="1017" height="748" alt="image" src="https://github.com/user-attachments/assets/3e6a11f5-a36e-4e97-bd40-081941ed3b28" />

---

### Task 4: Download Artifacts Between Jobs
1. Job 1: generate a file and upload it as an artifact
2. Job 2: download the artifact from Job 1 and use it (print its contents)

<img width="852" height="788" alt="image" src="https://github.com/user-attachments/assets/d230f06d-1900-4b4a-8d5d-9ea9b7f95d04" />

<img width="916" height="870" alt="image" src="https://github.com/user-attachments/assets/6072d7ef-1ebb-4dc7-8dc6-79de5db225c2" />

<img width="912" height="868" alt="image" src="https://github.com/user-attachments/assets/5c4e0e1d-3e6f-4e55-895e-706670b906ce" />

Que: When would you use artifacts in a real pipeline?

Ans: Artifacts are used to download the desired files/logs from the github actions runner to our local machine.

---

### Task 5: Run Real Tests in CI
Take a shell script and run it in CI:
1. Add script to the `github-actions-practice` repo
2. Write a workflow that:
   - Checks out the code
   - Installs any dependencies needed
   - Runs the script
   - Fails the pipeline if the script exits with a non-zero code

<img width="1089" height="877" alt="image" src="https://github.com/user-attachments/assets/d069fdf6-1859-4e69-a8f8-ad4aaf20054f" />

<img width="936" height="875" alt="image" src="https://github.com/user-attachments/assets/8778a0c4-ee56-4ca9-8623-4054709395f6" />

<img width="927" height="857" alt="image" src="https://github.com/user-attachments/assets/6914abfb-b0ef-42b0-8f85-16da7e6620cb" />

---

### Task 6: Caching
1. Add `actions/cache` to a workflow that installs dependencies
2. What is being cached and where is it stored?

Ans. The folder 'node_modules/' - which contains all packages installed by npm install/npm ci is being cached.

The cached folder is being stored in the GitHub's own cache storage servers, tied to the repository. It is not stored in the repo or on the runner's disk permanently.

- Each repo gets 10 GB of free cache storage on GitHub.
- Caches are scoped to a branch - PRs can access the base branch's cache but not other PRs' caches.
- A cache entry expires after 7 days of not being accessed.
- When the 10 GB limit is hit, GitHub evicts the oldest/least-used caches automatically.

<img width="978" height="810" alt="image" src="https://github.com/user-attachments/assets/f28dcbb3-bb49-4c73-b5af-6f314ed16aef" />

<img width="920" height="840" alt="image" src="https://github.com/user-attachments/assets/64623f42-efaa-409d-8ac6-8f19a2195d21" />

---
