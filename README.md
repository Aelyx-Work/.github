# Aelyx-Work GitHub standards

This repository keeps organization-wide contribution guidance and GitHub Actions workflow templates in one place. It is designed to make project setup repeatable while allowing each repository to add the checks its stack actually needs.

## Start a new repository

1. Create it under the Aelyx-Work organization with private visibility and initialize it with a README. This creates the default main branch immediately.
2. Add the CI workflow that matches the project from the repository's Actions tab: Aelyx Node.js CI (npm), Aelyx Python CI, or Aelyx C++ CI (CMake).
3. Commit the correct dependency manifest and lockfile. Add real tests as the project grows; CI runs configured checks but cannot invent meaningful tests for an empty app.
4. Adjust the workflow's install, lint, test, and build commands for the repository. Keep workflow permissions read-only unless a job has a documented need for more access.

## Included checks

- Node.js / npm: installs from package-lock.json with npm ci when available, then runs configured lint, test, and build scripts.
- Python: installs requirements.txt or the project in pyproject.toml, checks Python syntax, and runs pytest when the project includes tests.
- C++ / CMake: configures and builds the CMake project, then runs CTest.

Workflow templates are copied into a repository when selected. To improve a workflow later, update its template here and make the corresponding change in repositories that use it.

## Security

Keep credentials in GitHub Actions secrets or environments, never in source code. Review workflow changes like application code, use read-only GITHUB_TOKEN permissions by default, and do not automatically merge dependency updates without reviewing the CI result.
