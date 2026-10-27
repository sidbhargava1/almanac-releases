# The Almanac releases

Signed builds of The Almanac, a local-only Mac chat app that answers from an offline reference
library and cites its sources. This repo holds the DMGs and the engine's source (under Releases)
and `appcast.xml`, the feed installed copies check once a day.

## Install (macOS 15 or later, Apple silicon)

1. From Releases, download `Almanac-<version>.dmg`.
2. Open it, drag The Almanac onto Applications, eject.
3. Open it. It is self-signed, not notarized, so macOS blocks the first launch: dismiss the
   warning, then System Settings → Privacy & Security → **Open Anyway**.

## Updates

The Almanac checks `appcast.xml` daily and offers new versions; **Check for Updates…** in the app
menu checks now. Each DMG carries an EdDSA signature that the installed app verifies before
installing. The check is a plain request for `appcast.xml`: no query parameters, no system profile.
Without a network connection the check fails quietly and the app works as before.

`Almanac-Dev.cer` is the public half of the code-signing certificate, for provenance only.

## Licences and source

The app bundle holds two programs. The engine (`almanac-engine`, the helper that reads the library
and runs the model) links libzim and is free software under GPL-2.0-or-later. Each release carries
its complete source, `Almanac-<version>-engine-source.tar.gz` (build instructions in its README),
plus the upstream source of the bundled libzim (`libzim-*.tar.xz`, `xapian-core-*.tar.xz`) and the
kiwix-build recipe that compiled it (`kiwix-build-*.tar.gz`). The app
itself is proprietary and talks to the engine over a local socket. Every licence, and the source
location for that version, is in `The Almanac.app/Contents/Resources/Licenses/`.
