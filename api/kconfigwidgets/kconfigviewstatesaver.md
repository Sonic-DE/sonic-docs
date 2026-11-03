---
title: "KConfigViewStateSaver Class"
description: "Base class for saving and restoring state in QTreeViews and QItemSelectionModels using KConfig as storage."
---

# KConfigViewStateSaver Class

Base class for saving and restoring state in QTreeViews and QItemSelectionModels using [KConfig](../kconfigcore/kconfig.md) as storage. [More...](#details)

- **Header:** `#include <KConfigViewStateSaver>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`
- **Inherits:** [KViewStateSerializer](../kwidgetsaddons/kviewstateserializer.md)

[List of all members, including inherited members](kconfigviewstatesaver-members.md)

## Public Functions

- [void restoreState(const KConfigGroup &configGroup)](#restoreState)
- [void saveState(KConfigGroup &configGroup)](#saveState)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### void KConfigViewStateSaver::restoreState(const KConfigGroup &*configGroup*) {#restoreState}

Restores the state from the `configGroup`

### void KConfigViewStateSaver::saveState(KConfigGroup &*configGroup*) {#saveState}

Saves the state to the `configGroup`
