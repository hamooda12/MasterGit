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
