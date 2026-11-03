---
title: "KActivities::Info Class"
description: "Info about an activity."
---

# KActivities::Info Class

Info about an activity. [More...](#details)

- **Header:** `#include <PlasmaActivities/Info>`
- **CMake:** `find_package(Plasma REQUIRED COMPONENTS Activities)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Activities)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kactivities-info-members.md)

## Public Types

- [enum Info::Availability](#Availability-enum)

## Properties

- [\[read-only\] description : QString](#description-prop)
- [\[read-only\] icon : QString](#icon-prop)
- [\[read-only\] id : QString](#id-prop)
- [\[read-only\] isCurrent : bool](#isCurrent-prop)
- [\[read-only\] name : QString](#name-prop)

## Public Functions

- [Info(const QString &activity, QObject \*parent = nullptr)](#Info)
- [KActivities::Info::Availability availability() const](#availability)
- [QString description() const](#description)
- [QString icon() const](#icon)
- [QString id() const](#id)
- [bool isCurrent() const](#isCurrent)
- [QString name() const](#name)
- [QString uri() const](#uri)

## Signals

- [void added()](#added)
- [void descriptionChanged(const QString &description)](#descriptionChanged)
- [void iconChanged(const QString &icon)](#iconChanged)
- [void infoChanged()](#infoChanged)
- [void isCurrentChanged(bool current)](#isCurrentChanged)
- [void nameChanged(const QString &name)](#nameChanged)
- [void removed()](#removed)

## Detailed Description {#details}

Most methods in it require a semantic backend running to function properly.

This class is not thread-safe.

The API of the class is synchronous, but the most used properties are pre-fetched and cached. This means that, in order to get the least amount of d-bus related locks, you should declare long-lived instances of this class.

Before relying on the values retrieved by the class, make sure that the state is not Info::Unknown. You can get invalid data either because the service is not functioning properly (or at all) or because the class did not have enough time to synchronize the data with it.

For example, if this is the only existing instance of the Info class, the name method will return an empty string.

For example, this is wrong (works, but blocks):

```cpp
void someMethod(const QString & activity) {
    // Do not copy. This approach is not a good one!
    Info info(activity);
    doSomethingWith(info.name());
}
```

Instances of the Info class should be long-lived. For example, members of the classes that use them, and you should listen for the changes in the provided properties.

## Member Type Documentation {#member-type-documentation}

### enum Info::Availability {#Availability-enum}

Specifies which parts of this class are functional

| Constant | Value | Description |
| --- | --- | --- |
| `KActivities::Info::Nothing` | `0` | No activity info provided (isValid is false) |
| `KActivities::Info::BasicInfo` | `1` | Basic info is provided |
| `KActivities::Info::Everything` | `2` | Everything is available |

## Property Documentation {#property-documentation}

### \[read-only\] description : QString {#description-prop}

**Access functions:**

- `QString` **[description](kactivities-info.md#description)**() const

**Notifier signal:**

- `void` **[descriptionChanged](kactivities-info.md#descriptionChanged)**(const `QString` &*description*)

### \[read-only\] icon : QString {#icon-prop}

**Access functions:**

- `QString` **[icon](kactivities-info.md#icon)**() const

**Notifier signal:**

- `void` **[iconChanged](kactivities-info.md#iconChanged)**(const `QString` &*icon*)

### \[read-only\] id : QString {#id-prop}

**Access functions:**

- `QString` **[id](kactivities-info.md#id)**() const

### \[read-only\] isCurrent : bool {#isCurrent-prop}

**Access functions:**

- `bool` **[isCurrent](kactivities-info.md#isCurrent)**() const

**Notifier signal:**

- `void` **[isCurrentChanged](kactivities-info.md#isCurrentChanged)**(`bool` *current*)

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **[name](kactivities-info.md#name)**() const

**Notifier signal:**

- `void` **[nameChanged](kactivities-info.md#nameChanged)**(const `QString` &*name*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Info::Info(const QString &*activity*, QObject \**parent* = nullptr) {#Info}

### \[signal\] void Info::added() {#added}

Emitted when the activity is added

### KActivities::Info::Availability Info::availability() const {#availability}

Returns what info is provided by this instance of Info

### QString Info::description() const {#description}

Returns the description of the activity

> **Note:** Getter function for property [description](kactivities-info.md#description-prop).

### \[signal\] void Info::descriptionChanged(const QString &*description*) {#descriptionChanged}

Emitted when the description is changed

> **Note:** Notifier signal for property [description](kactivities-info.md#description-prop).

### QString Info::icon() const {#icon}

Returns the icon of the activity. Icon can be a freedesktop.org name or a file path. Or empty if no icon is set.

> **Note:** Getter function for property [icon](kactivities-info.md#icon-prop).

### \[signal\] void Info::iconChanged(const QString &*icon*) {#iconChanged}

Emitted when the icon was changed

> **Note:** Notifier signal for property [icon](kactivities-info.md#icon-prop).

### QString Info::id() const {#id}

Returns the id of the activity

> **Note:** Getter function for property [id](kactivities-info.md#id-prop).

### \[signal\] void Info::infoChanged() {#infoChanged}

Emitted when the activity's name, icon or some custom property is changed

### bool Info::isCurrent() const {#isCurrent}

Returns whether this activity is the current one

> **Note:** Getter function for property [isCurrent](kactivities-info.md#isCurrent-prop).

### \[signal\] void Info::isCurrentChanged(bool *current*) {#isCurrentChanged}

Emitted when the activity becomes the current one, or when it stops being the current one

> **Note:** Notifier signal for property [isCurrent](kactivities-info.md#isCurrent-prop).

### QString Info::name() const {#name}

Returns the name of the activity

> **Note:** Getter function for property [name](kactivities-info.md#name-prop).

### \[signal\] void Info::nameChanged(const QString &*name*) {#nameChanged}

Emitted when the name is changed

> **Note:** Notifier signal for property [name](kactivities-info.md#name-prop).

### \[signal\] void Info::removed() {#removed}

Emitted when the activity is removed

### QString Info::uri() const {#uri}

Returns the URI of this activity. The same URI is used by activities KIO worker.
