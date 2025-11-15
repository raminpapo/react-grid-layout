# Documentation: .github/workflows/stale.yml

## File Metadata

- **Path**: `.github/workflows/stale.yml`
- **Type**: .yml
- **Size**: 780 bytes (0.76 KB)
- **Lines**: 21
- **Last Modified**: 2025-11-15T20:36:35.072367

## Source Code

```yaml
name: "Close stale issues and PRs"
on:
  schedule:
    - cron: "0 0,6,12,18 * * *"

jobs:
  stale:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/stale@v1
        permissions:
          issues: write
        with:
          repo-token: ${{ secrets.GITHUB_TOKEN }}
          stale-issue-message: "This issue is stale because it has been open 30 days with no activity. Remove stale label or comment or this issue will be closed in 7 days"
          stale-pr-message: "This PR is stale because it has been open 30 days with no activity. Remove stale label or comment or this PR will be closed in 7 days"
          stale-pr-label: "stale"
          exempt-pr-label: "stale"
          days-before-stale: 90
          days-before-close: 30
          operations-per-run: 30

```

## High-Level Overview

This is a YAML configuration file (stale.yml).

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
*Documentation generated on 2025-11-15T20:39:40.737229Z*
