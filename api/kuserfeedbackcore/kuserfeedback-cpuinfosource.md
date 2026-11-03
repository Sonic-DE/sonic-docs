---
title: "KUserFeedback::CpuInfoSource Class"
description: "Data source reporting the type and amount of CPUs."
---

# KUserFeedback::CpuInfoSource Class

Data source reporting the type and amount of CPUs. [More...](#details)

- **Header:** `#include <KUserFeedback/CpuInfoSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md)

[List of all members, including inherited members](kuserfeedback-cpuinfosource-members.md)

## Public Functions

- [CpuInfoSource()](#CpuInfoSource)

## Detailed Description {#details}

The default telemetry mode for this source is [Provider::DetailedSystemInformation](kuserfeedback-provider.md#TelemetryMode-enum).

## Member Function Documentation {#member-function-documentation}

### CpuInfoSource::CpuInfoSource() {#CpuInfoSource}
