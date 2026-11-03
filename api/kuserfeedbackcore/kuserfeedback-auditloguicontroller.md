---
title: "KUserFeedback::AuditLogUiController Class"
description: "Widget/QtQuick-independent logic and data for the audit log browser UI."
---

# KUserFeedback::AuditLogUiController Class

Widget/QtQuick-independent logic and data for the audit log browser UI. [More...](#details)

- **Header:** `#include <KUserFeedback/AuditLogUiController>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kuserfeedback-auditloguicontroller-members.md)

## Properties

- [\[read-only\] hasLogEntries : bool](#hasLogEntries-prop)
- [\[read-only\] logEntryModel : QAbstractItemModel\* const](#logEntryModel-prop)

## Public Functions

- [AuditLogUiController(QObject \*parent = nullptr)](#AuditLogUiController)
- [bool hasLogEntries() const](#hasLogEntries)
- [QString logEntry(const QDateTime &dt) const](#logEntry)
- [QAbstractItemModel \*logEntryModel() const](#logEntryModel)

## Public Slots

- [void clear()](#clear)

## Signals

- [void logEntryCountChanged()](#logEntryCountChanged)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[read-only\] hasLogEntries : bool {#hasLogEntries-prop}

Returns `true` if there are log entries to display.

**Access functions:**

- `bool` **[hasLogEntries](kuserfeedback-auditloguicontroller.md#hasLogEntries)**() const

**Notifier signal:**

- `void` **[logEntryCountChanged](kuserfeedback-auditloguicontroller.md#logEntryCountChanged)**()

### \[read-only\] logEntryModel : QAbstractItemModel\* const {#logEntryModel-prop}

Returns a model listing all log entries.

**Access functions:**

- `QAbstractItemModel` \***[logEntryModel](kuserfeedback-auditloguicontroller.md#logEntryModel)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AuditLogUiController::AuditLogUiController(QObject \**parent* = nullptr) {#AuditLogUiController}

### \[slot\] void AuditLogUiController::clear() {#clear}

Delete all audit log entries.

### bool AuditLogUiController::hasLogEntries() const {#hasLogEntries}

Returns `true` if there are log entries to display.

> **Note:** Getter function for property [hasLogEntries](kuserfeedback-auditloguicontroller.md#hasLogEntries-prop).

### \[invokable\] QString AuditLogUiController::logEntry(const QDateTime &*dt*) const {#logEntry}

Returns a formatted text for display of the specified log entry.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[signal\] void AuditLogUiController::logEntryCountChanged() {#logEntryCountChanged}

Change notification for the [hasLogEntries](kuserfeedback-auditloguicontroller.md#hasLogEntries) property.

> **Note:** Notifier signal for property [hasLogEntries](kuserfeedback-auditloguicontroller.md#hasLogEntries-prop).

### QAbstractItemModel \*AuditLogUiController::logEntryModel() const {#logEntryModel}

Returns a model listing all telemetry data submission events.

[Qt::UserRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) contains the timestamp of the log entry for use in [logEntry](kuserfeedback-auditloguicontroller.md#logEntry)().

> **Note:** Getter function for property [logEntryModel](kuserfeedback-auditloguicontroller.md#logEntryModel-prop).
