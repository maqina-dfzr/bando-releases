# Bando — releases

This repository holds no code. It carries the **installers** for Bando and the
`latest.json` that an installed copy reads in order to update itself.

The source is private. What is public is the distribution: the files you
download, and the signature that proves they are the ones we published.

## Download

The newest version is under **[Releases](../../releases/latest)**.

| System | File |
| --- | --- |
| macOS (Apple Silicon) | `.dmg` |
| Windows | `-setup.exe` |
| Linux | `.AppImage`, `.deb` or `.rpm` |

**The first installer is not signed by the operating system yet.** macOS will
say the developer could not be verified — right-click › Open, once — and
Windows will show SmartScreen: More info › Run anyway. That is about the
*first* install. The signature the updater checks is a different one, and it
already exists.

## How updating works

Bando asks this repository, once per launch, whether a newer version shipped.
When one has, it says so in a toast with a button and **waits for you to say
yes**. It never replaces the application under somebody who is in the middle of
an open transaction against a production database.

The downloaded package is verified with
[minisign](https://jedisct1.github.io/minisign/) against a public key compiled
into the application. A tampered feed installs nothing: the signature is
checked before the first byte is written.

The automatic check can be turned off in Settings, and the *Check for updates*
button stays either way.

Two exceptions are worth knowing before you pick a file:

- **`.deb` and `.rpm` never update themselves.** The updater will not replace a
  package it did not install, so automatic updates on Linux mean the
  `.AppImage`.
- **Intel Macs have no build yet.** The release carries macOS for Apple
  Silicon.

## Problems

Open an [issue](../../issues). If Bando showed you an error ID — something like
`syntax_error-a1b2c3` — paste it in. It is what locates the problem, and it
carries nothing from your database.
