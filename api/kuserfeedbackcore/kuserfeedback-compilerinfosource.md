---
title: "KUserFeedback::CompilerInfoSource Class"
description: "Data source reporting which compiler was used to build this code."
---

# KUserFeedback::CompilerInfoSource Class

Data source reporting which compiler was used to build this code. [More...](#details)

- **Header:** `#include <KUserFeedback/CompilerInfoSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md)

[List of all members, including inherited members](kuserfeedback-compilerinfosource-members.md)

## Public Functions

- [CompilerInfoSource()](#CompilerInfoSource)

## Detailed Description {#details}

> **Note:** This will report which compiler was used to build the feedback library, which technically does not need to be the same as used for the application code. This is particularly true for compilers that don't break ABI regularly (such as Clang and GCC), so this information is most reliable when this is not the case, e.g. with MSVC.

The default telemetry mode for this source is [Provider::BasicSystemInformation](kuserfeedback-provider.md#TelemetryMode-enum).

## Member Function Documentation {#member-function-documentation}

### CompilerInfoSource::CompilerInfoSource() {#CompilerInfoSource}
