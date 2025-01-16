# GitHub workflows

## CI

```yaml
name: CI

on: [push]

jobs:
  blackbox:
    uses: innmind/github-workflows/.github/workflows/black-box-matrix.yml@main
    with:
      scenarii: 20 # optional
  coverage:
    uses: innmind/github-workflows/.github/workflows/coverage-matrix.yml@main
    secrets: inherit
  psalm:
    uses: innmind/github-workflows/.github/workflows/psalm-matrix.yml@main
  cs:
    uses: innmind/github-workflows/.github/workflows/cs.yml@main
    with:
      php-version: '8.2'
```

## Documentation

```yaml
name: Documentation
on:
  push:
    branches: [master, main]
permissions:
  contents: write
jobs:
  deploy:
    uses: innmind/github-workflows/.github/workflows/documentation.yml@main
    secrets: inherit
```

## Release

```yaml
name: Create release

on:
  push:
    tags:
      - '*'

jobs:
  release:
    uses: innmind/github-workflows/.github/workflows/release.yml@main
    secrets: inherit
```
