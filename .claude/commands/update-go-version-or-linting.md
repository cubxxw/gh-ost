---
name: update-go-version-or-linting
description: Workflow command scaffold for update-go-version-or-linting in gh-ost.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /update-go-version-or-linting

Use this workflow when working on **update-go-version-or-linting** in `gh-ost`.

## Goal

Keeps the Go toolchain, dependencies, and linting tools up to date to ensure compatibility and code quality.

## Common Files

- `go.mod`
- `Dockerfile.packaging`
- `Dockerfile.test`
- `.golangci.yml`
- `.github/workflows/golangci-lint.yml`
- `script/ensure-go-installed`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update configuration files (e.g., go.mod, Dockerfile, .golangci.yml, workflow YAMLs)
- Update scripts related to Go setup and testing
- Modify or touch Go source and test files to address compatibility or linting issues
- Update or add test expectations if needed

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.