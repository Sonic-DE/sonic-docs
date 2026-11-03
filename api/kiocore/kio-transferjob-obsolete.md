---
title: "Obsolete Members for KIO::TransferJob"
description: "Deprecated members of KIO::TransferJob."
parent: "kiocore/kio-transferjob"
---

# Obsolete Members for KIO::TransferJob

**The following members of class [TransferJob](kio-transferjob.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [bool isErrorPage() const](#isErrorPage) (deprecated in 6.3)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.3\] bool TransferJob::isErrorPage() const {#isErrorPage}

This function is deprecated since 6.3. We strongly advise against using it in new code.

Checks whether we got an error page. This currently only happens with HTTP urls. Call this from your slot connected to [result](../kcoreaddons/kjob.md#result)().

Returns `true` if we got an (HTML) error page from the server instead of what we asked for.

Not implemented.
