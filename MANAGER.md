# MANAGER.md

This repository is the control plane for `only-AI-project`.

## Responsibilities

- watch the target repository
- keep key workflows enabled
- close stale broken autonomous PRs
- trigger keepalive or forced proposal workflows when the target goes quiet

## Non-Responsibilities

- it does not generate product code for the target repository
- it does not rewrite its own control-plane logic automatically
- it should avoid direct pushes to the target repository

## Principle

The creator repository evolves.
The manager repository stabilizes.
