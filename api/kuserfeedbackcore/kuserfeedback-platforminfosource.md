---
title: "KUserFeedback::PlatformInfoSource Class"
description: "Reports information about the platform the application is running on."
---

# KUserFeedback::PlatformInfoSource Class

Reports information about the platform the application is running on. [More...](#details)

- **Header:** `#include <KUserFeedback/PlatformInfoSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md)

[List of all members, including inherited members](kuserfeedback-platforminfosource-members.md)

## Public Functions

- [PlatformInfoSource()](#PlatformInfoSource)

## Detailed Description {#details}

This includes two string data fields:

- platform.os: the operating system name
- platform.version: the operating system or distribution version.

The default telemetry mode for this source is [Provider::BasicSystemInformation](kuserfeedback-provider.md#TelemetryMode-enum).

## Member Function Documentation {#member-function-documentation}

### PlatformInfoSource::PlatformInfoSource() {#PlatformInfoSource}

Create a new platform information source.
