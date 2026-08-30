# Changelog — nodus-run-action

Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Versioning: [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

---

## [1.0.9] — 2026-08-30

- Pin the README's `version:` examples to nodus-lang **5.8.0**, flagged by
  `nodus_gate --consumers` at the 5.8.0 release. The pin is what new users copy,
  so a stale one hands them an old runtime, and it is invisible to the Stage 6
  content-hash sweep because this is a GitHub Action rather than a PyPI package.

---

## [1.0.8] — 2026-08-29

- Pin the README's `version:` examples to nodus-lang **5.7.1**. They documented
  5.6.0, so they had gone stale across two nodus-lang releases — the 5.7.0 cycle
  stopped before this step because that release was found defective after its
  PyPI upload and was superseded without a GitHub release.

  The pin is what new users copy, so a stale one hands them an old runtime. It is
  invisible to the Stage 6 content-hash sweep, which works by hashing published
  sdists and this is a GitHub Action; `nodus_gate --consumers` is what catches
  it, and did.

  `action.yml`'s `version` default is deliberately empty (meaning latest) and is
  not a pin — only the README examples are.

---

## [1.0.1] — 2026-08-19

### Docs

- Pin the README's `version:` examples to nodus-lang **5.0.4**. They documented
  4.0.5 — five releases back — and that pin is what new users copy, so it was
  handing them an old runtime.

No behaviour change; `action.yml` still defaults to `latest`.

Surfaced by nodus-lang's Gate 3c (`nodus_gate --consumers`). This action is not
packaged, so nodus-lang's Stage 6 sweep — which detects drift by hashing
published sdists and wheels — has nothing to hash and could never have seen it.

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
