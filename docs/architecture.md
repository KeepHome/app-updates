# Architecture

## Chosen stack

- **macOS desktop app:** SwiftUI + AppKit for native UI, menu bar, global shortcuts, lightweight panels, Keychain, Touch ID, and later Credential Provider integration.
- **Core:** Rust library for KDBX handling, search, TOTP, encrypted external file vault, backups, atomic save, and conflict detection.
- **Bridge:** Swift Package placeholder now; later UniFFI or C ABI + XCFramework.
- **iOS:** later SwiftUI target using the same Rust core, read-only first.

## Desktop-first performance principles

- No Electron/Tauri/Flutter/web runtime.
- No idle polling loops.
- Keep app asleep when locked/idle.
- Build a small safe metadata index only after unlock.
- Never index passwords, OTP seeds, secret notes, or file contents.
- Measure idle CPU/RAM before shipping.

## Current modules

```text
core/keep-home-core
  models       safe metadata models
  search       deterministic low-cost in-memory search
  totp         OTP helpers
  kdbx         compatibility-spike placeholder
  vault_files  encrypted external-file vault planning structs

packages/KeepHomeCoreSwift
  temporary Swift package placeholder for future FFI bridge
```
