# The release Branch in Git Flow

## Overview

In the Git Flow model, the **release** branch is used to prepare a new production release. It allows developers to finalize, test, and polish the upcoming version without blocking ongoing work in the **develop** branch.

## Key Characteristics

- **Created from:** `develop`  
- **Merged into:** `main` and `develop`  
- **Purpose:** Stabilize the code, perform testing, and fix minor bugs before release  
- **Naming convention:** `release/<version>` (e.g., `release/1.0`, `release/2.1`)  
- **Includes:** Final adjustments like documentation updates, version number changes, and small fixes  
- **Temporary branch:** Deleted after the release is finished  

## Example Workflow

```bash
# Start a new release branch from develop
git flow release start 1.0

# (Optional) Publish the release branch to remote
git flow release publish 1.0

# Make final changes (update version, fix bugs, etc.)
git commit -am "Update version number and finalize release"

# Finish the release
git flow release finish 1.0
```

## Explanation of Commands

- `git flow release start <version>` → Creates a branch `release/<version>` from `develop`.  
- `git flow release publish <version>` → Pushes the release branch to the remote repository for collaboration.  
- `git flow release finish <version>` → Merges the release branch into both `main` and `develop`, tags the commit with the release version (e.g., `v1.0`), and deletes the release branch locally.  

## Summary

| Aspect             | Description                                       |
|--------------------|-------------------------------------------------|
| Branch name        | `release/<version>`                              |
| Source branch      | `develop`                                        |
| Destination branches | `main` and `develop`                            |
| Purpose            | Prepare and stabilize code for production release |
| Contains           | Bug fixes, version updates, documentation improvements |
| Merged when        | The release is fully tested and approved          |
| Deleted after merge | Yes                                              |

## Diagram (Text Representation)

```
main ───────┐
             ├── develop ───┬── feature/add-login
             │               ├── feature/update-ui
             │               └── release/1.0
             │                    │
             │                    ├── merge → main (production)
             │                    └── merge → develop (post-release updates)
             │
             └── hotfix/1.0.1
```

The **release** branch provides a clean environment to finalize and verify a version before deployment, keeping **develop** open for new work while ensuring **main** remains stable and production-ready.

***
