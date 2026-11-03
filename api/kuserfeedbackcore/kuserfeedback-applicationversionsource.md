---
title: "KUserFeedback::ApplicationVersionSource Class"
description: "Data source for the application version."
---

# KUserFeedback::ApplicationVersionSource Class

Data source for the application version. [More...](#details)

- **Header:** `#include <KUserFeedback/ApplicationVersionSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md)

[List of all members, including inherited members](kuserfeedback-applicationversionsource-members.md)

## Public Functions

- [ApplicationVersionSource()](#ApplicationVersionSource)

## Detailed Description {#details}

The application version is retrieved via [QCoreApplication::applicationVersion](https://doc.qt.io/qt-6/qcoreapplication.html#applicationVersion-prop).

The default telemetry mode for this source is [Provider::BasicSystemInformation](kuserfeedback-provider.md#TelemetryMode-enum).

## Member Function Documentation {#member-function-documentation}

### ApplicationVersionSource::ApplicationVersionSource() {#ApplicationVersionSource}

Create a new application version source.
