---
title: "KStyleManager Namespace"
description: "Manager for Qt widget styles."
---

# KStyleManager Namespace

Manager for Qt widget styles. [More...](#details)

- Header: KStyleManager
- CMake: find\_package(KF6 REQUIRED COMPONENTS ConfigWidgets) target\_link\_libraries(mytarget PRIVATE KF6::ConfigWidgets)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### \[since 6.3\] QAction \*KStyleManager::createConfigureAction(QObject \**parent* = nullptr) {#createConfigureAction}

Creates an action to configure the current used style.

If the application is running using the KDE platform theme, this will just return a disabled and hidden action, else it will provide an action to show a menu to select the style to use for this applications.

This function was introduced in Qt 6.3.

### \[since 6.3\] void KStyleManager::initStyle() {#initStyle}

Enforces the style configured by the user with fallback to the Breeze style.

(following the settings in the application configuration with fallback to kdeglobals)

Must be called after one has constructed the [QApplication](https://doc.qt.io/qt-6/qapplication.html).

If the application is already using the KDE platform theme, the style will not be touched and the platform theme will ensure proper styling.

This function was introduced in Qt 6.3.
