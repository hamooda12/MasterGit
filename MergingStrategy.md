# GitHub Pull Request Merge Strategies

## Overview

GitHub provides three main strategies for merging pull requests:

* Merge Commit
* Squash and Merge
* Rebase and Merge

Each strategy affects the Git history in a different way.

## Example Scenario

Assume the `develop` branch has two commits:

```text
A -- B
```

A new branch called `feature` is created from `develop`.

```text
develop: A -- B
feature:       C -- D
```

Now we want to merge `feature` into `develop`.

## 1. Merge Commit

Merge Commit keeps all commits from the feature branch.

It also adds a new merge commit.

```text
develop after merge: A -- B -- C -- D -- M
```

`M` is the merge commit.

### Merge Commit Advantages

* Preserves the full commit history
* Shows exactly when a branch was merged
* Useful for teams that want detailed history

### Merge Commit Disadvantages

* Can make the Git history messy
* Adds extra merge commits
* Harder to read when there are many branches

### Merge Commit Use Case

Use Merge Commit when the team wants to keep the full history.

## 2. Squash and Merge

Squash and Merge combines all feature branch commits into one commit.

```text
develop after merge: A -- B -- S
```

`S` is a single commit that contains all changes from `C` and `D`.

### Squash Advantages

* Keeps the branch history clean
* Removes unnecessary small commits
* Good for small features and fixes

### Squash Disadvantages

* Loses the detailed commit history from the feature branch
* Harder to inspect each small step later

### Squash Use Case

Use Squash and Merge when you want a clean and simple history.

This is a good default choice for feature branches.

## 3. Rebase and Merge

Rebase and Merge moves feature commits on top of the base branch.

```text
develop after merge: A -- B -- C' -- D'
```

`C'` and `D'` are new versions of the original commits.

### Rebase Advantages

* Keeps a clean linear history
* Preserves individual commits
* Avoids extra merge commits

### Rebase Disadvantages

* Commit hashes change
* Can cause confusion if used incorrectly on shared branches
* Requires more Git understanding

### Rebase Use Case

Use Rebase and Merge when you want a linear history.

It keeps each commit separate.

## Recommended Strategy for This Project

For this project, the recommended strategy is:

```text
Squash and Merge
```

This keeps the main branches clean and easy to read.

## Recommended Workflow

```text
feature branch
      ↓
Pull Request
      ↓
develop
      ↓
Pull Request
      ↓
release/version
      ↓
Pull Request
      ↓
main
      ↓
GitHub Release
```

## Versioning Example

If the pull request adds a new feature:

```text
v1.1.0
```

If the pull request fixes a small bug:

```text
v1.1.1
```

If the pull request introduces breaking changes:

```text
v2.0.0
```

## Summary

| Strategy | Style | Best For |
| --- | --- | --- |
| Merge Commit | Full history | Team history |
| Squash and Merge | Single commit | Small features |
| Rebase and Merge | Linear history | Advanced history |

## Final Recommendation

Use **Squash and Merge** for most pull requests in this project.

It keeps the repository history clean and simple.
