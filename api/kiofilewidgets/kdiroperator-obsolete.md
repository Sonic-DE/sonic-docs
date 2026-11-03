---
title: "Obsolete Members for KDirOperator"
description: "Deprecated members of KDirOperator."
parent: "kiofilewidgets/kdiroperator"
---

# Obsolete Members for KDirOperator

**The following members of class [KDirOperator](kdiroperator.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [KIO::DeleteJob \*del(const KFileItemList &items, QWidget \*parent = nullptr, bool ask = true, bool showProgress = true)](#del) (deprecated in 6.15)
- [void setPreviewWidget(KPreviewWidgetBase \*w)](#setPreviewWidget) (deprecated in 6.19)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[virtual, deprecated in 6.15\] KIO::DeleteJob \*KDirOperator::del(const KFileItemList &*items*, QWidget \**parent* = nullptr, bool *ask* = true, bool *showProgress* = true) {#del}

This function is deprecated since 6.15. We strongly advise against using it in new code.

Starts and returns a [KIO::DeleteJob](../kiocore/kio-deletejob.md) to delete the given `items`.

`items` the list of items to be deleted

`parent` the parent widget used for the confirmation dialog

`ask` specifies whether a confirmation dialog should be shown

`showProgress` passed to the DeleteJob to show a progress dialog

### \[virtual, deprecated in 6.19\] void KDirOperator::setPreviewWidget(KPreviewWidgetBase \**w*) {#setPreviewWidget}

This function is deprecated since 6.19. We strongly advise against using it in new code.

Sets a preview-widget to be shown next to the file-view.

The ownership of `w` is transferred to [KDirOperator](kdiroperator.md), so don't delete it yourself!

Unused.
