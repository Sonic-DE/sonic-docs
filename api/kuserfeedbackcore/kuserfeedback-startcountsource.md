---
title: "KUserFeedback::StartCountSource Class"
description: "Data source reporting the total amount of applications starts."
---

# KUserFeedback::StartCountSource Class

Data source reporting the total amount of applications starts. [More...](#details)

- **Header:** `#include <KUserFeedback/StartCountSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md)

[List of all members, including inherited members](kuserfeedback-startcountsource-members.md)

## Public Functions

- [StartCountSource()](#StartCountSource)

## Detailed Description {#details}

The default telemetry mode for this source is [Provider::BasicUsageStatistics](kuserfeedback-provider.md#TelemetryMode-enum).

## Member Function Documentation {#member-function-documentation}

### StartCountSource::StartCountSource() {#StartCountSource}

Create a new start count data source.
