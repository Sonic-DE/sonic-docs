---
title: "Obsolete Members for KFileWidget"
description: "Deprecated members of KFileWidget."
parent: "kiofilewidgets/kfilewidget"
---

# Obsolete Members for KFileWidget

**The following members of class [KFileWidget](kfilewidget.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void readConfig(KConfigGroup &group)](#readConfig) (deprecated in 6.3)
- [void setPreviewWidget(KPreviewWidgetBase \*w)](#setPreviewWidget) (deprecated in 6.19)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.3\] void KFileWidget::readConfig(KConfigGroup &*group*) {#readConfig}

This function is deprecated since 6.3. We strongly advise against using it in new code.

reads the configuration for this widget from the given config group `group` the [KConfigGroup](../kconfigcore/kconfiggroup.md) to read from

Deprecated: No known use case

### \[deprecated in 6.19\] void KFileWidget::setPreviewWidget(KPreviewWidgetBase \**w*) {#setPreviewWidget}

This function is deprecated since 6.19. We strongly advise against using it in new code.

Adds a preview widget and enters the preview mode.

In this mode the dialog is split and the right part contains your preview widget.

Ownership is transferred to [KFileWidget](kfilewidget.md). You need to create the preview-widget with "new", i.e. on the heap.

`w` The widget to be used for the preview.

Unused.
