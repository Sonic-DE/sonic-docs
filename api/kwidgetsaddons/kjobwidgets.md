---
title: "KJobWidgets Namespace"
description: "Large set of desktop widgets."
---

# KJobWidgets Namespace

Large set of desktop widgets. [More...](#details)

- Header: KJobWidgets
- CMake: find\_package(KF6 REQUIRED COMPONENTS WidgetsAddons) target\_link\_libraries(mytarget PRIVATE KF6::WidgetsAddons)

## Detailed Description {#details}

[KJobWidgets](kjobwidgets.md) namespace

## Function Documentation {#function-documentation}

### \[since 6.0\] void KJobWidgets::setWindow(QObject \**job*, QWidget \**widget*) {#setWindow}

Associate this job with a window given by `window`.

`job` should be a KJob subclass

This is used:

- by KDialogJobUiDelegate as parent widget for error messages
- by KWidgetJobTracker as parent widget for progress dialogs
- by KIO::AbstractJobInteractionInterface as parent widget for rename/skip dialogs and possibly more.
- by KIO::DropJob as parent widget of popup menus. This is required on Wayland to properly position the menu.

This function was introduced in Qt 6.0.

*See also* [window](kjobwidgets.md#window)()

### \[since 6.0\] void KJobWidgets::updateUserTimestamp(QObject \**job*, unsigned long *time*) {#updateUserTimestamp}

Updates the last user action timestamp to the given time.

`job` should be a KJob subclass

This function was introduced in Qt 6.0.

### \[since 6.0\] unsigned long KJobWidgets::userTimestamp(QObject \**job*) {#userTimestamp}

Returns the last user action timestamp

`job` should be a KJob subclass

This function was introduced in Qt 6.0.

### \[since 6.0\] QWidget \*KJobWidgets::window(QObject \**job*) {#window}

Return the window associated with this job.

`job` should be a KJob subclass

This function was introduced in Qt 6.0.

*See also* [setWindow](kjobwidgets.md#setWindow)()

### \[since 6.4\] QWindow \*KJobWidgets::windowHandle(QObject \**job*) {#windowHandle}

Returns the window handle associated with this job.

`job` should be a KJob subclass

@deprecated\[6.5\] use KJobWindows::window() instead.

This function was introduced in Qt 6.4.
