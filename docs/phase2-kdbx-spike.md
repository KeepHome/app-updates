# Phase 2 KDBX spike notes

Desktop-first target API:

1. Open/unlock `.kdbx` once from the native macOS app.
2. Build a safe `SearchIndex` from metadata only.
3. Keep secrets out of search and logs.
4. Provide explicit copy actions for username/password/TOTP.
5. Add write support only after a fake DB roundtrip opens in Strongbox/KeePassXC.

CLI skeleton:

```bash
cargo run --manifest-path core/keep-home-core/Cargo.toml --bin keephome-spike -- requirements
cargo run --manifest-path core/keep-home-core/Cargo.toml --bin keephome-spike -- search-demo github
```

The `list/open/write-copy` commands intentionally return an error until real KDBX integration is wired.
