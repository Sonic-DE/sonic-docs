---
title: "KActivities::Consumer Class"
description: "Read-only information about activities."
---

# KActivities::Consumer Class

Read-only information about activities. [More...](#details)

- **Header:** `#include <PlasmaActivities/Consumer>`
- **CMake:** `find_package(Plasma REQUIRED COMPONENTS Activities)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Activities)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [KActivities::Controller](kactivities-controller.md)

[List of all members, including inherited members](kactivities-consumer-members.md)

## Public Types

- [enum Consumer::ServiceStatus](#ServiceStatus-enum)

## Properties

- [\[read-only\] activities : QStringList](#activities-prop)
- [\[read-only\] currentActivity : QString](#currentActivity-prop)
- [\[read-only\] serviceStatus : ServiceStatus](#serviceStatus-prop)

## Public Functions

- [Consumer(QObject \*parent = nullptr)](#Consumer)
- [QStringList activities() const](#activities)
- [QString currentActivity() const](#currentActivity)
- [KActivities::Consumer::ServiceStatus serviceStatus()](#serviceStatus)

## Signals

- [void activitiesChanged(const QStringList &activities)](#activitiesChanged)
- [void activityAdded(const QString &id)](#activityAdded)
- [void activityRemoved(const QString &id)](#activityRemoved)
- [void currentActivityChanged(const QString &id)](#currentActivityChanged)
- [void serviceStatusChanged(KActivities::Consumer::ServiceStatus status)](#serviceStatusChanged)

## Detailed Description {#details}

Contextual information can be, from the user's point of view, divided into three aspects - "who am I?", "where am I?" (what are my surroundings?) and "what am I doing?".

Activities deal with the last one - "what am I doing?". The current activity refers to what the user is doing at the moment, while the other activities represent things that he/she was doing before, and probably will be doing again.

Activity is an abstract concept whose meaning can differ from one user to another. Typical examples of activities are "developing a KDE project", "studying the 19th century art", "composing music", "lazing on a Sunday afternoon" etc.

Consumer provides read-only information about activities.

Before relying on the values retrieved by the class, make sure that the [serviceStatus](kactivities-consumer.md#serviceStatus) is set to Running. Otherwise, you can get invalid data either because the service is not functioning properly (or at all) or because the class did not have enough time to synchronize the data with it.

For example, if this is the only existing instance of the Consumer class, the listActivities method will return an empty list.

```cpp
void someMethod() {
    // Do not copy. This approach is not a good one!
    Consumer c;
    doSomethingWith(c.listActivities());
}
```

Instances of the Consumer class should be long-lived. For example, members of the classes that use them, and you should listen for the changes in the provided properties.

## Member Type Documentation {#member-type-documentation}

### enum Consumer::ServiceStatus {#ServiceStatus-enum}

Different states of the activities service

| Constant | Value | Description |
| --- | --- | --- |
| `KActivities::Consumer::NotRunning` | `0` | Service is not running |
| `KActivities::Consumer::Unknown` | `1` | Unable to determine the status of the service |
| `KActivities::Consumer::Running` | `2` | Service is running properly |

## Property Documentation {#property-documentation}

### \[read-only\] activities : QStringList {#activities-prop}

**Access functions:**

- `QStringList` **[activities](kactivities-consumer.md#activities)**() const

**Notifier signal:**

- `void` **[activitiesChanged](kactivities-consumer.md#activitiesChanged)**(const `QStringList` &*activities*)

### \[read-only\] currentActivity : QString {#currentActivity-prop}

**Access functions:**

- `QString` **[currentActivity](kactivities-consumer.md#currentActivity)**() const

**Notifier signal:**

- `void` **[currentActivityChanged](kactivities-consumer.md#currentActivityChanged)**(const `QString` &*id*)

### \[read-only\] serviceStatus : ServiceStatus {#serviceStatus-prop}

**Access functions:**

- `KActivities::Consumer::ServiceStatus` **[serviceStatus](kactivities-consumer.md#serviceStatus)**()

**Notifier signal:**

- `void` **[serviceStatusChanged](kactivities-consumer.md#serviceStatusChanged)**(`KActivities::Consumer::ServiceStatus` *status*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Consumer::Consumer(QObject \**parent* = nullptr) {#Consumer}

### QStringList Consumer::activities() const {#activities}

Returns the list of all existing activities

> **Note:** If the [serviceStatus](kactivities-consumer.md#serviceStatus) is not Running, only a null activity will be returned.

> **Note:** Getter function for property [activities](kactivities-consumer.md#activities-prop).

### \[signal\] void Consumer::activitiesChanged(const QStringList &*activities*) {#activitiesChanged}

This signal is emitted when the activity list changes

`activities` list of activities

> **Note:** Notifier signal for property [activities](kactivities-consumer.md#activities-prop).

### \[signal\] void Consumer::activityAdded(const QString &*id*) {#activityAdded}

This signal is emitted when a new activity is added

`id` id of the new activity

### \[signal\] void Consumer::activityRemoved(const QString &*id*) {#activityRemoved}

This signal is emitted when an activity has been removed

`id` id of the removed activity

### QString Consumer::currentActivity() const {#currentActivity}

Returns the id of the current activity

> **Note:** Activity ID is a UUID-formatted string. If the [serviceStatus](kactivities-consumer.md#serviceStatus) is not Running, a null UUID is returned. The ID can also be an empty string in the case there is no current activity.

> **Note:** Getter function for property [currentActivity](kactivities-consumer.md#currentActivity-prop).

### \[signal\] void Consumer::currentActivityChanged(const QString &*id*) {#currentActivityChanged}

This signal is emitted when the current activity is changed

`id` id of the new current activity

> **Note:** Notifier signal for property [currentActivity](kactivities-consumer.md#currentActivity-prop).

### KActivities::Consumer::ServiceStatus Consumer::serviceStatus() {#serviceStatus}

Returns status of the activities service

> **Note:** Getter function for property [serviceStatus](kactivities-consumer.md#serviceStatus-prop).

### \[signal\] void Consumer::serviceStatusChanged(KActivities::Consumer::ServiceStatus *status*) {#serviceStatusChanged}

This signal is emitted when the activity service goes online or offline, or when the class manages to synchronize the data with the service.

`status` new status of the service

> **Note:** Notifier signal for property [serviceStatus](kactivities-consumer.md#serviceStatus-prop).
