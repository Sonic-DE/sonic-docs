---
title: "KUnitConversion::UpdateJob Class"
description: "Dynamic conversion data update job. This class was introduced in Qt 6.0."
---

# KUnitConversion::UpdateJob Class

Dynamic conversion data update job. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KUnitConversion/UnitCategory>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UnitConversion)`  
  `target_link_libraries(mytarget PRIVATE KF6::UnitConversion)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kunitconversion-updatejob-members.md)

## Signals

- [void finished()](#finished)

## Detailed Description {#details}

Created via the factory methods in KUnitConversion::Updater, useful for getting notified about an update having completed. Update jobs are automatically deleted on completion, but it is also save to delete instances manually.

*See also* [UnitCategory](kunitconversion-unitcategory.md)

## Member Function Documentation {#member-function-documentation}

### \[signal\] void UpdateJob::finished() {#finished}
