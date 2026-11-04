---
title: "NETFullscreenMonitors Struct"
description: "Simple multiple monitor topology class for NET classes."
---

# NETFullscreenMonitors Struct

Simple multiple monitor topology class for NET classes. [More...](#details)

- **Header:** `#include <NETFullscreenMonitors>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`

[List of all members, including inherited members](netfullscreenmonitors-members.md)

## Public Functions

- [NETFullscreenMonitors()](#NETFullscreenMonitors)
- [bool isSet() const](#isSet)

## Detailed Description {#details}

This class is a convenience class, defining a multiple monitor topology for fullscreen applications that wish to be present on more than one monitor/head. As per the \_NET\_WM\_FULLSCREEN\_MONITORS hint in the EWMH spec, this topology consists of 4 monitor indices such that the bounding rectangle is defined by the top edge of the top monitor, the bottom edge of the bottom monitor, the left edge of the left monitor, and the right edge of the right monitor. See the \_NET\_WM\_FULLSCREEN\_MONITORS hint in the EWMH spec.

## Member Function Documentation {#member-function-documentation}

### NETFullscreenMonitors::NETFullscreenMonitors() {#NETFullscreenMonitors}

Constructor to initialize this struct to -1,0,0,0 (an initialized, albeit invalid, topology).

### bool NETFullscreenMonitors::isSet() const {#isSet}

Convenience check to make sure that we don't return the initial (invalid) values.

Note that we don't want to call this isValid() because we're not actually validating the monitor topology here, but merely that our initial values were overwritten at some point by real (non-negative) monitor indices.

## Member Variable Documentation {#member-variable-documentation}

### int NETFullscreenMonitors::bottom {#bottom-var}

Monitor index whose bottom border defines the bottom edge of the topology.

### int NETFullscreenMonitors::left {#left-var}

Monitor index whose left border defines the left edge of the topology.

### int NETFullscreenMonitors::right {#right-var}

Monitor index whose right border defines the right edge of the topology.

### int NETFullscreenMonitors::top {#top-var}

Monitor index whose top border defines the top edge of the topology.
