A **merge conflict** happens when Git cannot automatically decide which changes to keep while merging branches.

Usually occurs when:

* Two people edit the same line
* One deletes a file while another modifies it
* Same code block changed differently in two branches

---

# Example Scenario

## main branch

```bash id="r1kq7"
print("Hello")
```

## feature branch

```bash id="jw5l8"
print("Hello Ahmed")
```

When merging:

```bash id="2xg9p"
git merge feature
```

Git gets confused because both branches changed the same line.

---

# Conflict Output

Git shows:

```bash id="5mcn2"
CONFLICT (content): Merge conflict in app.py
Automatic merge failed
```

---

# How Conflict Looks in File

```bash id="b7qf1"
<<<<<<< HEAD
print("Hello")
=======
print("Hello Ahmed")
>>>>>>> feature
```

Meaning:

* `<<<<<<< HEAD` → current branch code
* `=======` → separator
* `>>>>>>> feature` → incoming branch code

---

# How to Resolve

## Step 1: Open file

Edit manually:

```bash id="z2nka"
print("Hello Ahmed")
```

Remove conflict markers.

---

## Step 2: Add resolved file

```bash id="v6dwp"
git add app.py
```

---

## Step 3: Commit merge

```bash id="0o4ev"
git commit -m "Resolved merge conflict"
```

---

# Commands Used During Conflicts

| Command             | Purpose                    |
| ------------------- | -------------------------- |
| `git status`        | Shows conflicted files     |
| `git diff`          | Shows conflict differences |
| `git merge --abort` | Cancel merge               |
| `git add <file>`    | Mark resolved              |
| `git commit`        | Complete merge             |
| `git log --merge`   | Show conflicting commits   |

---

# Merge Conflict Interview Answer

“A merge conflict occurs when Git cannot automatically merge changes because multiple branches modified the same part of a file differently. We resolve it manually by editing the conflicted file, staging it, and committing the merge.”

---

# Types of Merge Conflicts

| Type                   | Example                       |
| ---------------------- | ----------------------------- |
| Content conflict       | Same line edited differently  |
| Delete/modify conflict | One branch deletes file       |
| Rename conflict        | Same file renamed differently |
| Binary conflict        | Image/zip files changed       |

---

# How Companies Reduce Merge Conflicts

* Small frequent commits
* Pull latest code regularly
* Short-lived branches
* Proper branching strategy
* Code reviews
* Feature flags

---

# Merge vs Rebase Conflict

| Merge Conflict       | Rebase Conflict       |
| -------------------- | --------------------- |
| Happens during merge | Happens during rebase |
| Creates merge commit | Rewrites history      |
| Easier for teams     | Cleaner history       |

---

# Important Interview Point

After fixing conflicts during rebase:

```bash id="k3u8y"
git rebase --continue
```

During merge:

```bash id="8y1tm"
git commit
```

---

# Real-Time DevOps Example

Two engineers modify:

* `terraform.tf`
* Kubernetes YAML
* GitHub Actions workflow

When PR merges into `main`, conflict occurs because both changed same configuration block.

This is a very common real-world scenario in DevOps teams.
