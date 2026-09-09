<div align="center">

# WingletReader — Releases

**Download the latest build of WingletReader.**
A local-first desktop speed-reading application for Windows.

**Early alpha — v0.2.1-alpha.1**

### ➜ [**Download the latest release**](https://github.com/winglet-stack/WingletReader-Releases/releases)

</div>

---

> **This repository hosts the packaged installers only.** It is where the app's
> download links point and where the built-in updater checks for new builds.
> The source code, architecture, design work, and feedback venues live in the
> main repository: **[winglet-stack/WingletReader](https://github.com/winglet-stack/WingletReader)**.

---

## Contents

- [What WingletReader is](#what-wingletreader-is)
- [Requirements](#requirements)
- [Install](#install)
- [First run](#first-run)
- [Auto-updates](#auto-updates)
- [Verifying your download](#verifying-your-download-optional)
- [Uninstall](#uninstall)
- [Latest release](#latest-release)
- [Feedback & links](#feedback--links)

---

## What WingletReader is

WingletReader turns any text into a rhythmic, adjustable word-stream, so you
read along at a pace you set instead of scanning a static page. You control the
speed, how many words appear at a time, how many lines, and the colours.
Everything stays on your machine — no account, no cloud sync, no telemetry.

For the full feature tour, screenshots, architecture, and source, see the
**[main repository](https://github.com/winglet-stack/WingletReader)**.

---

## Requirements

| | |
|---|---|
| **Operating system** | Windows 10 or Windows 11 |
| **Architecture** | 64-bit (x64) |
| **Admin rights** | **Not needed** — installs for your user account only |
| **Disk space** | ~250 MB |

> There is currently **no macOS, Linux, or ARM64 build**. Windows x64 is the only
> published target during alpha.

---

## Install

### 1. Download the installer

Go to the **[latest release](https://github.com/winglet-stack/WingletReader-Releases/releases)**
and download the file named:

```
WingletReader-<version>-Setup.exe
```

For example: `WingletReader-0.2.1-alpha.1-Setup.exe`. The other files on the
release page (`latest.yml`, `.blockmap`) are used by the built-in updater — you
do not need to download them.

### 2. Expect a SmartScreen warning — this is normal

Alpha builds are **not yet code-signed**, so Windows will likely show a blue
*"Windows protected your PC"* screen when you run the installer. To continue:

1. Click **More info**.
2. Click **Run anyway**.

The warning appears because the installer is unsigned — not because anything is
wrong with the file. Windows shows this for any new, unsigned application until
it builds reputation. **Code signing is planned for beta.** If you would rather
not run an unsigned installer, you can
[build from source](https://github.com/winglet-stack/WingletReader#build--run)
instead.

### 3. Run the installer

The installer runs **for your user account only** and does not ask for admin
rights or a UAC prompt. It installs to a fixed per-user location and creates:

- a **Desktop** shortcut named *WingletReader*
- a **Start menu** entry named *WingletReader*

There is nothing to configure — click through and it is done.

---

## First run

Launch WingletReader from the Desktop or Start menu shortcut. There is no
account to create and no sign-in.

**Where your data lives.** All of your texts, settings, bookmarks, and reading
progress are stored in a single JSON file on your machine:

```
%APPDATA%\wingletreader\
```

Paste that path into File Explorer's address bar to open it. Nothing is
uploaded anywhere.

> The data file itself is named `fasttrack-data.json` — a legacy internal name
> deliberately kept so existing users' data never orphans. It is the right file.

**Backing up.** In the app, **Settings → Data** exports your whole library to a
portable JSON file you can keep or move to another machine.

---

## Auto-updates

Once installed, WingletReader keeps itself up to date:

- It **checks this repository for a newer build on startup**.
- When one exists, it downloads and installs it for you.
- Because alpha builds are published as **prereleases**, the app is configured
  to accept them — you will receive new alpha builds as they ship.

**Your data is not touched by an update.** Texts, settings, and progress in
`%APPDATA%\wingletreader\` persist across updates.

This startup update check is the **only** network request a packaged build
makes. There is no telemetry, analytics, or crash reporting.

---

## Verifying your download (optional)

Alpha builds are unsigned (see the [SmartScreen note](#2-expect-a-smartscreen-warning--this-is-normal)).
If you would like to confirm your download is intact, each release includes a
`latest.yml` file containing the installer's expected **SHA-512** hash — compare
it against the file you downloaded.

Most people can skip this.

---

## Uninstall

1. Open **Windows Settings → Apps → Installed apps**.
2. Find **WingletReader** and choose **Uninstall**.

**Your data is kept.** Uninstalling removes the application but leaves your
library and settings in `%APPDATA%\wingletreader\`, so reinstalling picks up
where you left off. To remove everything, delete that folder manually after
uninstalling.

---

## Latest release

**v0.2.1-alpha.1** — EPUB and Winglet Book imports, reading stats, goals, and
stricter progress integrity.

See **[CHANGELOG.md](CHANGELOG.md)** for what changed in this and every previous
release, or browse the
**[full release list](https://github.com/winglet-stack/WingletReader-Releases/releases)**.

---

## Feedback & links

WingletReader is built **in public**, and feedback from real use is the most
useful thing you can give during alpha. All of it happens in the main repo:

- **💡 Ideas & recommendations →
  [Discussions](https://github.com/winglet-stack/WingletReader/discussions/categories/ideas)**
- **🐛 Bugs →
  [Issues](https://github.com/winglet-stack/WingletReader/issues/new/choose)** —
  please include your version, OS, and steps to reproduce.
- **🔒 Security →
  [SECURITY.md](https://github.com/winglet-stack/WingletReader/blob/master/SECURITY.md)** —
  report privately, never as a public issue.
- **📖 Source, docs & architecture →
  [winglet-stack/WingletReader](https://github.com/winglet-stack/WingletReader)**

---

## License

WingletReader is **source-available, not open source**. The installers published
here are provided for evaluation and personal use. Redistribution, derivative
works, and commercial or non-commercial reuse require written permission. See the
[LICENSE](https://github.com/winglet-stack/WingletReader/blob/master/LICENSE) in
the main repository.

© 2026 Florian. The WingletReader name, logo, and dove mark are reserved.
