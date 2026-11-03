---
title: "KUserFeedback::UsageTimeSource Class"
description: "Data source reporting the total usage time of the application."
---

# KUserFeedback::UsageTimeSource Class

Data source reporting the total usage time of the application. [More...](#details)

- **Header:** `#include <KUserFeedback/UsageTimeSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md)

[List of all members, including inherited members](kuserfeedback-usagetimesource-members.md)

## Public Functions

- [UsageTimeSource()](#UsageTimeSource)

## Detailed Description {#details}

The default telemetry mode for this source is [Provider::BasicUsageStatistics](kuserfeedback-provider.md#TelemetryMode-enum).

## Member Function Documentation {#member-function-documentation}

### UsageTimeSource::UsageTimeSource() {#UsageTimeSource}

Create a new usage time data source.
