```markdown
# gh-ost Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill provides guidance for contributing to the `gh-ost` codebase, a Go-based project for online schema migrations. It covers the project's coding conventions, update and linting workflows, and testing patterns, helping maintainers and contributors ensure consistency and code quality.

## Coding Conventions

### File Naming
- Use **snake_case** for file names.
  - Example: `table_mapper.go`, `migration_context.go`

### Import Style
- Use **relative imports** within the project.
  - Example:
    ```go
    import (
        "github.com/github/gh-ost/go/sql"
        "github.com/github/gh-ost/go/mysql"
    )
    ```

### Export Style
- Use **named exports** for functions, types, and variables that should be accessible outside their package.
  - Example:
    ```go
    // Exported type
    type MigrationContext struct {
        // ...
    }

    // Exported function
    func NewMigrationContext() *MigrationContext {
        // ...
    }
    ```

## Workflows

### Update Go Version or Linting
**Trigger:** When you need to upgrade the Go version or update linting tools for compatibility or code quality.  
**Command:** `/update-go-or-lint`

1. **Update configuration files**  
   Edit files such as `go.mod`, `Dockerfile.packaging`, `Dockerfile.test`, `.golangci.yml`, and `.github/workflows/golangci-lint.yml` to specify the new Go version or updated linting tool versions.
2. **Update scripts**  
   Modify scripts related to Go setup and testing, such as `script/ensure-go-installed` and `script/test`, to ensure they use the correct Go version and linting tools.
3. **Modify Go source and test files**  
   Update Go code in `go/**/*.go` to address any compatibility or linting issues introduced by the new versions.
4. **Update test expectations**  
   If necessary, update or add files in `localtests/**/expect_failure` to reflect new test outcomes or error messages.
5. **Run tests and linting**  
   Ensure all tests pass and linting checks are clean before submitting your changes.

**Example: Updating Go version in `go.mod`**
```go
module github.com/github/gh-ost

go 1.21 // updated from go 1.20
```

**Example: Updating `.golangci.yml`**
```yaml
linters:
  enable:
    - govet
    - golint
    - staticcheck
run:
  go: "1.21"
```

## Testing Patterns

- **Test files** follow the pattern `*.test.*` (e.g., `table_mapper.test.go`).
- The **testing framework** is not explicitly specified, but standard Go testing practices are likely used.
- Tests are located alongside the code in the `go/` directory structure.
- **Test expectations** may be specified in files under `localtests/**/expect_failure`.

**Example: Basic Go test file**
```go
// table_mapper.test.go
package sql

import "testing"

func TestTableMapping(t *testing.T) {
    // test logic here
}
```

## Commands

| Command              | Purpose                                                      |
|----------------------|--------------------------------------------------------------|
| /update-go-or-lint   | Update Go version, dependencies, or linting tools and configs|
```
