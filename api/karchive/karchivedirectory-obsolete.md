---
title: "Obsolete Members for KArchiveDirectory"
description: "Deprecated members of KArchiveDirectory."
parent: "karchive/karchivedirectory"
---

# Obsolete Members for KArchiveDirectory

**The following members of class [KArchiveDirectory](karchivedirectory.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void addEntry(KArchiveEntry \*)](#addEntry) (deprecated in 6.13)
- [void removeEntry(KArchiveEntry \*)](#removeEntry) (deprecated in 6.13)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.13\] void KArchiveDirectory::addEntry(*KArchiveEntry \**) {#addEntry}

This function is deprecated since 6.13. We strongly advise against using it in new code.

Adds a new entry to the directory.

Note: this can delete the entry if another one with the same name is already present

Use addEntryV2() instead.

### \[deprecated in 6.13\] void KArchiveDirectory::removeEntry(*KArchiveEntry \**) {#removeEntry}

This function is deprecated since 6.13. We strongly advise against using it in new code.

Removes an entry from the directory.

Use [removeEntryV2](karchivedirectory.md#removeEntryV2)() instead.
