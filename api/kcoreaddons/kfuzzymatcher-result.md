---
title: ""
description: "The result of a fuzzy match."
---

# 

The result of a fuzzy match. [More...](#details)

- Header: Result
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

## Member Variable Documentation {#member-variable-documentation}

### bool Result::matched {#matched-var}

`true` if match was successful

### int Result::score {#score-var}

This variable holds the score of this match. This can be negative. If matched is `false` then the score will be zero.
