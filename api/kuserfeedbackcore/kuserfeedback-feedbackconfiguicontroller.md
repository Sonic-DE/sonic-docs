---
title: "KUserFeedback::FeedbackConfigUiController Class"
description: "Logic/behavior of the feedback configuration UI."
---

# KUserFeedback::FeedbackConfigUiController Class

Logic/behavior of the feedback configuration UI. [More...](#details)

- **Header:** `#include <KUserFeedback/FeedbackConfigUiController>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kuserfeedback-feedbackconfiguicontroller-members.md)

## Properties

- [applicationName : QString](#applicationName-prop)
- [feedbackProvider : KUserFeedback::Provider\*](#feedbackProvider-prop)
- [\[read-only\] surveyModeCount : const int](#surveyModeCount-prop)
- [\[read-only\] telemetryModeCount : int](#telemetryModeCount-prop)

## Public Functions

- [FeedbackConfigUiController(QObject \*parent = nullptr)](#FeedbackConfigUiController)
- [QString applicationName() const](#applicationName)
- [KUserFeedback::Provider \*feedbackProvider() const](#feedbackProvider)
- [void setApplicationName(const QString &appName)](#setApplicationName)
- [void setFeedbackProvider(KUserFeedback::Provider \*provider)](#setFeedbackProvider)
- [int surveyIndexToInterval(int index) const](#surveyIndexToInterval)
- [int surveyIntervalToIndex(int interval) const](#surveyIntervalToIndex)
- [int surveyModeCount() const](#surveyModeCount)
- [QString surveyModeDescription(int surveyIndex) const](#surveyModeDescription)
- [QString telemetryDescription(KUserFeedback::Provider::TelemetryMode mode) const](#telemetryDescription)
- [KUserFeedback::Provider::TelemetryMode telemetryIndexToMode(int index) const](#telemetryIndexToMode)
- [int telemetryModeCount() const](#telemetryModeCount)
- [QString telemetryModeDescription(int telemetryIndex) const](#telemetryModeDescription)
- [QString telemetryModeDetails(int telemetryIndex) const](#telemetryModeDetails)
- [QString telemetryModeName(int telemetryIndex) const](#telemetryModeName)
- [int telemetryModeToIndex(KUserFeedback::Provider::TelemetryMode mode) const](#telemetryModeToIndex)
- [QString telemetryName(KUserFeedback::Provider::TelemetryMode mode) const](#telemetryName)

## Signals

- [void applicationNameChanged(const QString &applicationName)](#applicationNameChanged)
- [void providerChanged()](#providerChanged)

## Detailed Description {#details}

This is available for use in e.g. QtQuick-based UIs.

*See also* [KUserFeedback::FeedbackConfigWidget](kuserfeedback-index.md)

## Property Documentation {#property-documentation}

### applicationName : QString {#applicationName-prop}

Name of the application that will appear on descriptions. By default it will use QGuiApplication::applicationDisplayName()

**Access functions:**

- `QString` **[applicationName](kuserfeedback-feedbackconfiguicontroller.md#applicationName)**() const
- `void` **[setApplicationName](kuserfeedback-feedbackconfiguicontroller.md#setApplicationName)**(const `QString` &*appName*)

**Notifier signal:**

- `void` **[applicationNameChanged](kuserfeedback-feedbackconfiguicontroller.md#applicationNameChanged)**(const `QString` &*applicationName*)

### feedbackProvider : KUserFeedback::Provider\* {#feedbackProvider-prop}

The Provider instance we are configuring.

**Access functions:**

- `KUserFeedback::Provider` \***[feedbackProvider](kuserfeedback-feedbackconfiguicontroller.md#feedbackProvider)**() const
- `void` **[setFeedbackProvider](kuserfeedback-feedbackconfiguicontroller.md#setFeedbackProvider)**(`KUserFeedback::Provider` \**provider*)

**Notifier signal:**

- `void` **[providerChanged](kuserfeedback-feedbackconfiguicontroller.md#providerChanged)**()

### \[read-only\] surveyModeCount : const int {#surveyModeCount-prop}

Amount of supported survey modes.

**Access functions:**

- `int` **[surveyModeCount](kuserfeedback-feedbackconfiguicontroller.md#surveyModeCount)**() const

### \[read-only\] telemetryModeCount : int {#telemetryModeCount-prop}

Amount of telemetry modes supported by the provider.

**Access functions:**

- `int` **[telemetryModeCount](kuserfeedback-feedbackconfiguicontroller.md#telemetryModeCount)**() const

**Notifier signal:**

- `void` **[providerChanged](kuserfeedback-feedbackconfiguicontroller.md#providerChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] FeedbackConfigUiController::FeedbackConfigUiController(QObject \**parent* = nullptr) {#FeedbackConfigUiController}

### QString FeedbackConfigUiController::applicationName() const {#applicationName}

> **Note:** Getter function for property [applicationName](kuserfeedback-feedbackconfiguicontroller.md#applicationName-prop).

*See also* [setApplicationName](kuserfeedback-feedbackconfiguicontroller.md#setApplicationName)()

### \[signal\] void FeedbackConfigUiController::applicationNameChanged(const QString &*applicationName*) {#applicationNameChanged}

> **Note:** Notifier signal for property [applicationName](kuserfeedback-feedbackconfiguicontroller.md#applicationName-prop).

### KUserFeedback::Provider \*FeedbackConfigUiController::feedbackProvider() const {#feedbackProvider}

Returns the feedback provider to be configured.

> **Note:** Getter function for property [feedbackProvider](kuserfeedback-feedbackconfiguicontroller.md#feedbackProvider-prop).

*See also* [setFeedbackProvider](kuserfeedback-feedbackconfiguicontroller.md#setFeedbackProvider)()

### \[signal\] void FeedbackConfigUiController::providerChanged() {#providerChanged}

A provider-related setting has changed.

> **Note:** Notifier signal for properties [feedbackProvider](kuserfeedback-feedbackconfiguicontroller.md#feedbackProvider-prop) and [telemetryModeCount](kuserfeedback-feedbackconfiguicontroller.md#telemetryModeCount-prop).

### void FeedbackConfigUiController::setApplicationName(const QString &*appName*) {#setApplicationName}

> **Note:** Setter function for property [applicationName](kuserfeedback-feedbackconfiguicontroller.md#applicationName-prop).

*See also* [applicationName](kuserfeedback-feedbackconfiguicontroller.md#applicationName)()

### void FeedbackConfigUiController::setFeedbackProvider(KUserFeedback::Provider \**provider*) {#setFeedbackProvider}

Set the feedback provider to configure.

> **Note:** Setter function for property [feedbackProvider](kuserfeedback-feedbackconfiguicontroller.md#feedbackProvider-prop).

*See also* [feedbackProvider](kuserfeedback-feedbackconfiguicontroller.md#feedbackProvider)()

### \[invokable\] int FeedbackConfigUiController::surveyIndexToInterval(int *index*) const {#surveyIndexToInterval}

Convert slider index to survey interval.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] int FeedbackConfigUiController::surveyIntervalToIndex(int *interval*) const {#surveyIntervalToIndex}

Convert survey interval to slider index.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### int FeedbackConfigUiController::surveyModeCount() const {#surveyModeCount}

Amount of supported survey modes.

> **Note:** Getter function for property [surveyModeCount](kuserfeedback-feedbackconfiguicontroller.md#surveyModeCount-prop).

### \[invokable\] QString FeedbackConfigUiController::surveyModeDescription(int *surveyIndex*) const {#surveyModeDescription}

Survey mode explanation text.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QString FeedbackConfigUiController::telemetryDescription(KUserFeedback::Provider::TelemetryMode *mode*) const {#telemetryDescription}

Telemetry mode explanation text.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] KUserFeedback::Provider::TelemetryMode FeedbackConfigUiController::telemetryIndexToMode(int *index*) const {#telemetryIndexToMode}

Convert slider index to telemetry mode.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### int FeedbackConfigUiController::telemetryModeCount() const {#telemetryModeCount}

Amount of supported telemetry modes. This depends on what type of sources the provider actually has.

> **Note:** Getter function for property [telemetryModeCount](kuserfeedback-feedbackconfiguicontroller.md#telemetryModeCount-prop).

### \[invokable\] QString FeedbackConfigUiController::telemetryModeDescription(int *telemetryIndex*) const {#telemetryModeDescription}

Telemetry mode explanation text.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QString FeedbackConfigUiController::telemetryModeDetails(int *telemetryIndex*) const {#telemetryModeDetails}

Detailed information about the data sources of the given telemetry mode index.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QString FeedbackConfigUiController::telemetryModeName(int *telemetryIndex*) const {#telemetryModeName}

Telemetry mode short name.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] int FeedbackConfigUiController::telemetryModeToIndex(KUserFeedback::Provider::TelemetryMode *mode*) const {#telemetryModeToIndex}

Convert telemetry mode to slider index.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QString FeedbackConfigUiController::telemetryName(KUserFeedback::Provider::TelemetryMode *mode*) const {#telemetryName}

Telemetry mode short name.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.
