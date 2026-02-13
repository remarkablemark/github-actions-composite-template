# AGENTS.md

Guidelines for agentic coding agents operating in this repository.

## Repository Overview

This is a **GitHub Actions Composite Action** template. The main file is `action.yml`.

## Project Type

- **Language**: YAML (GitHub Actions)
- **Package Manager**: None
- **Testing**: GitHub Actions workflows

## Build / Test Commands

### Running Tests

Tests run via GitHub Actions. The test workflow (`.github/workflows/test.yml`) runs on:

- `push` events
- `pull_request` events

Tests on multiple OSes: `ubuntu-latest`, `macos-latest`, `windows-latest`.

### Local Testing with act

```bash
act -W .github/workflows/test.yml
```

### Release Process

Automated via `.github/workflows/release-please.yml`:

- Triggered on push to `master` branch
- Uses "simple" release type
- Creates semantic version tags

## Code Style Guidelines

### General Principles

1. **Keep it simple**: Minimal composite action template
2. **YAML format**: 2-space indentation
3. **Descriptive names**: Clear names for inputs, steps, and jobs

### Git Commit Messages

**Required**: Use [Conventional Commits](https://www.conventionalcommits.org/) format:

```
<type>(<scope>): <description>
```

Types: `fix`, `feat`, `docs`, `chore`, `refactor`, `test`

Examples:
```
feat: add new input parameter
fix: resolve issue with default value
docs: update README
```

### YAML Conventions

- 2-space indentation
- Hyphen `-` for list items
- Quote strings with special characters
- Use anchor aliases (`&anchor`, `*alias`) for reusable fragments

### action.yml Structure

```yaml
name: <action-name>
description: <description>
author: <username>

inputs:
  <input-name>:
    description: <description>
    required: false
    default: <value>

runs:
  using: composite
  steps:
    - name: <step-name>
      uses: <action>
      with:
        <key>: <value>
      shell: bash
      run: |
        <commands>
      env:
        <VAR>: ${{ inputs.<input> }}

branding:
  icon: <icon-name>
  color: <color>
```

### Naming Conventions

- **Action name**: kebab-case
- **Input names**: kebab-case
- **Step names**: Title case
- **Job names**: kebab-case
- **Environment variables**: SCREAMING_SNAKE_CASE

### GitHub Actions Best Practices

1. Always specify `permissions` (principle of least privilege)
2. Use pinned action versions (e.g., `actions/checkout@v6`)
3. Use `with:` for inputs instead of environment variables
4. Set `continue-on-error: false` explicitly
5. Use `id:` on steps when referencing outputs

### Error Handling

- Steps fail on errors by default
- Use `if: ${{ always() }}` or `if: ${{ failure() }}` when continuing is needed
- Check for required inputs

## File Structure

```
.
├── action.yml
├── .github/workflows/
│   ├── test.yml
│   ├── commitlint.yml
│   └── release-please.yml
├── README.md
├── LICENSE
└── version.txt
```

## Common Tasks

### Adding a New Input

1. Add to `inputs:` in `action.yml`
2. Add `with:` in steps using it
3. Update `README.md` with documentation

### Adding a Test Case

Add a step in `.github/workflows/test.yml`:

```yaml
- name: Run action with <scenario>
  uses: ./
  with:
    <input>: <value>
```

### Updating Dependencies

Update action versions in `.github/workflows/*.yml` and `.github/dependabot.yml`.
