# Git Recovery Guide

This guide explains how to recover from common Git mistakes using `git restore`, `git reset`, `git revert`, and `git reflog`.

---

# 1. git restore

Use `git restore` to discard changes in your working directory.

## Restore a File

```bash
git restore file.txt
```

This restores `file.txt` to the version in the current commit (`HEAD`).

### Before

```text
Modified file.txt
```

### After

```text
file.txt matches HEAD
```

## Unstage a File

```bash
git restore --staged file.txt
```

This removes the file from the staging area while keeping the changes in your working directory.

---

# 2. git reset

`git reset` moves `HEAD` to a previous commit.

Depending on the mode, it may also modify the staging area and working directory.

---

## Soft Reset

```bash
git reset --soft HEAD~1
```

### What Happens

* Moves `HEAD` back one commit
* Keeps all changes staged
* Does not modify files

### Use Case

When you want to redo the last commit while keeping all changes ready for recommit.

---

## Mixed Reset (Default)

```bash
git reset --mixed HEAD~1
```

or

```bash
git reset HEAD~1
```

### What Happens

* Moves `HEAD` back one commit
* Unstages changes
* Keeps all file modifications

### Use Case

When you want to remove a commit but continue working on the changes.

---

## Hard Reset

```bash
git reset --hard HEAD~1
```

### What Happens

* Moves `HEAD` back one commit
* Clears the staging area
* Discards all local changes

### Warning

This operation can permanently remove uncommitted work.

Only use it when you are certain that the changes are no longer needed.

---

# 3. git revert

`git revert` creates a new commit that reverses the changes introduced by an existing commit.

```bash
git revert <commit-hash>
```

### What Happens

* Keeps commit history intact
* Creates a new commit that undoes the selected commit

### Use Case

Use `git revert` for commits that have already been pushed to a shared repository.

### Example

Before:

```text
A --- B --- C
```

After:

```text
A --- B --- C --- D
```

Where `D` reverses the changes made in `C`.

---

# 4. Recovering Lost Commits with git reflog

`git reflog` records updates to `HEAD` and branch references.

It can help recover commits that are no longer visible in `git log`.

## View Reflog

```bash
git reflog
```

Example:

```text
abc123 HEAD@{0}: reset: moving to HEAD~1
def456 HEAD@{1}: commit: add booking feature
```

## Recover a Lost Commit

```bash
git reset --hard def456
```

or

```bash
git reset --hard HEAD@{1}
```

### Use Case

Recover commits lost after:

* reset
* rebase
* checkout
* branch switching
* accidental history rewrites

---

# Quick Reference

| Command           | Changes History | Keeps Files | Safe for Shared Branches |
| ----------------- | --------------- | ----------- | ------------------------ |
| git restore       | No              | Yes         | Yes                      |
| git reset --soft  | Rewrites        | Yes         | No                       |
| git reset --mixed | Rewrites        | Yes         | No                       |
| git reset --hard  | Rewrites        | No          | No                       |
| git revert        | Preserves       | Yes         | Yes                      |
| git reflog        | Recovery Tool   | N/A         | Local Only               |

---

# Best Practices

* Use `git restore` to discard file changes.
* Use `git reset --soft` to rewrite recent commits.
* Use `git reset --mixed` to undo commits while keeping work.
* Use `git reset --hard` only when you are certain changes can be discarded.
* Use `git revert` for commits already pushed to remote repositories.
* Use `git reflog` to recover lost commits after resets or rebases.
