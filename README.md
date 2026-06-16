# nodus-run-action

GitHub Action for running [Nodus](https://github.com/Masterplanner25/Nodus) scripts in CI.
Installs `nodus-lang` from PyPI and exposes three modes: script execution, test suite, and format check.

## Usage

### Run a .nd script

```yaml
- uses: Masterplanner25/nodus-run-action@v1
  with:
    file: scripts/deploy.nd
```

### Run a test suite

```yaml
- uses: Masterplanner25/nodus-run-action@v1
  with:
    test-path: tests/
```

### Enforce formatting

```yaml
- uses: Masterplanner25/nodus-run-action@v1
  with:
    fmt-check: 'true'
```

### Combine modes

All three inputs can be used together in one step:

```yaml
- uses: Masterplanner25/nodus-run-action@v1
  with:
    file: scripts/build.nd
    test-path: tests/
    fmt-check: 'true'
```

### Full workflow example

```yaml
name: CI

on: [push, pull_request]

jobs:
  nodus:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Run Nodus tests
        uses: Masterplanner25/nodus-run-action@v1
        with:
          test-path: tests/
          fmt-check: 'true'
          version: '4.0.5'
```

## Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `file` | No | `''` | Path to a `.nd` file to run with `nodus run` |
| `test-path` | No | `''` | File or directory to run with `nodus test` |
| `fmt-check` | No | `false` | Run `nodus fmt --check` on all `.nd` files in the workspace |
| `version` | No | latest | `nodus-lang` version to install (e.g. `4.0.5`) |
| `args` | No | `''` | Extra arguments appended to `nodus run` (ignored for test/fmt modes) |

At least one of `file`, `test-path`, or `fmt-check: 'true'` must be set.

## Version pinning

Pin to a specific action release for reproducible builds:

```yaml
- uses: Masterplanner25/nodus-run-action@v1.0.0
  with:
    file: main.nd
    version: '4.0.5'   # also pin the nodus-lang version
```

## Pass arguments to nodus run

```yaml
- uses: Masterplanner25/nodus-run-action@v1
  with:
    file: scripts/migrate.nd
    args: '--allow-paths /tmp'
```

## Requirements

- A Python environment with `pip` available (all GitHub-hosted runners qualify).
- `nodus-lang` is installed fresh each run; no pre-installation needed.

## License

MIT
