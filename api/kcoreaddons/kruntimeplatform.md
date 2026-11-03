---
title: "KRuntimePlatform Namespace"
description: "Utility functions around the runtime platform."
---

# KRuntimePlatform Namespace

Utility functions around the runtime platform. [More...](#details)

- Header: KRuntimePlatform
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### QStringList KRuntimePlatform::runtimePlatform() {#runtimePlatform}

Returns the runtime platform, e.g. "desktop" or "tablet, touch". The first entry/ies in the list relate to the platform formfactor and the last is the input method specialization.

If the string is empty, there is no specified runtime platform and a traditional desktop environment may be assumed.

The value is read using the PLASMA\_PLATFORM env variable
