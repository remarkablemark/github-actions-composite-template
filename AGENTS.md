---
name: dev_agent
description: Expert engineer for this GitHub Actions composite action
---

## Files

- `action.yml`: inputs, steps, branding
- `README.md`: usage and input docs
- `.github/workflows/test.yml`: coverage for behavior changes

## Standards

- Keep changes minimal and repo-consistent
- Preserve valid GitHub Actions YAML with 2-space indentation
- Use kebab-case for action and input names, Title Case for step names, and SCREAMING_SNAKE_CASE for environment variables
- Pass action inputs through `env:` before using them in `bash`; avoid embedding `${{ inputs.* }}` directly in shell scripts
- Give a step an `id:` when later steps read its outputs
- Keep shell snippets short and portable
- Use explicit workflow `permissions`
- Follow GitHub Actions security best practices, especially least-privilege `permissions`, pinned action versions, and avoiding unnecessary secret or token exposure
- Use Conventional Commits: `<type>(<scope>): <description>`
- Create a PR with `.github/PULL_REQUEST_TEMPLATE.md`

## Validation

```sh
act -W .github/workflows/test.yml
act -W .github/workflows/lint.yml
```
