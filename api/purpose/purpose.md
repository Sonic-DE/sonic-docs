---
title: "Purpose Namespace"
description: "Framework for providing abstractions to get the developer's purposes fulfilled.."
---

# Purpose Namespace

Framework for providing abstractions to get the developer's purposes fulfilled.. [More...](#details)

- Header: Purpose
- CMake: find\_package(KF6 REQUIRED COMPONENTS Purpose) target\_link\_libraries(mytarget PRIVATE KF6::Purpose)

## Detailed Description {#details}

## Classes {#classes}

### class [AlternativesModel](purpose-alternativesmodel.md)

Interface for client applications to share data.

### class [Configuration](purpose-configuration.md)

This class will be in charge of figuring out the job configuration.

### class [Job](purpose-job.md)

Job that will actually perform the sharing.

### class [PluginBase](purpose-pluginbase.md)

Base class to implement by plugins.
