---
title: "KFuzzyMatcher::Result Struct"
description: "The result of a fuzzy match."
---

# KFuzzyMatcher::Result Struct

The result of a fuzzy match. [More...](#details)

- **Header:** `#include <Result>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kfuzzymatcher-result-members.md)

## Detailed Description {#details}

## Member Variable Documentation {#member-variable-documentation}

### bool Result::matched {#matched-var}

`true` if match was successful

### int Result::score {#score-var}

This variable holds the score of this match. This can be negative. If matched is `false` then the score will be zero.
