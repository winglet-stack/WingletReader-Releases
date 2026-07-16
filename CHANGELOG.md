# Changelog

All notable changes to **WingletReader** are recorded here, newest first.
This file is the canonical record of what shipped in each build; the notes on
each [GitHub release](https://github.com/winglet-stack/WingletReader-Releases/releases)
mirror it.

Entries are written for people **using** the app — what changed for you, not
what changed in the code. For the engineering detail behind a change, see the
[main repository](https://github.com/winglet-stack/WingletReader) and its
[decision records](https://github.com/winglet-stack/WingletReader/tree/master/docs/adr).

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

> **About version numbers.** WingletReader is in **alpha**. Builds are numbered
> `0.MINOR.0-alpha.N` — during an alpha cycle the `alpha.N` counter increases
> (`0.2.0-alpha.1`, `0.2.0-alpha.2`, …). Alpha builds are published as
> prereleases and the app accepts them automatically.

---

## [Unreleased]

*Changes landed since the last release will appear here.*

---

## [0.2.0-alpha.1] — 2026-07-16

**The first official public alpha.** This is the first build published openly,
alongside the opening of the public source repository. The focus of this release
was making the app safe and honest to hand to strangers: recovering gracefully
when things go wrong, removing anything that could not be shipped publicly, and
putting a real release pipeline behind every download.

### Added

- **Recovery from a damaged library file.** If the file holding your texts and
  settings is corrupted or unreadable, the app now recovers and starts instead
  of failing to open.
- **A recovery screen instead of a blank window.** If part of the interface hits
  an unexpected error, you now get a readable screen you can act on, rather than
  the app going blank.
- **A local crash log.** If the app closes unexpectedly, details are written to a
  log file on your machine — useful when reporting a bug. Nothing is sent
  anywhere; the log stays local.

### Changed

- **The Reader now uses a system font.** The previously bundled serif typeface
  could not be redistributed publicly, so text now renders in a standard system
  font. Reading behaviour is unchanged, but text will look slightly different
  from earlier builds.
- **The logo now follows your theme.** There is a single canonical logo that
  switches automatically between light and dark appearance. The separate logo
  style setting has been removed — there is nothing you need to change.
- **Updated the underlying application platform.** The Electron runtime the app
  is built on was moved from an end-of-life version to a current, supported one,
  bringing security and performance fixes.

### Removed

- **The bundled serif font** (see *Changed*, above).
- **The logo style setting**, now that the logo is theme-driven.

### Notes

- Builds are **not yet code-signed**, so Windows SmartScreen will warn on first
  run. This is expected — see the
  [install guide](README.md#2-expect-a-smartscreen-warning--this-is-normal).
  Code signing is planned for beta.
- Every published build is now produced by an automated pipeline that runs the
  full test suite before releasing.
- Updating from an earlier build keeps your library, settings, and progress
  intact.

---

## Earlier milestones

These were **pre-public test builds**, made before the project was published
openly. They are listed as waypoints in the project's progress rather than
detailed release notes, and are not recommended for fresh installs — start with
the [latest release](https://github.com/winglet-stack/WingletReader-Releases/releases/latest)
instead.

- **v0.1.2-alpha.1** — the last pre-public build; the supported upgrade path to
  the first public alpha.
- **v0.1.1-alpha.1** — pre-public test build.
- **v0.1.0-alpha.1** — the first packaged Windows build, introducing the
  installer and self-updating.

---

[Unreleased]: https://github.com/winglet-stack/WingletReader-Releases/releases
[0.2.0-alpha.1]: https://github.com/winglet-stack/WingletReader-Releases/releases/tag/v0.2.0-alpha.1
