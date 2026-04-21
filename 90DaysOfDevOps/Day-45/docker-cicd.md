# Day 45 – Docker Build & Push in GitHub Actions

## Challenge Tasks

### Task 1: Prepare
1. Use a simple Dockerfile
2. Add the Dockerfile to your `github-actions-practice` repo
3. Make sure `DOCKER_USERNAME` and `DOCKER_TOKEN` secrets are set from Day 44.

<img width="724" height="588" alt="image" src="https://github.com/user-attachments/assets/8ed94f13-7695-4032-be58-96cea477a59b" />

---

### Task 2: Build the Docker Image in CI
Create `.github/workflows/docker-publish.yml` that:
1. Triggers on push to `main`
2. Checks out the code
3. Builds the Docker image and tags it

<img width="786" height="634" alt="image" src="https://github.com/user-attachments/assets/e9927869-18ef-4e08-b6e7-48c96e1c6d2d" />

---

### Task 3: Push to Docker Hub
Add steps to:
1. Log in to Docker Hub using your secrets
2. Tag the image as `username/repo:latest` and also `username/repo:sha-<short-commit-hash>`
3. Push both tags

<img width="952" height="756" alt="image" src="https://github.com/user-attachments/assets/8c113e65-6c7d-4ba0-b842-1d850a12f26b" />

**Verify:**

<img width="922" height="626" alt="image" src="https://github.com/user-attachments/assets/fca90f5b-f9fa-4881-bfc9-7f5595dc6bc6" />

---

### Task 4: Only Push on Main
Add a condition so the push step only runs on the `main` branch — not on feature branches or PRs.

<img width="722" height="623" alt="image" src="https://github.com/user-attachments/assets/fca14a59-758d-45ae-be5f-10ae3116f92d" />

---

### Task 5: Add a Status Badge
1. Get the badge URL for your `docker-publish` workflow from the Actions tab
2. Add it to your `README.md`
3. Push — the badge should show green


---

### Task 6: Pull and Run It
1. On your local machine (or a cloud server), pull the image you just pushed
2. Run it
3. Confirm it works

---
