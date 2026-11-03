---
title: "KNSWidgets::Action Class"
description: "QAction subclass that encapsulates the logic for showing the KNewStuff dialog."
---

# KNSWidgets::Action Class

QAction subclass that encapsulates the logic for showing the KNewStuff dialog. [More...](#details)

- **Header:** `#include <Action>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`

[List of all members, including inherited members](knswidgets-action-members.md)

## Public Functions

- [Action(const QString &text, const QString &configFile, QObject \*parent)](#Action)

## Signals

- [void dialogFinished(const QList\<KNSCore::Entry\> &changedEntries)](#dialogFinished)

## Detailed Description {#details}

If KNewStuff is disabled using [KAuthorized](../kconfigcore/kauthorized.md), the action is hidden.

*See also* [KAuthorized::GenericRestriction::GHNS](../kconfigcore/kauthorized.md#GenericRestriction-enum)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Action::Action(const QString &*text*, const QString &*configFile*, QObject \**parent*) {#Action}

Constructs a [KNSWidgets::Action](knswidgets-action.md) instance.

`text` describing what is being downloaded. It should be a text beginning with "Download New ..." for consistency

`configFile` the name of the .knsrc file

`parent` the parent object

### \[signal\] void Action::dialogFinished(const QList\<KNSCore::Entry\> &*changedEntries*) {#dialogFinished}

Emitted when the dialog has been closed.

`changedEntries` contains the entries that were changed
