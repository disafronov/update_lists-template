# update_lists-template

Automated repository list updater for GitHub repositories.

## Overview

This tool automatically updates `repos.list` files in target repositories based on pattern matching against your GitHub repositories. It runs as a GitHub Action on a schedule and creates pull requests with updated repository lists.

## How it works

1. Reads patterns from `patterns.list` file
2. Fetches all your non-fork, non-archived repositories from GitHub
3. Filters repositories using regex patterns
4. Updates `repos.list` in target repositories via pull requests

## Configuration

### patterns.list

Each line defines a target repository and pattern in format:
```
target-repo:regex-pattern
```

Example:
```
disafronov/ansible_project-template_sync:^disafronov/ansible_project-
disafronov/ansible_role-template_sync:^disafronov/ansible_role-
```

### Required secrets

- `REPO_UPDATE_TOKEN`: GitHub token with repository access permissions

## Usage

The workflow runs automatically:
- **Schedule**: Daily at 14:00 UTC
- **Manual**: Via `workflow_dispatch` trigger

## Files

- `patterns.list` - Configuration file with repository patterns
- `.github/workflows/refresh-repos-list.yaml` - GitHub Action workflow
