# Decisions

## 2026-08-03 — Desktop first

Decision: focus implementation on macOS desktop first. Mobile stays later/read-only.

Why:
- Tomasz's primary pain is Strongbox resource usage on macOS.
- macOS menu bar/global shortcut/search gives the biggest daily-value win.
- AutoFill integration is desktop-critical but should come after stable core/search.

## 2026-08-03 — Native macOS + Rust core

Decision: Build KeepHome as native SwiftUI/AppKit app backed by Rust core.

Rejected now:
- Electron: too heavy for RAM/CPU/battery.
- Tauri/webview: unnecessary UI/runtime layer.
- Flutter: weaker native macOS password-manager integration.

## 2026-08-03 — KDBX only

Decision: support `.kdbx` only. Do not create a custom password DB format.

## 2026-08-03 — Tray is read-only, editing moves to local web UI

Decision: Keep the tray/global-search surface read-only and optimized for lookup/copy. Full editing should open a local web UI in Safari, served from localhost.

Why:
- The tray must stay tiny, fast, and keyboard-first.
- Editing KDBX fields, custom fields, attachments, external encrypted files, and conflict resolution need more space than a tray popup.
- A local browser UI can evolve faster for full forms while the native desktop app remains lightweight.

Implications:
- Tray actions: search, copy password/login/OTP, open URL, open editor.
- Editor action target: local URL such as `http://127.0.0.1:19731/editor?entry=<id>`.
- The local editor must be localhost-only, authenticated/ephemeral-token protected before real secrets are exposed.

## 2026-08-03 — External files via local synced folder

Decision: Start provider-neutral. Google Drive/iCloud/Dropbox expose local folders; KeepHome encrypts files before placing them there. No direct cloud API/OAuth in MVP.
