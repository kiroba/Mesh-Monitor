# Mesh-Monitor

Mesh Monitor for The Omniverse. Split out of [kiroba/The-Omniverse](https://github.com/kiroba/The-Omniverse) with its git history (Oct 30 2026).

## Status (Nov 16, 2026)

- **Windows build — merged Nov 14, 2026 (PR #9).** Scaffold + CI workflow only by design: Mesh Monitor keeps no local DB (telemetry is HTTP polling of the daemon's `:9100` surfaces; the only storage is secure storage). The `mesh-monitor-windows-x64` artifact (11.6 MB) runs on Kiro's laptop.
- **BLE tile** is wired to live met counts (PR #7, Nov 13, 2026), and the **NAT tile** reports relay truth (PR #10, Nov 15, 2026).
- By protocol, Mesh Monitor is built with **no logs** (logs can hold PII) — diagnosis goes through the telemetry surfaces, not log files.

## Build
```
flutter pub get
flutter build apk --release --target-platform android-arm64
```
Shared code comes from [Omni-Core-UI](https://github.com/kiroba/Omni-Core-UI), pinned by tag in `pubspec.yaml`. Android package: `com.omniverse.mesh_monitor`.

CI here makes test builds (debug key). Signed releases still come from the monorepo's `release.yml` until release orchestration moves.

`tool/build_multi_app_suite.py` is the old generator, kept for reference.
