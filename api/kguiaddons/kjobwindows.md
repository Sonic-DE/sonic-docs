---
title: "KJobWindows Namespace"
description: "Associate jobs with a window."
---

# KJobWindows Namespace

Associate jobs with a window. [More...](#details)

- **Header:** `#include <KJobWindows>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### \[since 6.0\] void KJobWindows::setWindow(QObject \**job*, QWindow \**window*) {#setWindow}

Associate this job with a window given by `window`.

`job` should be a [KJob](../kcoreaddons/kjob.md) subclass

This is used:

- by [KDialogJobUiDelegate](../kjobwidgets/kdialogjobuidelegate.md) as parent widget for error messages
- by [KWidgetJobTracker](../kjobwidgets/kwidgetjobtracker.md) as parent widget for progress dialogs
- by KIO::AbstractJobInteractionInterface as parent widget for rename/skip dialogs and possibly more.
- by [KIO::DropJob](../kiowidgets/kio-dropjob.md) as parent widget of popup menus.

This function was introduced in Qt 6.0.

*See also* [window](kjobwindows.md#window)()

### \[since 6.0\] QWindow \*KJobWindows::window(QObject \**job*) {#window}

Returns the window associated with this job.

`job` should be a [KJob](../kcoreaddons/kjob.md) subclass

This function was introduced in Qt 6.0.

*See also* [setWindow](kjobwindows.md#setWindow)()
