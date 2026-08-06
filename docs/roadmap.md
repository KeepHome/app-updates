# Roadmap

## Phase 1 — Foundation

- Repo skeleton.
- Rust safe metadata/search/TOTP foundation.
- Swift package placeholder.
- Docs and test script.

## Phase 2 — KDBX compatibility spike

- Pick/evaluate Rust KDBX crate(s).
- Open fake KDBX fixture.
- List/search entries.
- Modify a field and write a copy.
- Verify modified copy opens in Strongbox/KeePassXC.

## Phase 3 — macOS desktop tray MVP

- Native menu-bar app.
- Select/unlock `.kdbx`.
- Read-only tray search/list/detail/copy.
- Copy password/login/OTP/open URL.
- Open full editor in local Safari web UI.
- Auto-lock and clipboard auto-clear.

## Phase 4 — Local Safari editor

- Localhost-only web server, e.g. `127.0.0.1:19731`.
- Full entry editor: title, username, password, URL, notes, group, custom fields, TOTP.
- Ephemeral token/auth before real secrets are exposed.
- Safe KDBX writes: backup, atomic save, conflict detection.

## Phase 5 — Menu bar quick search polish

- `NSStatusItem`.
- Global hotkey.
- Spotlight/Raycast-style panel.
- Keyboard shortcuts for login/password/OTP/URL.

## Phase 5 — Editing/safe writes

- Basic fields editor.
- Backups, atomic save, conflict detection.

## Phase 6 — macOS AutoFill

- Credential Provider Extension.

## Phase 7 — Encrypted external file folder

- Local-folder encrypted file vault.

## Phase 8 — iOS read-only

- Read-only SwiftUI app on same core.
