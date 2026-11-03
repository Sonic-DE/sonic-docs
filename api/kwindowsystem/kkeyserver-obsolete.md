---
title: "Obsolete Members for KKeyServer"
description: "Deprecated members of KKeyServer Namespace."
parent: "kwindowsystem/kkeyserver"
---

# Obsolete Members for KKeyServer

**The following members of class [KKeyServer](kkeyserver.md) are deprecated.** We strongly advise against using them in new code.

## Obsolete Function Documentation {#obsolete-function-documentation}

### \[deprecated in 6.0\] bool KKeyServer::keyQtToCodeX(int *keyQt*, int \**keyCode*) {#keyQtToCodeX}

This function is deprecated since 6.0. We strongly advise against using it in new code.

Extracts the code from the given Qt key.

`keyQt` the qt key code

`keyCode` if successful, the symbol will be written here

Returns true if successful, false otherwise

Use [keyQtToCodeXs](kkeyserver.md#keyQtToCodeXs)(keyQt)

### \[deprecated in 6.0\] bool KKeyServer::keyQtToSymX(int *keyQt*, int \**sym*) {#keyQtToSymX}

This function is deprecated since 6.0. We strongly advise against using it in new code.

Extracts the symbol from the given Qt key and converts it to an X11 symbol + modifiers.

`keyQt` the qt key code

`sym` if successful, the symbol will be written here

Returns true if successful, false otherwise

Use [keyQtToSymXs](kkeyserver.md#keyQtToSymXs)(keyQt)
