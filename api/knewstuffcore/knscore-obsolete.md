---
title: "Obsolete Members for KNSCore"
description: "Deprecated members of KNSCore Namespace."
parent: "knewstuffcore/knscore"
---

# Obsolete Members for KNSCore

**The following members of class [KNSCore](knscore.md) are deprecated.** We strongly advise against using them in new code.

## Obsolete Classes {#obsolete-classes}

### \[deprecated in 6.9\] class KNSCore::Provider

**This class is deprecated since 6.9. We strongly advise against using it in new code.**

This class provides accessors for the provider object.

> **Note:** This class should not be used directly by the application. This class is the base class and will be instantiated for static website providers.

Use ProviderBase to implement providers (only in-tree supported). Use ProviderCore to manage instances of base.
