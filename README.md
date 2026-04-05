# Meshery — Open Source Contributions

A collection of my contributions to [Meshery](https://github.com/meshery/meshery), an open source cloud-native management platform built primarily in Go.

---

## Pull Requests

### 1. [mesheryctl] Replace `cobra.ArbitraryArgs` with Proper Argument Validation in `filter view`
Replaced `cobra.ArbitraryArgs` with `cobra.MaximumNArgs(1)` to reject extra positional arguments. Moved `--all` flag conflict check and missing name/ID check to `PreRunE` for early validation. Removed the now-unused `parseQuotedArg` function and patched an empty-string edge case that silently bypassed required flag checks.

🔗 [View PR](https://github.com/meshery/meshery/pull/18362)

---

### 2. [Server] Fix `DeleteMeshSyncResource` HTTP Response Handling
Updated the handler to return a proper `200 OK` with a JSON body on success and `500 Internal Server Error` on database failure. Added a comprehensive test suite using an in-memory SQLite database covering both scenarios. Improved response type safety by replacing `strings.Contains` checks with proper struct-based JSON unmarshaling.

🔗 [View PR](https://github.com/meshery/meshery/pull/18193)

---

### 3. [Server] Reject Invalid Performance Test Endpoint URLs
Updated `SMPPerformanceTestConfigValidator` to use `url.ParseRequestURI` with explicit scheme and host checks, ensuring only absolute URLs are accepted. Added a table-driven test file covering edge cases including empty endpoint lists.

🔗 [View PR](https://github.com/meshery/meshery/pull/18291)

---

### 4. Fix Token Commands to Use Active Config Path for Consistency
Introduced an `activeConfigPath` helper to ensure all token commands (`create`, `delete`, `set`, `list`, `view`) correctly target the active config file instead of defaulting to the standard path. Added a regression test verifying active config isolation from the default config.

🔗 [View PR](https://github.com/meshery/meshery/pull/18280)

---

### 5. Fix Error Handling in `ProcessConnectionRegistration`
Improved error handling by fixing a typo, adding dynamic connection details to error messages, ensuring early returns with proper HTTP error responses, and adding a nil guard for the event object before persist/publish operations.

🔗 [View PR](https://github.com/meshery/meshery/pull/18219)

---

## Tech Stack
`Go` · `Cobra CLI` · `SQLite` · `HTTP Handlers` · `REST APIs` · `Table-driven Tests`
