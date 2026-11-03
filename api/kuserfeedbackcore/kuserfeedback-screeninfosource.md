---
title: "KUserFeedback::ScreenInfoSource Class"
description: "Data source for information about connected displays."
---

# KUserFeedback::ScreenInfoSource Class

Data source for information about connected displays. [More...](#details)

- **Header:** `#include <KUserFeedback/ScreenInfoSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md)

[List of all members, including inherited members](kuserfeedback-screeninfosource-members.md)

## Public Functions

- [ScreenInfoSource()](#ScreenInfoSource)

## Detailed Description {#details}

This provides as array of maps containing the following properties:

- height: Height of the corresponding screen in pixel.
- width: Width of the corresponding screen in pixel.
- dpi: Dots per inch of the corresponding screen.

The default telemetry mode for this source is [Provider::DetailedSystemInformation](kuserfeedback-provider.md#TelemetryMode-enum).

## Member Function Documentation {#member-function-documentation}

### ScreenInfoSource::ScreenInfoSource() {#ScreenInfoSource}

Create a new screen information source.
