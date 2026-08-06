# KDBX crate research — Phase 2

Date: 2026-08-03

## Candidate crates checked

Commands used:

```bash
cargo search keepass --limit 10
cargo search kdbx --limit 10
cargo info keepass
cargo info kdbx-rs
cargo info rust-kpdb
cargo info trove-core
```

## Findings

### `keepass = 0.13.20`

- License: MIT.
- Repository: `https://github.com/sseemayer/keepass-rs`.
- Description: KeePass `.kdbx` database file parser.
- Important features: `save_kdbx4`, `totp`, `challenge_response`, `serialization`, `utilities`.
- Looks like the best first candidate because it is active enough, MIT licensed, and explicitly exposes a KDBX4 save feature.

### `kdbx-rs = 0.5.2`

- License: GPL-3.0+.
- Description: KDBX parsing and creation.
- Rejected for now for app-core use because GPL is not a good default for this private/native app core unless we deliberately accept that license later.

### `rust-kpdb = 0.6.0`

- License: MIT/Apache-2.0.
- Description says read/write KeePass 2 and KeePassX databases.
- Older/less obvious maintenance status. Keep as fallback candidate.

### `trove-core = 0.7.1`

- License: MIT OR Apache-2.0.
- KDBX-compatible vault library using `keepass` under the hood for some features.
- Interesting fallback/reference, but likely too much product-level abstraction for our lean desktop app core.

## Decision

Start Phase 2 spike with `keepass` crate using minimal feature flags:

```toml
keepass = { version = "0.13.20", features = ["save_kdbx4", "totp"] }
```

Acceptance criteria remain unchanged: fake DB read, list entries, read TOTP/custom fields, write modified copy, verify in Strongbox/KeePassXC.

## Desktop-first implication

The core must expose a lightweight API suitable for the macOS quick-search panel: open/unlock once, build safe metadata index, then serve search without background polling.
