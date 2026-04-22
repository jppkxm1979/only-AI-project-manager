# only-AI-project-manager
"An AI project manager oversees the project to ensure the code is evolving on its own."

## Purpose

This repository is the guardian and manager for `jppkxm1979/only-AI-project`.

- It does not build the target product.
- It monitors and stabilizes the target repository.
- It can re-enable target workflows, close stale blocked autonomous PRs, and trigger recovery workflows.
- It maintains a simple guardian stability report issue in this repository.

## Recommended Auth

Best: GitHub App with narrowly scoped permissions on `only-AI-project`.

Fallback: fine-grained token stored as `TARGET_REPO_TOKEN`.

### Recommended Secrets and Variables

- `GUARDIAN_APP_PRIVATE_KEY`
- `TARGET_REPO_TOKEN` only as fallback
- repository variable `GUARDIAN_APP_CLIENT_ID`

## Configuration

Edit `automation/manager.json` if the target changes:

- `target_owner`
- `target_repo`

The current default target is `jppkxm1979/only-AI-project`.

## Quick Start

Follow [SETUP.md](C:/Users/Administrator/Documents/GitHub/only-AI-project-manager/SETUP.md) to connect this manager repository to the target repository.
