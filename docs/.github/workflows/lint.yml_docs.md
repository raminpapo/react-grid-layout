# Documentation: .github/workflows/lint.yml

## File Metadata

- **Path**: `.github/workflows/lint.yml`
- **Type**: .yml
- **Size**: 618 bytes (0.60 KB)
- **Lines**: 34
- **Last Modified**: 2025-11-15T20:36:35.072367

## Source Code

```yaml
name: Lint

on:
  # Trigger the workflow on push or pull request,
  # but only for the master branch
  push:
    branches:
      - master
  pull_request:
    branches:
      - master

jobs:
  run-linters:
    name: Run linters
    runs-on: ubuntu-latest

    steps:
      - name: Check out Git repository
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: 18

      - name: Install Node.js dependencies
        run: yarn

      - name: Run Prettier
        run: yarn fmt:check

      - name: Run ESLint/Flow
        run: yarn lint

```

## High-Level Overview

This is a YAML configuration file (lint.yml).

## Detailed Analysis

### Structure

Structure analysis not applicable for this file type.

### Components and Functions

Component analysis not applicable for this file type.

### Dependencies

No external dependencies detected.

## Usage Examples

Refer to other files in the repository for usage examples.

## Related Files

Related files can be found by examining:

- Files in the same directory: `.github/workflows/`


## Notes

- **Performance**: No specific performance concerns
- **Security**: Review for potential vulnerabilities if handling user input
- **Maintainability**: Manageable file size

---
*Documentation generated on 2025-11-15T20:39:40.739090Z*
