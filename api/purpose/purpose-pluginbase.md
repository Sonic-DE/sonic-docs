---
title: "Purpose::PluginBase Class"
description: "Base class to implement by plugins."
---

# Purpose::PluginBase Class

Base class to implement by plugins. [More...](#details)

- **Header:** `#include <Purpose/PluginBase>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Purpose)`  
  `target_link_libraries(mytarget PRIVATE KF6::Purpose)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](purpose-pluginbase-members.md)

## Public Functions

- [Purpose::Job \*createJob() const](#createJob)

## Detailed Description {#details}

Class for Qt native plugins to extend. Plugins will just be issuing jobs that will be configured then started.

See README.md on how to create plugins on technologies different to Qt.

> **Note:** This file shouldn't be included by any application.

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] Purpose::Job \*PluginBase::createJob() const {#createJob}

Returns the job that will perform the plugin's action.
