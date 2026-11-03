---
title: ""
description: "Partial strut class for NET classes."
---

# 

Partial strut class for NET classes. [More...](#details)

- Header: NETExtendedStrut
- CMake: find\_package(KF6 REQUIRED COMPONENTS KWindowSystem) target\_link\_libraries(mytarget PRIVATE KF6::KWindowSystem)

## Detailed Description {#details}

This class is a convenience class defining a strut with left, right, top and bottom border values, and ranges for them. The existence of this class is to keep the implementation from being dependent on a separate framework/library. See the \_NET\_WM\_STRUT\_PARTIAL property in the NETWM spec.

## Member Function Documentation {#member-function-documentation}

### NETExtendedStrut::NETExtendedStrut() {#NETExtendedStrut}

Constructor to initialize this struct to 0,0,0,0.

## Member Variable Documentation {#member-variable-documentation}

### int NETExtendedStrut::bottom\_end {#bottom_end-var}

This variable holds the end of the bottom border of the strut.

### int NETExtendedStrut::bottom\_start {#bottom_start-var}

This variable holds the start of the bottom border of the strut.

### int NETExtendedStrut::bottom\_width {#bottom_width-var}

This variable holds the width of the bottom border of the strut.

### int NETExtendedStrut::left\_end {#left_end-var}

This variable holds the end of the left border of the strut.

### int NETExtendedStrut::left\_start {#left_start-var}

This variable holds the start of the left border of the strut.

### int NETExtendedStrut::left\_width {#left_width-var}

This variable holds the width of the left border of the strut.

### int NETExtendedStrut::right\_end {#right_end-var}

This variable holds the end of the right border of the strut.

### int NETExtendedStrut::right\_start {#right_start-var}

This variable holds the start of the right border of the strut.

### int NETExtendedStrut::right\_width {#right_width-var}

The width of the right border of the strut.

### int NETExtendedStrut::top\_end {#top_end-var}

This variable holds the end of the top border of the strut.

### int NETExtendedStrut::top\_start {#top_start-var}

This variable holds the start of the top border of the strut.

### int NETExtendedStrut::top\_width {#top_width-var}

This variable holds the width of the top border of the strut.
