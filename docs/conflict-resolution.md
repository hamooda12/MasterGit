# Conflict Resolution

## What Happened?

A merge conflict happened because the same file was edited in two
different branches.

First, I edited the `StudentService` code in the
`feat/student-service` branch and committed the changes.

After that, I moved to another branch and edited the same
student-related code without pulling or merging the latest changes
from the first branch.

Because both branches changed the same part of the code, Git could not
decide which version should be kept automatically.

## Why the Conflict Happened

The conflict happened because the branches were not synchronized before
editing the same file.

Git found different changes in the same area of the `Student` or
`StudentService` class.

So Git stopped the merge and asked me to resolve the conflict manually.

## How I Resolved the Conflict

I opened the conflicted file and compared both versions of the code.

Git showed conflict markers like this:

```text
<<<<<<< HEAD
Current branch code
=======
Incoming branch code
>>>>>>> branch-name
```

I reviewed the old code and the new code, then decided which changes
should be kept.

After comparing both versions, I removed the conflict markers and kept
the correct final version of the code.

Then I saved the file and completed the merge process.

## Commands Used

```bash
git status
```

Used to check which files had conflicts.

```bash
git add .
```

Used after resolving the conflict manually.

```bash
git commit
```

Used to complete the merge conflict resolution.

## Best Practice

Before editing code in another branch, it is better to update the
branch first.

Example:

```bash
git checkout branch-name
git pull origin branch-name
```

Or merge the latest changes from the development branch:

```bash
git merge develop
```

This helps reduce merge conflicts and keeps the branch up to date.

## Conclusion

The conflict happened because the same code was changed in two branches
without syncing first.

I resolved it by comparing the old and new code, keeping the correct
changes, removing the conflict markers, and committing the resolved
file.
