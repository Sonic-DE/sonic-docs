---
title: "KActivities::Controller Class"
description: "Methods for controlling and managing the activities."
---

# KActivities::Controller Class

Methods for controlling and managing the activities. [More...](#details)

- **Header:** `#include <PlasmaActivities/Controller>`
- **CMake:** `find_package(Plasma REQUIRED COMPONENTS Activities)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Activities)`
- **Inherits:** [KActivities::Consumer](kactivities-consumer.md)

[List of all members, including inherited members](kactivities-controller-members.md)

## Properties

- [currentActivity : QString](#currentActivity-prop)

## Public Functions

- [Controller(QObject \*parent = nullptr)](#Controller)
- [QFuture\<QString\> addActivity(const QString &name)](#addActivity)
- [QFuture\<void\> nextActivity()](#nextActivity)
- [QFuture\<void\> previousActivity()](#previousActivity)
- [QFuture\<void\> removeActivity(const QString &id)](#removeActivity)
- [QFuture\<void\> setActivityDescription(const QString &id, const QString &description)](#setActivityDescription)
- [QFuture\<void\> setActivityIcon(const QString &id, const QString &icon)](#setActivityIcon)
- [QFuture\<void\> setActivityName(const QString &id, const QString &name)](#setActivityName)
- [QFuture\<bool\> setCurrentActivity(const QString &id)](#setCurrentActivity)

## Detailed Description {#details}

> **Note:** The [QFuture](https://doc.qt.io/qt-6/qfuture.html) objects returned by these methods are not thread-based, you can not call synchronous methods like waitForFinished, cancel, pause on them. You need either to register watchers to check when those have finished, or to check whether they are ready from time to time manually.

## Property Documentation {#property-documentation}

### currentActivity : QString {#currentActivity-prop}

**Access functions:**

- `QString` **[currentActivity](kactivities-consumer.md#currentActivity)**() const
- `QFuture`\<`bool`\> **[setCurrentActivity](kactivities-controller.md#setCurrentActivity)**(const `QString` &*id*)

**Notifier signal:**

- `void` **[currentActivityChanged](kactivities-consumer.md#currentActivityChanged)**(const `QString` &*id*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Controller::Controller(QObject \**parent* = nullptr) {#Controller}

### QFuture\<QString\> Controller::addActivity(const QString &*name*) {#addActivity}

Adds a new activity

`name` name of the activity

Returns the id of the newly created activity

### QFuture\<void\> Controller::nextActivity() {#nextActivity}

Switches to the next activity

### QFuture\<void\> Controller::previousActivity() {#previousActivity}

Switches to the previous activity

### QFuture\<void\> Controller::removeActivity(const QString &*id*) {#removeActivity}

Removes the specified activity

`id` id of the activity to delete

### QFuture\<void\> Controller::setActivityDescription(const QString &*id*, const QString &*description*) {#setActivityDescription}

Sets the description of the specified activity

`id` id of the activity

`description` description to be set

### QFuture\<void\> Controller::setActivityIcon(const QString &*id*, const QString &*icon*) {#setActivityIcon}

Sets the icon of the specified activity

`id` id of the activity

`icon` icon to be set - freedesktop.org name or file path

### QFuture\<void\> Controller::setActivityName(const QString &*id*, const QString &*name*) {#setActivityName}

Sets the name of the specified activity

`id` id of the activity

`name` name to be set

### QFuture\<bool\> Controller::setCurrentActivity(const QString &*id*) {#setCurrentActivity}

Sets the current activity

`id` id of the activity to make current

Returns `true` if successful

> **Note:** Setter function for property [currentActivity](kactivities-controller.md#currentActivity-prop).
