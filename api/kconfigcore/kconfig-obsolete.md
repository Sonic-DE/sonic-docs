---
title: "Obsolete Members for KConfig"
description: "Deprecated members of KConfig."
parent: "kconfigcore/kconfig"
---

# Obsolete Members for KConfig

**The following members of class [KConfig](kconfig.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [KConfig(const QString &file, const QString &backend, QStandardPaths::StandardLocation type = QStandardPaths::GenericConfigLocation)](#KConfig-2) (deprecated in 6.3)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.3\] KConfig::KConfig(const QString &*file*, const QString &*backend*, QStandardPaths::StandardLocation *type* = QStandardPaths::GenericConfigLocation) {#KConfig-2}

This function is deprecated since 6.3. We strongly advise against using it in new code.

Creates a [KConfig](kconfig.md) object at the given `file` using the specified `backend`, with an optional `type` of configuration file. If the backend cannot be found or loaded, then the standard configuration parser is used as a fallback. Use other constructor
