---
title: "Obsolete Members for KIO::SimpleJob"
description: "Deprecated members of KIO::SimpleJob."
parent: "kiocore/kio-simplejob"
---

# Obsolete Members for KIO::SimpleJob

**The following members of class [SimpleJob](kio-simplejob.md) are deprecated.** We strongly advise against using them in new code.

## Obsolete Related Non-Members {#obsolete-related-non-members}

### \[deprecated in 6.9\] KIO::SimpleJob \*http\_update\_cache(const QUrl &*url*, bool *no\_cache*, const QDateTime &*expireDate*) {#http_update_cache}

This function is deprecated since 6.9. We strongly advise against using it in new code.

HTTP cache update

Not implemented.

`url` Url to update, protocol must be "http".

`no_cache` If true, cache entry for `url` is deleted.

`expireDate` Local machine time indicating when the entry is supposed to expire.

Returns the job handling the operation.
