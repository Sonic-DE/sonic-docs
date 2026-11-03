---
title: "KAboutDataListener Class"
description: "Notify about changes in the global application data. This class was introduced in Qt 6.18."
---

# KAboutDataListener Class

Notify about changes in the global application data. This class was introduced in Qt 6.18. [More...](#details)

- **Header:** `#include <KAboutData>`
- **Since:** Qt 6.18
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kaboutdatalistener-members.md)

## Signals

- [void applicationDataChanged()](#applicationDataChanged)

## Detailed Description {#details}

[KAboutData](kaboutdata.md) has a globally accessible instance that represents the aboutdata of the current process. This class allows us to notify about this information having changed.

## Member Function Documentation {#member-function-documentation}

### \[signal\] void KAboutDataListener::applicationDataChanged() {#applicationDataChanged}

Notifies that [KAboutData::setApplicationData](kaboutdata.md#setApplicationData) was called.
