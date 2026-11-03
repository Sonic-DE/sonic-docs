---
title: "KUserFeedback::SelectionRatioSource Class"
description: "Records the time ratio a given entry is selected via a QItemSelectionModel."
---

# KUserFeedback::SelectionRatioSource Class

Records the time ratio a given entry is selected via a [QItemSelectionModel](https://doc.qt.io/qt-6/qitemselectionmodel.html). [More...](#details)

- **Header:** `#include <KUserFeedback/SelectionRatioSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md)

[List of all members, including inherited members](kuserfeedback-selectionratiosource-members.md)

## Public Functions

- [SelectionRatioSource(QItemSelectionModel \*selectionModel, const QString &sampleName)](#SelectionRatioSource)
- [void setDescription(const QString &desc)](#setDescription)
- [void setRole(int role)](#setRole)

## Detailed Description {#details}

An example use-case would be the usage ratio of a applications views/modes selected using a model-based view sidebar (such as used in e.g. Kontact).

The default telemetry mode for this source is [Provider::DetailedUsageStatistics](kuserfeedback-provider.md#TelemetryMode-enum).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] SelectionRatioSource::SelectionRatioSource(QItemSelectionModel \**selectionModel*, const QString &*sampleName*) {#SelectionRatioSource}

Create a new selection ratio data source.

`selectionModel` The selection to monitor.

`sampleName` This is the name of the database field this data source is associated with.

### void SelectionRatioSource::setDescription(const QString &*desc*) {#setDescription}

Set human-readable and translated description of the data provided by this source.

> **Note:** This must be set before adding this source, sources without description are discarded.

`desc` The description.

### void SelectionRatioSource::setRole(int *role*) {#setRole}

Determine which role to consider for the reported value. By default this is [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum).
