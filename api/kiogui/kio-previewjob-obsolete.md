---
title: "Obsolete Members for KIO::PreviewJob"
description: "Deprecated members of KIO::PreviewJob."
parent: "kiogui/kio-previewjob"
---

# Obsolete Members for KIO::PreviewJob

**The following members of class [PreviewJob](kio-previewjob.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void removeItem(const QUrl &url)](#removeItem) (deprecated in 6.22)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.22\] void PreviewJob::removeItem(const QUrl &*url*) {#removeItem}

This function is deprecated since 6.22. We strongly advise against using it in new code.

Removes an item from preview processing. Use this if you passed an item to [filePreview](kio-previewjob.md#filePreview) and want to delete it now.

`url` the url of the item that should be removed from the preview queue Unused.
