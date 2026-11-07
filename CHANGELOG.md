# LPX 1.1.0

Published distribution preparation: 7 November 2026.

LPX discovers local TCP/UDP listeners, identifies applications and owning processes, detects
HTTP/HTTPS services, monitors health, keeps activity history, and groups development services
into projects with folder scanning, launch profiles and dependency-aware start configurations.
Everything stays local; no account, cloud or telemetry.

- Reliable Open Link states, retry/backoff, and health-aware service links.
- Add running services to projects with relaunch analysis and launch preflight.
- Dependency-wave, sequential and parallel stack start modes.
- Platform permission explanations; Windows supports a one-shot UAC helper for selected stops.
- First macOS universal DMG, sharing the same Tauri/Rust/React app as Windows, with native menus,
  menu-bar extra, Dock/reopen support and macOS process control.

## Downloads

| Platform | Version | File | Bytes | Architectures |
|---|---|---|---|---|
| Windows 10/11 | 1.1.0 | LPX-Setup.exe | 5,944,690 | x64 |
| macOS 11+ | 1.1.0 | LPX.dmg | 11,323,521 | arm64 + x86_64 (universal) |

The existing Windows installer was reused. Its SHA-256 matches the previously tested build; no
Windows rebuild was performed. The MSI is retained locally as a build-only artifact and is not
the primary public download. Checksums are retained in release.json and SHA256SUMS.txt.

## Installation and trust

Windows: run LPX-Setup.exe; it installs for your user without administrator rights. The installer
is unsigned, so SmartScreen may warn.

macOS: open LPX.dmg and drag LPX to Applications, then eject the image. The app has an ad-hoc
signature and hardened runtime, with code integrity verified. It has no Developer ID signature
and is not notarized. Gatekeeper may block an internet download; only for a verified official
download, use System Settings → Privacy & Security → Open Anyway if offered. Do not disable
Gatekeeper. Unattended DMG packaging includes the app and Applications shortcut; Finder cosmetic
icon positioning was skipped.

## Verification and limits

Mac: both architectures compiled; DMG checksum/mount, bundle version/identifier/minimum OS, icon,
Applications shortcut and code integrity passed. A copy extracted from the image ran on Apple
Silicon macOS 26.5.1. Verified 66 Rust unit tests, 10 UI tests, the real HTTP/TCP/UDP/IPv4/IPv6
discovery lab and conflict detection, native keyboard navigation, About/version, permission
text, and window hide/reopen.

Windows: original release evidence records per-user install, upgrade, relaunch, shortcuts and
uninstall on Windows 11. This session verified installer bytes/checksum on a Mac; it did not
repeat Windows runtime tests.

Unverified: Intel runtime, macOS 11 runtime, internet-downloaded Gatekeeper flow, macOS
notification delivery and start-at-login, Docker with a running daemon, Windows 10, a second
Windows PC, WebView2 bootstrap on a clean PC, MSI installation and the UAC consent prompt.
