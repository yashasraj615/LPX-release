# LPX 1.2.0

- Fixed Open in browser rejecting valid HTTP/HTTPS URLs, including localhost:4329, on Windows
  and macOS. Open uses the same URL as Copy URL and the system's default browser.
- Improved Scan Folder detection for npm/pnpm/Yarn/Bun scripts, custom server script names,
  workspace package-manager declarations, scriptless Node servers and Vite preview ports.
- Frontend, backend and worker scripts sharing a package become separate components. Database
  client libraries are not mistaken for database servers; Compose infrastructure stays identified.
- Added Create and start, with preflight checks and the existing dependency-aware launch flow.
- Improved Windows package-manager launching through Node, preserving literal arguments and
  working folders containing spaces. Rescan keeps same-folder services separate and preserves
  custom commands.

Scanning does not install dependencies or execute project code. Starting a reviewed project runs
its own scripts with the user's normal permissions. No cloud account, telemetry, elevated app or
privileged helper was added.

Windows installers remain unsigned. macOS builds use an ad-hoc signature without Developer ID
trust or Apple notarization. Installation verification and remaining runtime limits are recorded
in the release metadata. Intel compilation does not establish Intel runtime verification.

## Verification and installation

Both installers are newly built for 1.2.0. Previous 1.1.0 assets remain unchanged. Checksums are
in release.json and SHA256SUMS.txt. MSI is retained locally as a build-only artifact.

Windows: run LPX-Setup.exe, per-user without administrator rights. Silent install, version,
15-second startup with a verified standard-user token and silent uninstall passed on a hosted
Windows runner. 75 Rust tests, 11 frontend tests, the live discovery lab and real npm frontend/
backend HTTP launch integration passed. Interactive browser/wizard UI, upgrade/shortcuts,
Windows 10, clean-PC WebView2 bootstrap, MSI installation and UAC consent remain unverified.

macOS: open LPX.dmg, drag LPX to Applications and eject. Universal DMG metadata, both architectures,
icon, Applications shortcut and ad-hoc code integrity passed. The exact packaged app ran on
Apple Silicon macOS 26.5.1: localhost:4329 opened in default Chrome; folder scan inferred frontend/
backend scripts and dependency; Create and start reached Healthy 2/2; rescan and stop passed.
72 Rust tests, 11 frontend tests and the live discovery lab passed. Intel/macOS 11 runtime and
internet-downloaded Gatekeeper flow remain unverified. No Developer ID signature or notarization;
Gatekeeper may block the download. For a verified official download, use Privacy & Security →
Open Anyway if offered; do not disable Gatekeeper. Windows SmartScreen may warn.

Docker with a running daemon, notification delivery and login startup remain unverified.
Scanning does not install dependencies: starting requires project dependencies and local runtimes.
