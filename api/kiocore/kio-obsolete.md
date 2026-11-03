---
title: "Obsolete Members for KIO"
description: "Deprecated members of KIO Namespace."
parent: "kiocore/kio"
---

# Obsolete Members for KIO

**The following members of class [KIO](kio.md) are deprecated.** We strongly advise against using them in new code.

## Obsolete Type Documentation {#obsolete-type-documentation}

### \[deprecated in 6.6\] enum KIO::CacheControl {#CacheControl-enum}

This enum is deprecated since 6.6. We strongly advise against using it in new code.

Specifies how to use the cache.

Not used

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::CC_CacheOnly` | `0` | Fail request if not in cache |
| `KIO::CC_Cache` | `1` | Use cached entry if available |
| `KIO::CC_Verify` | `2` | Validate cached entry with remote site if expired |
| `KIO::CC_Refresh` | `3` | Always validate cached entry with remote site |
| `KIO::CC_Reload` | `4` | Always fetch from remote site |

*See also* [parseCacheControl](kio-obsolete.md#parseCacheControl)(), [getCacheControlString](kio-obsolete.md#getCacheControlString)()

### \[deprecated in 6.19\] enum KIO::PrivilegeOperationStatus {#PrivilegeOperationStatus-enum}

This enum is deprecated since 6.19. We strongly advise against using it in new code.

Specifies privilege file operation status.

| Constant |   |
| --- | --- |
| `KIO::OperationAllowed` | `1` |
| `KIO::OperationCanceled` | `2` |
| `KIO::OperationNotAllowed` | `3` |

## Obsolete Function Documentation {#obsolete-function-documentation}

### \[deprecated in 6.6\] QString KIO::getCacheControlString(KIO::CacheControl *cacheControl*) {#getCacheControlString}

This function is deprecated since 6.6. We strongly advise against using it in new code.

Returns a string representation of the given cache control method.

`cacheControl` the cache control method

Returns the string representation

Not used.

*See also* [parseCacheControl](kio-obsolete.md#parseCacheControl)()

### \[deprecated in 6.9\] KIO::SimpleJob \*http\_update\_cache(const QUrl &*url*, bool *no\_cache*, const QDateTime &*expireDate*) {#http_update_cache}

This function is deprecated since 6.9. We strongly advise against using it in new code.

HTTP cache update

Not implemented.

`url` Url to update, protocol must be "http".

`no_cache` If true, cache entry for `url` is deleted.

`expireDate` Local machine time indicating when the entry is supposed to expire.

Returns the job handling the operation.

### \[deprecated in 6.6\] KIO::CacheControl KIO::parseCacheControl(const QString &*cacheControl*) {#parseCacheControl}

This function is deprecated since 6.6. We strongly advise against using it in new code.

Parses the string representation of the cache control option.

`cacheControl` the string representation

Returns the cache control value.

Not used

*See also* [getCacheControlString](kio-obsolete.md#getCacheControlString)()
