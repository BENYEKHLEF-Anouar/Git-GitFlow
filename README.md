# Git Flow Branching Model

This repository uses the Git Flow branching model to manage development workflows. Git Flow is a structured approach to branching and merging that ensures a clean and organized commit history.

## Overview

Git Flow organizes branches into specific roles:

- **main**: Production-ready branch containing stable code.
- **develop**: Integration branch for ongoing development with the latest work.
- **feature/***: Branches for developing new features, branched from develop.
- **release/***: Branches for preparing a release, branched from develop and merged into main and develop.
- **hotfix/***: Branches for urgent fixes, branched from main and merged back into main and develop.
- **support/***: Branches for long-term support of older releases, branched from main.

## Setup

Initialize Git Flow in your repository:

```bash
git flow init
```

Follow prompts to set branch names (e.g., main for production, develop for development). To accept default settings, run:

```bash
git flow init -d
```

## Common Commands

### Feature Branches

- **Start a feature**:

  ```bash
  git flow feature start <feature-name>
  ```

- **Finish a feature**:

  ```bash
  git flow feature finish <feature-name>
  ```

- **Publish feature to remote**:

  ```bash
  git flow feature publish <feature-name>
  ```

- **Pull feature from remote**:

  ```bash
  git flow feature pull <remote> <feature-name>
  ```

### Release Branches

- **Start a release**:

  ```bash
  git flow release start <release-version>
  ```

- **Finish a release**:

  ```bash
  git flow release finish <release-version>
  ```

### Hotfix Branches

- **Start a hotfix**:

  ```bash
  git flow hotfix start <hotfix-version>
  ```

- **Finish a hotfix**:

  ```bash
  git flow hotfix finish <hotfix-version>
  ```

### Support Branches

- **Start a support branch**:

  ```bash
  git flow support start <release-version> <base-commit>
  ```

## Installation

To install Git Flow:

- **Windows**:

  Use a package manager like Chocolatey or download from the Git Flow repository.

For detailed installation instructions, see the Git Flow Wiki.

## Best Practices

- Always branch features from **develop**, not **main**.
- Keep feature branches focused on a single change.
- Regularly merge **develop** into feature branches to stay updated.
- Use descriptive branch names (e.g., `feature/add-user-auth`).
- Tag releases and hotfixes for traceability.

## Resources

- Original blog post: *A Successful Git Branching Model*
- Git Flow repository: github.com/nvie/gitflow
- Community discussion: Google Group

## License

Git Flow is licensed under the BSD License. See the LICENSE file for details.

***
