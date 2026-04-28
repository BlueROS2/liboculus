# Changelog — BlueROS2 fork of liboculus

This file tracks changes made in the BlueROS2 fork relative to the upstream
[`apl-ocean-engineering/liboculus`](https://github.com/apl-ocean-engineering/liboculus) repository.

The upstream library is maintained by Aaron Marburg (University of Washington APL Ocean Engineering).
The BlueROS2 fork is maintained by Fredrik Fogh Sørensen for the BlueROS2 ecosystem.

---

## Fork changes — 2026-04-21

### Fixed
- `package.xml` — `<n>` corrected to `<n>` (colcon build would fail on fresh clone)
- `package.xml` — `<maintainer>` updated to BlueROS2 fork maintainer;
  original `<author>` (Aaron Marburg) preserved
- `package.xml` — `<url>` entries added pointing to the BlueROS2 fork repository
- `CMakeLists.txt` — `cmake_minimum_required(VERSION 3.14.4)` lowered to `3.8`
  for ROS 2 Humble compatibility
- `.gitmodules` — removed stale `gpmf-parser` submodule entry (GoPro video metadata
  parser; not used by this library)
- `.github/workflows/ci.yaml` — added `humble` as the primary CI target (the
  BlueROS2 deployment target); removed `kilted` (pre-release); updated
  `actions/checkout` from v5 → v4
- `.github/workflows/ci_cmake.yaml` — `actions/checkout` v5 → v4
- `.github/workflows/format.yaml` — `actions/checkout` v5 → v4,
  `actions/setup-python` v6 → v5

### Added
- BlueROS2 banner, fork notice, and CI badge at top of `README.md`
- All internal `apl-ocean-engineering/liboculus` links in README updated to
  point to `BlueROS2/liboculus`; the upstream reference text retains its
  original upstream URL
- `CHANGELOG.md` (this file)
- `docs/assets/` directory for banner image
