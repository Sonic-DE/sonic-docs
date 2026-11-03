---
title: "Obsolete Members for NETWinInfo"
description: "Deprecated members of NETWinInfo."
parent: "kwindowsystem/netwininfo"
---

# Obsolete Members for NETWinInfo

**The following members of class [NETWinInfo](netwininfo.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void setStrut(NETStrut strut)](#setStrut)
- [NETStrut strut() const](#strut)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated\] void NETWinInfo::setStrut(NETStrut *strut*) {#setStrut}

This function is deprecated. We strongly advise against using it in new code.

use [setExtendedStrut](netwininfo.md#setExtendedStrut)()

Set the strut for the application window.

`strut` the new strut \*

*See also* [strut](netwininfo-obsolete.md#strut)()

### \[deprecated\] NETStrut NETWinInfo::strut() const {#strut}

This function is deprecated. We strongly advise against using it in new code.

use strutPartial()

Returns the strut specified by this client. \*

*See also* [setStrut](netwininfo-obsolete.md#setStrut)()
