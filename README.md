## Git Workflow Diagram

```mermaid
gitGraph
    commit id: "Initial commit"

    branch develop
    checkout develop
    commit id: "Start develop"

    branch feature/authentication
    checkout feature/authentication
    commit id: "Authentication work"
    commit id: "Open PR to develop"

    checkout develop
    merge feature/authentication id: "Merge feature/authentication"

    branch feature/logging
    checkout feature/logging
    commit id: "Logging work"
    commit id: "Open PR to develop"

    checkout develop
    merge feature/logging id: "Merge feature/logging"

    branch release/v1.0.0
    checkout release/v1.0.0
    commit id: "Prepare release v1.0.0"

## Branch Rules

- Every change must be done through a Pull Request.
- `feature/*` branches are created from `develop`.
- `feature/*` branches are merged into `develop`.
- `release/*` branches are created from `develop`.
- `release/*` branches are merged into `main`.
- After release, merge `release/*` back into `develop`.
- `hotfix/*` branches are created from `main`.
- `hotfix/*` branches must be merged into both `main` and `develop`.

## Example Branches

```txt
main
develop
feature/authentication
feature/logging
release/v1.0.0
hotfix/critical-fix
```

