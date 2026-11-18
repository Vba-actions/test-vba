# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com),
and this project adheres to [Semantic Versioning](https://semver.org).

## [Unreleased]
### Added
- Added Changelog.

## [1.0.1] - 2026-11-18
### Added
- Added `.github/workflows/push-tag.yml` workflow to automatically pin the floating `v1` major tag to the latest `v1.x.x` release tag.

## [1.0.0] - 2026-11-18
### Added
- Initial release of `test-vba` composite GitHub Action.
- Headless VBA unit test execution via `vbaUnit` with `VbaStdLib` and `Vba-Excel-Object-Library` pre-installed.
- Automated line coverage reporting to Coveralls.io.
- Configurable `source_path`, `test_path`, and `github_token` inputs.

[unreleased]: https://github.com/Beakerboy/VBA-Projects/compare/v1.0.1...HEAD
[1.0.1]: https://github.com/Beakerboy/VBA-Projects/compare/v1.0.0...v1.0.1
[1.0.0]: https://github.com/olivierlacan/keep-a-changelog/releases/tag/v1.0.0
