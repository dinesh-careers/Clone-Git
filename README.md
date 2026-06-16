If you want to migrate **everything** from the old repository to a new repository:

✅ All branches
✅ All commit history (logs)
✅ All tags
✅ All remote refs

Use **Git Mirror**.

### Step 1: Clone the old repository as a mirror

```bash id="7c7zcf"
git clone --mirror https://github.com/OLD-ACCOUNT/OLD-REPO.git
```

This creates:

```text id="r7w1x5"
OLD-REPO.git
```

---

### Step 2: Go into the mirrored repository

```bash id="i1w6xp"
cd OLD-REPO.git
```

---

### Step 3: Point it to the new repository

Create an empty repository in Account B, then:

```bash id="2zwxgn"
git remote set-url origin https://github.com/NEW-ACCOUNT/NEW-REPO.git
```

Verify:

```bash id="i4qpkd"
git remote -v
```

---

### Step 4: Push everything

```bash id="7tmc8z"
git push --mirror
```

This copies:

* main
* master
* develop
* stage
* feature/*
* hotfix/*
* all tags
* complete commit history

---

### Verify

```bash id="b9mn2m"
git ls-remote
```

Or open the new GitHub repository and check:

```text id="q3q34n"
Branches
Tags
Commit History
```

Everything should be identical to the old repository.

### Example

```bash id="bgj04f"
git clone --mirror https://github.com/company-a/project.git
cd project.git

git remote set-url origin https://github.com/company-b/project.git

git push --mirror
```

This is the safest and most complete way to migrate a repository with **100% history and all branches preserved**.
