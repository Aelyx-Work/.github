# Aelyx-Work GitHub standards

This repository holds organization-wide contribution defaults, workflow starters, and reusable guidance for human and AI-assisted development. Application repositories should stay private unless their product owner decides otherwise.

## Start a repository

1. Create it under Aelyx-Work with private visibility and initialize it with a README. This creates the default main branch before any automation runs.
2. In the repository's **Actions** tab, select **Aelyx Node.js / React / Next.js CI** for JavaScript or TypeScript apps. Choose the Python or CMake workflow only when that matches the project.
3. Copy [AGENTS.md](repository-templates/AGENTS.md) into the new repository root so compatible coding agents have the same safe working and testing guidance. Add project-specific architecture and commands as they become known.
4. For a Node.js repository, copy [dependabot-node.yml](repository-templates/dependabot-node.yml) to .github/dependabot.yml. This groups routine npm dependency updates into one weekly npm pull request and GitHub Actions updates into one weekly Actions pull request.
5. Commit the application's real manifest and lockfile. The Node workflow skips before package.json exists, then uses the npm, pnpm, or Yarn lockfile and runs configured lint, typecheck, test, and build scripts. A manifest without a lockfile fails so dependencies stay reproducible.
6. Review the first CI result and tailor the scripts to the application. The starter is a baseline, not a substitute for tests that check real product behavior.

## AI coding tools

The organization agent [Aelyx Implementation Partner](agents/implementation-partner.agent.md) is available to compatible GitHub Copilot agent features. The AGENTS.md starter can be copied into a repository for Codex, Copilot, and other tools that read that file. Keep the instructions short and add each project's own commands and architecture.

## Checks in the workflow starters

- Node.js / React / Next.js: Node 24 LTS, lockfile-based npm, pnpm, or Yarn install, then configured lint, type-check, test, and build scripts.
- Python: installs from requirements.txt or pyproject.toml, checks syntax, and runs pytest when tests are present.
- C++ / CMake: configures and builds the CMake project, then runs CTest.

Workflow templates are copied into a repository when selected; updates to a template here do not change workflows already copied into other repositories. The Node template handles an empty scaffold without switching or renaming the default branch.

## Dependency update practice

Grouped Dependabot security updates are enabled in the organization's settings. For routine version updates, each repository needs its own .github/dependabot.yml; the example above groups all updates within each ecosystem and directory. Dependabot opens separate groups per ecosystem, so npm and GitHub Actions each have their own pull request. Review the CI result before merging; the organization does not auto-merge dependency updates.

## Security

Keep credentials in GitHub Actions secrets or environments, never in source code. Workflow templates use read-only GITHUB_TOKEN permissions by default. Review workflow changes like application code and grant a workflow additional permissions only when its job clearly needs them.
