# CI safeguards

Firmware builds run on master pushes and PRs for config, board, Zephyr, device-tree, include, source, snippet, build manifest, CMake/Kconfig, and workflow changes. Markdown-only changes skip branch/PR builds. Feature branches use PR checks instead of duplicate push and PR builds. Manual runs remain available.

Existing tag builds are preserved with an explicit all-tags trigger. GitHub does not apply path filters to tag pushes. Per-ref concurrency cancels superseded branch/PR checks but never cancels tag runs.

The job still calls zmkfirmware/zmk/.github/workflows/build-user-config.yml@main. GitHub does not allow timeout-minutes or steps on a reusable-workflow caller job. Its build and download timeouts must be implemented upstream; this repository cannot impose them without replacing the upstream workflow. No upstream changes were made.

Validation was limited to actionlint and lightweight static trigger and whitespace checks. No firmware build, compilation, hosted run, release, tag, or deployment was performed. The upstream workflow and firmware compatibility remain unverified. No version bump rule exists in this repository.
