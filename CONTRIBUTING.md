# Contributing Guide

## Branching Strategy

| Branch     | Role              | Source  | Target         |
|------------|-------------------|---------|----------------|
| **main**   | Stable production  | —       | —              |
| **develop**| Integration       | main    | —              |
| **feature/*** | New feature     | develop | develop        |
| **release/*** | Release preparation | develop | main + develop |
| **hotfix/*** | Production fix   | main    | main + develop |

### Naming

- `feature/<ticket-id>-<slug>` → `feature/123-login-form`  
- `release/<version>` → `release/1.2.0`  
- `hotfix/<slug>` → `hotfix/fix-500-login`  

## Workflow

### 1. Feature Development

```bash
git checkout -b feature/321-search-filter develop
git pull --rebase origin develop
git commit -m "feat(search): add filters"
git push -u origin feature/321-search-filter
```

- Rebase regularly on `develop` to stay updated.  
- Open a PR targeting `develop`.  
- CI must pass (tests + lint).  
- At least one review approval required.  
- Use **squash merge** → one clean commit per feature.  
- Delete the branch after merge.

### 2. Release

```bash
git checkout -b release/1.2.0 develop
# minor fixes, changelog, version bump
git push -u origin release/1.2.0
```

- Open PR `release/1.2.0` → `main`.  
- After merge: create tag `v1.2.0`.  
- Back-merge `main` → `develop`.

### 3. Hotfix

```bash
git checkout -b hotfix/fix-404 main
# fix issue
git push -u origin hotfix/fix-404
```

- Open PR → `main`.  
- Merge + tag (e.g., `v1.2.1`).  
- Back-merge `main` → `develop` to stay aligned.

## Continuous Integration (CI)

Our CI pipeline ensures code quality and stability before merging.

Every Pull Request triggers:

- Automated tests (unit/integration)  
- Lint checks (code style)  
- Build validation (if applicable)  

### A PR can only be merged if:

- All checks pass (green CI)  
- At least one reviewer has approved  
- The branch is up to date with the target (`develop` or `main`)  

### Protected branches (`main`, `develop`):

- No direct pushes allowed.  
- Only PRs with passing CI can be merged.  
- Squash merge only.  

This ensures a consistent, reliable mainline and avoids regressions.

## Versioning & Tags

We use **Semantic Versioning (SemVer)**:

| Type  | Example  | Meaning                          |
|-------|----------|---------------------------------|
| Major | 2.0.0    | Breaking changes                |
| Minor | 1.3.0    | Backward-compatible new features |
| Patch | 1.2.1    | Bug fixes, hotfixes             |

### Tagging Rules

- Tags are only created on `main` after merging a release or hotfix.  
- Tags mark a production-ready version.  
- Always use the format:  
  ```bash
  git tag v1.2.0
  git push origin v1.2.0
  ```
- The changelog (and sometimes deployment) is generated from these tags.

## Definition of Done (DoD)

- All PRs merged via squash.  
- Tests and lint pass in CI.  
- Each release/hotfix has a SemVer tag.  
- `main` and `develop` remain protected.  
- Back-merges ensure all branches stay synchronized.

***
