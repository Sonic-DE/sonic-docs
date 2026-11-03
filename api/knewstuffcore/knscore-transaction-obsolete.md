---
title: "Obsolete Members for KNSCore::Transaction"
description: "Deprecated members of KNSCore::Transaction."
parent: "knewstuffcore/knscore-transaction"
---

# Obsolete Members for KNSCore::Transaction

**The following members of class [Transaction](knscore-transaction.md) are deprecated.** We strongly advise against using them in new code.

## Static Public Members

- [KNSCore::Transaction \*install(KNSCore::EngineBase \*engine, const KNSCore::Entry &entry, int linkId = 1)](#install) (deprecated in 6.9)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[static, deprecated in 6.9\] KNSCore::Transaction \*Transaction::install(KNSCore::EngineBase \**engine*, const KNSCore::Entry &*entry*, int *linkId* = 1) {#install}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Performs an install on the given `entry` from the `engine`.

`linkId` specifies which of the assets we want to see installed.

Returns a Transaction object that we can use to track the progress to completion Use [installLatest](knscore-transaction.md#installLatest) or [installLinkId](knscore-transaction.md#installLinkId) instead
