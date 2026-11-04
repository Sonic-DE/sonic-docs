---
title: "NETStrut Struct"
description: "Simple strut class for NET classes. This struct is deprecated. We strongly advise against using it in new code."
---

# NETStrut Struct

Simple strut class for NET classes. **This struct is deprecated. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <NETStrut>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **Status:** Deprecated

[List of all members, including inherited members](netstrut-members.md)

## Public Functions

- [NETStrut()](#NETStrut)

**This struct is deprecated. We strongly advise against using it in new code.**

## Detailed Description {#details}

use [NETExtendedStrut](netextendedstrut.md)

This class is a convenience class defining a strut with left, right, top and bottom border values. The existence of this class is to keep the implementation from being dependent on a separate framework/library. See the \_NET\_WM\_STRUT property in the NETWM spec.

## Member Function Documentation {#member-function-documentation}

### NETStrut::NETStrut() {#NETStrut}

Constructor to initialize this struct to 0,0,0,0.

## Member Variable Documentation {#member-variable-documentation}

### int NETStrut::bottom {#bottom-var}

Bottom border of the strut.

### int NETStrut::left {#left-var}

Left border of the strut.

### int NETStrut::right {#right-var}

Right border of the strut.

### int NETStrut::top {#top-var}

Top border of the strut.
