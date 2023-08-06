# github-actions-composite-template

[![version](https://badgen.net/github/release/remarkablemark/github-actions-composite-template)](https://github.com/remarkablemark/github-actions-composite-template/releases)
[![build](https://github.com/remarkablemark/github-actions-composite-template/actions/workflows/build.yml/badge.svg)](https://github.com/remarkablemark/github-actions-composite-template/actions/workflows/build.yml)

:gear: GitHub Actions Composite Template. Inspired by [remarkablemark/hello-world-composite-action](https://github.com/remarkablemark/hello-world-composite-action).

## Quick Start

```yaml
- name: GitHub Actions Composite Template
  uses: remarkablemark/github-actions-composite-template@v1
```

## Usage

See [action.yml](action.yml)

**Basic:**

```yaml
steps:
  - uses: remarkablemark/github-actions-composite-template@v1
```

## Inputs

### `version`

**Optional**: The version. Defaults to `1.2.3`:

```yaml
- uses: remarkablemark/github-actions-composite-template@v1
  with:
    version: 1.2.3
```

## Contributions

Contributions are welcome!

## License

[MIT](LICENSE)
