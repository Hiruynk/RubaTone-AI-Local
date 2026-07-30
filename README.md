# RubaTone AI Local

RubaTone AI Local is the offline Windows edition of RubaTone AI, accompanied by an Android remote-control client. This repository intentionally contains no application source code. Installers, signed manifests, checksums, and runtime volumes are published on the [Releases](https://github.com/Hiruynk/RubaTone-AI-Local/releases) page.

## Windows

- Windows 11 x64
- NVIDIA RTX 40/50 series
- At least 12 GB VRAM
- The Launcher downloads and verifies the selected runtime once. After a complete installation, the main application can run without Internet access.
- RTX 5070 Ti 16 GB with NVIDIA driver 596.36 is the currently verified hardware configuration. Other listed RTX 40/50 models have not yet been verified on physical hardware.

## Android

- Android 10 or later
- arm64
- The APK is a remote client and must be paired with a Windows computer on the same private network. Without a reachable paired computer, only the home page is available.

## Local-data policy

No songs, models, training data, job history, preferences, or account database from the cloud service are included or migrated. The Local edition has no account UI and does not include the Convert MIDI/MuScriptor feature.

## Integrity

Before installation, compare downloaded files with `SHA256SUMS.json`. The Launcher additionally verifies signed release manifests and every downloaded runtime volume before activating a version.

This build is provided for private, non-commercial evaluation among the developer's friends. Third-party notices are included in the installed package.
