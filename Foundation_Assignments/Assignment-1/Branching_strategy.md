# 1. Explain the branching strategy we use to keep our main codebase safe.

We follow the **Trunk-Based Development** branching strategy to keep our main codebase stable and make sure that all code changes are properly reviewed and tested before they are merged.

In this approach, we maintain one central branch called `main` (trunk). Developers integrate their code changes into this main branch frequently.

For every JIRA ticket, a developer creates a short-lived feature branch from the latest `main` branch. They clone that repository to their local machine, work on their changes locally, test them and push the code to the remote feature branch.

Then, they raise a Pull Request (PR) to merge their changes into `main`.

The PR goes through peer code review and, as part of that process, the CI pipeline automatically runs the build, unit tests, code-quality checks using SonarQube and security scans.

We also keep branch protection rules so that developers cannot push directly to the `main` branch.

Once the PR is approved and all required checks pass, the code changes are merged into the `main` branch.

Since developers integrate their changes into the `main` branch frequently and in small increments, this helps us identify integration issues early and avoid large merge conflicts.
