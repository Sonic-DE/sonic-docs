---
title: "Obsolete Members for KUrlRequester"
description: "Deprecated members of KUrlRequester."
parent: "kiowidgets/kurlrequester"
---

# Obsolete Members for KUrlRequester

**The following members of class [KUrlRequester](kurlrequester.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [QFileDialog \*fileDialog() const](#fileDialog)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[virtual, deprecated\] QFileDialog \*KUrlRequester::fileDialog() const {#fileDialog}

This function is deprecated. We strongly advise against using it in new code.

Returns a pointer to the filedialog. You can use this to customize the dialog, e.g. to call setLocationLabel or other things which are not accessible in the [KUrlRequester](kurlrequester.md) API.

Never returns 0. This method creates the file dialog on demand.

Deprecated: The dialog will be created anyway when the user requests it, and will behave according to the properties of [KUrlRequester](kurlrequester.md). 5.0.
