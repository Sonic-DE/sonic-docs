---
title: "KCommandBar::ActionGroup Struct"
description: "Widgets for configuration dialogs."
---

# KCommandBar::ActionGroup Struct

Widgets for configuration dialogs. [More...](#details)

- **Header:** `#include <ActionGroup>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`

[List of all members, including inherited members](kcommandbar-actiongroup-members.md)

## Detailed Description {#details}

Represents a list of action that belong to the same group. For example:

- All actions under the menu "File" or "Tool"

## Member Variable Documentation {#member-variable-documentation}

### QList\<QAction \*\> ActionGroup::actions {#actions-var}

### QString ActionGroup::name {#name-var}
