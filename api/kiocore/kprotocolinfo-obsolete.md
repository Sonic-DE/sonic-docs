---
title: "Obsolete Members for KProtocolInfo"
description: "Deprecated members of KProtocolInfo."
parent: "kiocore/kprotocolinfo"
---

# Obsolete Members for KProtocolInfo

**The following members of class [KProtocolInfo](kprotocolinfo.md) are deprecated.** We strongly advise against using them in new code.

## Static Public Members

- [QString proxiedBy(const QString &protocol)](#proxiedBy) (deprecated in 6.4)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[static, deprecated in 6.4\] QString KProtocolInfo::proxiedBy(const QString &*protocol*) {#proxiedBy}

This function is deprecated since 6.4. We strongly advise against using it in new code.

Returns the name of the protocol through which the request will be routed if proxy support is enabled.

A good example of this is the ftp protocol for which proxy support is commonly handled by the http protocol.

This corresponds to the "ProxiedBy=" in the protocol description file.

Not used.
