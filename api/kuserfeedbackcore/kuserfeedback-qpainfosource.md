---
title: "KUserFeedback::QPAInfoSource Class"
description: "Reports information about the Qt platform abstraction plugin the application is running on."
---

# KUserFeedback::QPAInfoSource Class

Reports information about the Qt platform abstraction plugin the application is running on. [More...](#details)

- **Header:** `#include <KUserFeedback/QPAInfoSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md)

[List of all members, including inherited members](kuserfeedback-qpainfosource-members.md)

## Public Functions

- [QPAInfoSource()](#QPAInfoSource)

## Detailed Description {#details}

The default telemetry mode for this source is [Provider::BasicSystemInformation](kuserfeedback-provider.md#TelemetryMode-enum).

## Member Function Documentation {#member-function-documentation}

### QPAInfoSource::QPAInfoSource() {#QPAInfoSource}
