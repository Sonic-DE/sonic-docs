---
title: "Obsolete Members for KProtocolManager"
description: "Deprecated members of KProtocolManager."
parent: "kiocore/kprotocolmanager"
---

# Obsolete Members for KProtocolManager

**The following members of class [KProtocolManager](kprotocolmanager.md) are deprecated.** We strongly advise against using them in new code.

## Static Public Members

- [int connectTimeout()](#connectTimeout) (deprecated in 6.11)
- [int minimumKeepSize()](#minimumKeepSize) (deprecated in 6.26)
- [int proxyConnectTimeout()](#proxyConnectTimeout) (deprecated in 6.11)
- [int readTimeout()](#readTimeout) (deprecated in 6.11)
- [int responseTimeout()](#responseTimeout) (deprecated in 6.11)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[static, deprecated in 6.11\] int KProtocolManager::connectTimeout() {#connectTimeout}

This function is deprecated since 6.11. We strongly advise against using it in new code.

Returns the preferred timeout value for remote connections in seconds.

Returns the timeout value for remote connection in secs.

This is not used.

### \[static, deprecated in 6.26\] int KProtocolManager::minimumKeepSize() {#minimumKeepSize}

This function is deprecated since 6.26. We strongly advise against using it in new code.

Returns the minimum file size for keeping aborted downloads.

Any data downloaded that does not meet this minimum requirement will simply be discarded. The default size is 5 KB.

Use DEFAULT\_MINIMUM\_KEEP\_SIZE

### \[static, deprecated in 6.11\] int KProtocolManager::proxyConnectTimeout() {#proxyConnectTimeout}

This function is deprecated since 6.11. We strongly advise against using it in new code.

Returns the preferred timeout value for proxy connections in seconds.

Returns the timeout value for proxy connection in secs.

This is not used.

### \[static, deprecated in 6.11\] int KProtocolManager::readTimeout() {#readTimeout}

This function is deprecated since 6.11. We strongly advise against using it in new code.

Returns the preferred timeout value for reading from remote connections in seconds.

Returns the timeout value for remote connection in secs.

This is not used.

### \[static, deprecated in 6.11\] int KProtocolManager::responseTimeout() {#responseTimeout}

This function is deprecated since 6.11. We strongly advise against using it in new code.

Returns the preferred response timeout value for remote connecting in seconds.

Returns the timeout value for remote connection in seconds.

This is not used.
