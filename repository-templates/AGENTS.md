# AI coding guidelines

These guidelines apply to coding agents working in this repository. Follow the user's task and the repository's more specific instructions together.

## Before changing code

- Read this file, the README, contribution and security guidance, project manifests, and nearby implementation and tests.
- Identify the repository's language, framework, supported runtime, architecture, and existing commands. Do not assume every Aelyx project uses the same stack.
- Make a short plan for changes that cross multiple files or affect data, security, compatibility, or user-visible behavior. Ask for missing product decisions only when a safe implementation cannot be inferred.

## Implementation

- Make the smallest complete change that solves the requested problem. Preserve established patterns unless there is a concrete reason to improve them.
- Add or update meaningful tests for changed behavior. Do not add tests that merely repeat the implementation or claim a test exists when it does not.
- Avoid new dependencies when the existing stack can solve the problem. If a dependency is necessary, explain why and choose a maintained, compatible package.
- Keep secrets, tokens, credentials, and private customer data out of source code, prompts, logs, fixtures, and commits.
- Treat generated content and AI suggestions as untrusted until reviewed. Check edge cases, validation, authorization, and failure handling.
- Do not deploy, release, merge pull requests, change repository or organization security/access settings, or use credentials unless the user explicitly requested that specific action.

## Verification

- Use the repository's documented lint, type-check, test, and build commands when available. Run the relevant checks after changes.
- Review the final diff for unintended files, security issues, broken links, and unnecessary complexity.
- In your final report, state what changed, which checks actually ran and passed or failed, and any assumptions or remaining risks. Never claim a check passed unless it completed successfully.

## Project-specific notes

Repository maintainers should extend this file with the commands, architecture notes, supported runtime versions, and review requirements that are specific to this project.
