# Changelog — nodus-run-action

Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Versioning: [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

---

## [1.0.0] — 2026-06-15

Initial release.

### Added

- **`file` input** — runs a `.nd` script with `nodus run`
- **`test-path` input** — runs a test file or directory with `nodus test`
- **`fmt-check` input** — enforces formatting with `nodus fmt --check` across all `.nd` files in the workspace
- **`version` input** — pins the installed `nodus-lang` version; defaults to latest
- **`args` input** — extra flags forwarded to `nodus run`
- Input validation: error with actionable message if no mode is selected
- Self-test CI workflow covering all modes and a version matrix (4.0.4, 4.0.5)
- Fixture scripts in `tests/`: `hello.nd` (smoke run), `test_basic.nd` (language correctness)

[1.0.0]: https://github.com/Masterplanner25/nodus-run-action/releases/tag/v1.0.0
