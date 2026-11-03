---
title: "Obsolete Members for KAssistantDialog"
description: "Deprecated members of KAssistantDialog."
parent: "kwidgetsaddons/kassistantdialog"
---

# Obsolete Members for KAssistantDialog

**The following members of class [KAssistantDialog](kassistantdialog.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [QPushButton \*backButton() const](#backButton) (deprecated in 6.29)
- [QPushButton \*finishButton() const](#finishButton) (deprecated in 6.29)
- [QPushButton \*nextButton() const](#nextButton) (deprecated in 6.29)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.29\] QPushButton \*KAssistantDialog::backButton() const {#backButton}

This function is deprecated since 6.29. We strongly advise against using it in new code.

Returns the back button

Override [back](kassistantdialog.md#back)(), instead

### \[deprecated in 6.29\] QPushButton \*KAssistantDialog::finishButton() const {#finishButton}

This function is deprecated since 6.29. We strongly advise against using it in new code.

Returns the finish button

Override [next](kassistantdialog.md#next)(), or use [setValid](kassistantdialog.md#setValid)(), instead, possibly combined with [onLastPage](kassistantdialog.md#onLastPage)()

### \[deprecated in 6.29\] QPushButton \*KAssistantDialog::nextButton() const {#nextButton}

This function is deprecated since 6.29. We strongly advise against using it in new code.

Returns the next button

Override [next](kassistantdialog.md#next)(), or use [setValid](kassistantdialog.md#setValid)(), instead
