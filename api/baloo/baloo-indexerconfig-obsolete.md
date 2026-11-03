---
title: "Obsolete Members for Baloo::IndexerConfig"
description: "Deprecated members of Baloo::IndexerConfig."
parent: "baloo/baloo-indexerconfig"
---

# Obsolete Members for Baloo::IndexerConfig

**The following members of class [IndexerConfig](baloo-indexerconfig.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void refresh() const](#refresh) (deprecated in 6.22)
- [bool shouldBeIndexed(const QString &path) const](#shouldBeIndexed) (deprecated in 6.22)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.22\] void IndexerConfig::refresh() const {#refresh}

This function is deprecated since 6.22. We strongly advise against using it in new code.

### \[deprecated in 6.22\] bool IndexerConfig::shouldBeIndexed(const QString &*path*) const {#shouldBeIndexed}

This function is deprecated since 6.22. We strongly advise against using it in new code.

Use `Baloo::File` to know if a file has been indexed. Use `Baloo::IndexerConfig::canBeSearched` if a path contains indexed files.

*See also* [Baloo::File](baloo-index.md), [Baloo::IndexerConfig:](baloo-index.md), :
