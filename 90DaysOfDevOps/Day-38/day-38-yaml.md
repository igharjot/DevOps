# Day 38 – YAML Basics

## Challenge Tasks

### Task 1: Key-Value Pairs

Create `person.yaml` that describes yourself with:

- `name`
- `role`
- `experience_years`
- `learning` (a boolean)

**Verify:** Run `cat person.yaml`

<img width="948" height="857" alt="image" src="https://github.com/user-attachments/assets/59497e75-abbb-40e5-9516-03b4d933094d" />

---

### Task 2: Lists

Add to `person.yaml`:

- `tools` — a list of 5 DevOps tools you know or are learning
- `hobbies` — a list using the inline format `[item1, item2]`

<img width="913" height="993" alt="image" src="https://github.com/user-attachments/assets/820b98e2-9b53-46dc-b6ac-7d5ae5b0fcca" />

**Question: What are the two ways to write a list in YAML?**
Answer:
*1. Block Style (Dash - format)*

Each item starts with a dash and space.
```YAML
tools:
  - Git
  - Docker
  - AWS
  - Linux
```
✔ Most common
✔ Clean and readable
✔ Used in GitHub Actions a lot

*2. Inline Style (Bracket [] format)*

Items are written inside square brackets, separated by commas.
```YAML
hobbies: [Listening to hip hop, Coding, Gaming]
```
✔ Shorter
✔ Good for small lists
✔ Less readable for long lists

---

### Task 3: Nested Objects

Create `server.yaml` that describes a server:

- `server` with nested keys: `name`, `ip`, `port`
- `database` with nested keys: `host`, `name`, `credentials` (nested further: `user`, `password`)

<img width="949" height="988" alt="image" src="https://github.com/user-attachments/assets/79c455d2-0ac6-4cdf-861f-95d657085994" />

---

### Task 4: Multi-line Strings

In `server.yaml`, add a `startup_script` field using:

1. The `|` block style (preserves newlines)
2. The `>` fold style (folds into one line)
3. 
<img width="943" height="997" alt="image" src="https://github.com/user-attachments/assets/8c9dbbd1-f967-4635-b77f-d778d6631a4b" />

Write in your notes: When would you use `|` vs `>`?
```
|          Use '|'        |               Use '>'          |
|-------------------------|--------------------------------|
| Shell scripts           | Long text paragraphs           |
| Multi-line commands     | Long descriptions              |
| Code blocks             | Messages                       |
| When formatting matters | When formatting doesn't matter |
```

---

### Task 5: Validate Your YAML

1. Install `yamllint` or use an online validator
2. Validate both your YAML files
3. Intentionally break the indentation — what error do you get?
4. Fix it and validate again

### person.yml
Correct format:
<img width="920" height="606" alt="image" src="https://github.com/user-attachments/assets/7b82f0a7-683b-455f-827e-548dfc95859f" />

.

Wrong Indentation:
<img width="909" height="657" alt="image" src="https://github.com/user-attachments/assets/6464dbc2-b2e3-42c5-92b2-f15e48f5b18a" />

---

### server.yml
Correct format:
<img width="925" height="651" alt="image" src="https://github.com/user-attachments/assets/66b0d30c-079a-4beb-b0cf-fa0dfe168d99" />

.

Wrong Indentation:
<img width="925" height="678" alt="image" src="https://github.com/user-attachments/assets/d5a0694f-7f8a-4928-971e-be3cf36d33f8" />

---

### Task 6: Spot the Difference

Read both blocks and write what's wrong with the second one:

```yaml
# Block 1 - correct
name: devops
tools:
  - docker
  - kubernetes
```

```yaml
# Block 2 - broken
name: devops
tools:
  - docker
    - kubernetes
```
**ANSWER:** Wrong indentation in Block-2; '-kubernetes' is a tab space away, while '-docker' is 2 spaces away(which is the correct format).

---
