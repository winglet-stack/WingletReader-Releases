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

> **About version numbers.** WingletReader is in **alpha** and uses Semantic
> Versioning. `0.2.1-alpha.1` is the first published prerelease of the `0.2.1`
> target; if another alpha is needed for that target it becomes
> `0.2.1-alpha.2`, then `.3`. Alpha builds are published as prereleases and
> the app accepts them automatically.

---

## [Unreleased]

No entries yet.

---

## [0.2.1-alpha.1] — 2026-09-09

**The second public alpha.** This release brings the completed EPUB and Winglet
Book import paths together with reading stats, goals, streaks, and stricter
progress integrity in one tested snapshot — and it tells you, right where you
meet them, which parts of the app are still rough.

### Added

- **Open Winglet Books.** You can import a curated `.wbook` file as a complete,
  chaptered book. WingletReader validates it before adding anything, shows a
  confirmation card, and refuses duplicate, malformed, or unsupported books
  without changing your library.

- **Reading stats, goals and streaks.** WingletReader now shows you how you read. When a
  session ends, the dialog shows that session's numbers — words read, time, your measured
  reading speed, pauses, rewinds, and a 0–100 Reading Fluency score — compared against
  your own recent sessions. A banner on the home screen tracks today's words, goal
  progress and reading time, and clicking it opens a new Stats screen: a Dashboard of
  today's and lifetime numbers plus personal highscores, and Graphs of each metric across
  today, the week, the month, or all time. Set a daily reading goal (in pages) and a
  weekly target of reading days — in Settings or right on the Dashboard; meeting your goal
  builds a streak, protected by weekly rest days, and earns points. Re-reading after a
  rewind never double-counts, and everything stays on your device — stats are part of your
  data export like everything else.

- **Open EPUB books.** You can now import `.epub` e-books — the format public libraries and
  Project Gutenberg hand out. The book keeps **the publisher's own chapters** instead of
  having chapters guessed from the text, and its words and punctuation are imported exactly
  as written. Before anything is added, a card shows you the title, author, chapter count and
  word count so you can confirm or back out. Pictures aren't part of the reading view, so
  they're left out — the card tells you how many. Copy-protected (DRM) books are declined
  clearly, by name; WingletReader reads DRM-free books.

- **Warnings where the app is still rough.** Three features now say up front
  what to expect, before you commit to anything, in the same style as the
  existing Transmute warning:
  - **Read While Working** — a notice at the top of its settings explains that
    it is in active development: capture and overlay behaviour can change
    between builds, and the overlay may miss or mis-read selections in some
    apps.
  - **EPUB import** — the confirmation card notes that EPUB text is imported as
    published, without the usual cleanup, so spacing and punctuation can look
    unusual; chapter structure comes from the book's own table of contents,
    and some books lack a good one.
  - **Create Portable Drive** — a notice above the button says the portable
    drive path has not been verified end to end on a real machine in this
    alpha, and asks you to keep a backup of your data before relying on it.

### Changed

- **Reading progress counts only words you actually read.** Skipping forward, dragging the
  scrubber, or jumping to a bookmark no longer counts the words you passed over. Rewinding
  and reading the same passage again still does not double-count it.
- **Reading time now means active reading time.** Long waits in tap-to-read, suspended
  playback, and time spent paused no longer inflate time totals or longest-session records;
  the home banner, Dashboard, and Graphs all use active time.
- **Goal changes no longer rewrite today's or this week's results.** Once you have read that
  day, daily-goal edits take effect tomorrow; once the week has begun, weekly-target edits
  take effect next Monday. The goal editor tells you when a change is waiting.

### Notes

- Builds are still **not code-signed**, so Windows SmartScreen will warn on
  first run — click **More info → Run anyway**. This is expected — see the
  [install guide](README.md#2-expect-a-smartscreen-warning--this-is-normal).
  Never turn off SmartScreen or your antivirus to install an alpha build. Code
  signing is planned before WingletReader is distributed publicly.
- The installer's **SHA-256** is published in the release notes so you can
  check that the file you downloaded is the file that was built.
- Updating from `0.2.0-alpha.1` keeps your library, settings, and progress
  intact; reading stats start counting from the first session you read on the
  new build.

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
the [latest release](https://github.com/winglet-stack/WingletReader-Releases/releases)
instead.

- **v0.1.2-alpha.1** — the last pre-public build; the supported upgrade path to
  the first public alpha.
- **v0.1.1-alpha.1** — pre-public test build.
- **v0.1.0-alpha.1** — the first packaged Windows build, introducing the
  installer and self-updating.

---

[Unreleased]: https://github.com/winglet-stack/WingletReader-Releases/releases
[0.2.1-alpha.1]: https://github.com/winglet-stack/WingletReader-Releases/releases/tag/v0.2.1-alpha.1
[0.2.0-alpha.1]: https://github.com/winglet-stack/WingletReader-Releases/releases/tag/v0.2.0-alpha.1
