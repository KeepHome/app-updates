# Security Model

## Current foundation

Phase 1 does not open real databases and does not store secrets. It establishes safe metadata and search boundaries.

## Rules

- Never commit real `.kdbx`, key files, document vaults, Apple signing assets, or credentials.
- Search indexes only safe metadata: title, username, URL/domain, group, tags, UUID.
- Passwords, OTP seeds, secret notes, and file contents must not be indexed.
- Clipboard copy must later auto-clear.
- Unlock secrets should later use Keychain + LocalAuthentication only with explicit user consent.
- Writes to KDBX must be backup-before-write, atomic, and conflict-aware.

## External encrypted files

External files will be encrypted individually before landing in a synced folder. The sync provider sees encrypted blobs and encrypted index data only.
