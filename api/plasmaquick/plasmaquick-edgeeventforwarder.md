---
title: "PlasmaQuick::EdgeEventForwarder Class"
description: "The EdgeEventForwarder class."
---

# PlasmaQuick::EdgeEventForwarder Class

The [EdgeEventForwarder](plasmaquick-edgeeventforwarder.md) class. [More...](#details)

- **Header:** `#include <EdgeEventForwarder>`
- **CMake:** `find_package(PlasmaQuick REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::PlasmaQuick)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](plasmaquick-edgeeventforwarder-members.md)

## Public Functions

- [EdgeEventForwarder(QWindow \*parent)](#EdgeEventForwarder)
- [void setActiveEdges(Qt::Edges edges)](#setActiveEdges)
- [void setMargins(const QMargins &margins)](#setMargins)

## Detailed Description {#details}

This class forwards edge events to be replayed within the given margin. This is useful if children do not touch the edge of a window, but want to get input events.

## Member Function Documentation {#member-function-documentation}

### EdgeEventForwarder::EdgeEventForwarder(QWindow \**parent*) {#EdgeEventForwarder}

[EdgeEventForwarder](plasmaquick-edgeeventforwarder.md) constructor.

`window` The window to intercept and filter

The event forwarder is parented to the window.

### void EdgeEventForwarder::setActiveEdges(Qt::Edges *edges*) {#setActiveEdges}

Sets which margins should be active for edge forwarding.

Typically this should match edges touching a screen edge.

> **Note:** Setter function for property activeEdges.

*See also* activeEdges()

### void EdgeEventForwarder::setMargins(const QMargins &*margins*) {#setMargins}

Sets the margins to use for the event forwarding.

> **Note:** Setter function for property margins.

*See also* margins()
