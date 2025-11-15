# Documentation: .github/workflows/release.yml

## File Metadata

- **Path**: `.github/workflows/release.yml`
- **Type**: .yml
- **Size**: 1597 bytes (1.56 KB)
- **Lines**: 59
- **Last Modified**: 2025-11-15T20:36:35.072367

## Source Code

```yaml
name: release

on:
  workflow_dispatch:
    inputs:
      semver:
        description: "The semver to use"
        required: true
        default: "patch"
        type: choice
        options:
          - auto
          - patch
          - minor
          - major
          - prerelease
          - prepatch
          - preminor
          - premajor
      baseTag:
        description: "base release tag"
      tag:
        description: "The npm tag"
        required: false
        default: "latest"
      commit-message:
        description: "The commit message template"
        required: false
        default: "Release {version}"
  pull_request:
    types: [closed]

jobs:
  release:
    runs-on: ubuntu-latest
    permissions:
      contents: write
      issues: write
      pull-requests: write
      # optional: `id-token: write` permission is required if `provenance: true` is set below
      id-token: write
    steps:
      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: 18

      - uses: nearform-actions/optic-release-automation-action@v4
        with:
          commit-message: ${{ github.event.inputs.commit-message }}
          semver: ${{ github.event.inputs.semver }}
          npm-tag: ${{ github.event.inputs.tag }}
          # optional: set this secret in your repo config for publishing to NPM
          npm-token: ${{ secrets.NPM_TOKEN }}
          # optional: NPM will generate provenance statement, or abort release if it can't
          provenance: true
          build-command: |
            yarn
            yarn build

```

## High-Level Overview

This is a YAML configuration file (release.yml).

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
*Documentation generated on 2025-11-15T20:39:40.740015Z*
