---
title: "KActivities Namespace"
description: "Namespace for everything in libkactivities."
---

# KActivities Namespace

Namespace for everything in libkactivities. [More...](#details)

- **Header:** `#include <KActivities/Version>`
- **CMake:** `find_package(Plasma REQUIRED COMPONENTS Activities)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Activities)`

## Detailed Description {#details}

## Namespaces {#namespaces}

### namespace KActivities::ResourceInstance

## Classes {#classes}

### class [ActivitiesModel](kactivities-activitiesmodel.md)

Data model that shows existing activities.

### class [Consumer](kactivities-consumer.md)

Read-only information about activities.

### class [Controller](kactivities-controller.md)

Methods for controlling and managing the activities.

### class [Info](kactivities-info.md)

Info about an activity.

## Function Documentation {#function-documentation}

### unsigned int KActivities::version() {#version}

The runtime version of libkactivities

### unsigned int KActivities::versionMajor() {#versionMajor}

The runtime major version of libkactivities

### unsigned int KActivities::versionMinor() {#versionMinor}

The runtime major version of libkactivities

### unsigned int KActivities::versionRelease() {#versionRelease}

The runtime major version of libkactivities

### const char \*KActivities::versionString() {#versionString}

The runtime version string of libkactivities
