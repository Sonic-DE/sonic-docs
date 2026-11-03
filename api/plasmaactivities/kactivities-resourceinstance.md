---
title: "KActivities::ResourceInstance Namespace"
description: "Library for interacting with Plasma Activities."
---

# KActivities::ResourceInstance Namespace

Library for interacting with Plasma Activities. [More...](#details)

- Header: KActivities/ResourceInstance
- CMake: find\_package(Plasma REQUIRED COMPONENTS Activities) target\_link\_libraries(mytarget PRIVATE Plasma::Activities)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### void ResourceInstance::notifyAccessed(const QUrl &*uri*, const QString &*application* = QString()) {#notifyAccessed}

This function is used to notify the system that a file, web page or some other resource has been accessed.

`uri` URI of the resource

`application` application's name (the name used for the .desktop file). If not specified, [QCoreApplication::applicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop) is used
