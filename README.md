# RainyDM releases

Published versions of **RainyDM**, the download manager for Windows, Linux and macOS. RainyDM
updates itself from this repository: you never need to download a new version by hand. The
[Releases](https://github.com/DevAI48/RainyDM-releases/releases) page has every version if you do.

This repository holds only published builds and the update information. The source code is
private.

## Contents

| Path | What it is |
|---|---|
| Releases `v<version>` | One archive per system: `RainyDM-<version>-win-x64.zip`, `-win-arm64.zip`, `-linux-x64.tar.gz`, `-osx-x64.tar.gz`, `-osx-arm64.tar.gz` |
| `update-feed.json` | Every published version, whether it is mandatory, release notes (English and Arabic), and each archive's size and SHA-256 |
| `update-feed.json.sig` | The publisher's signature of `update-feed.json` (ECDSA P-256, SHA-256, base64 DER) |

RainyDM checks the signature before it reads the feed, and checks each archive's SHA-256 before it
installs anything. A feed or archive that does not match is never used.

## Rules

- **Never edit `update-feed.json` or its `.sig` by hand.** They are written and signed only by the
  `release.yml` workflow of the RainyDM repository. A hand edit breaks the signature, and every
  RainyDM would then refuse the feed and report the update service as blocked.
- **Never remove a release from the feed.** Older versions use the full list to find out whether
  they must update.
- **Never commit keys or tokens here.** The signing key lives only in the RainyDM repository's
  Actions secrets.

## Installing by hand

Download the archive for your system from a release, extract it into a folder you can write to
(for example `%LOCALAPPDATA%\Programs\RainyDM` on Windows or `~/Applications/RainyDM` on macOS and
Linux) and run `RainyDM.Desktop`. Updates then happen inside the app.
