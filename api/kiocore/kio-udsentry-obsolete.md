---
title: "Obsolete Members for KIO::UDSEntry"
description: "Deprecated members of KIO::UDSEntry."
parent: "kiocore/kio-udsentry"
---

# Obsolete Members for KIO::UDSEntry

**The following members of class [UDSEntry](kio-udsentry.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void reserve(int size)](#reserve) (deprecated in 6.29)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.29\] void UDSEntry::reserve(int *size*) {#reserve}

This function is deprecated since 6.29. We strongly advise against using it in new code.

Calling this function before inserting items into an empty [UDSEntry](kio-udsentry.md) may save time and memory.

`size` number of items for which memory will be pre-allocated

Use [reserveStrings](kio-udsentry.md#reserveStrings)() and [reserveNumbers](kio-udsentry.md#reserveNumbers)().
