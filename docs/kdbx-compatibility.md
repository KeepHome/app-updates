# KDBX Compatibility

Real KDBX read/write is not implemented in Phase 1.

## Acceptance criteria for the spike

A candidate KDBX implementation is acceptable only when it can:

1. Open a test `.kdbx` database.
2. Read groups, entries, username, password, URL, notes, custom fields, and TOTP fields.
3. Preserve unsupported fields where possible.
4. Write a modified copy.
5. Open the modified copy in Strongbox/KeePassXC.
6. Support the KDBX version/KDF/cipher used by Tomasz's real database, tested only on a copy.

## Safety

- Never test on the real production database directly.
- Use a disposable copy.
- Before write support ships, implement backup-before-write and atomic save.
