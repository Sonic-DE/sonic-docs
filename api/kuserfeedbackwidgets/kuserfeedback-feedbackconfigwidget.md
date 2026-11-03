---
title: "KUserFeedback::FeedbackConfigWidget Class"
description: "Configuration widget for telemetry and survey contributions."
---

# KUserFeedback::FeedbackConfigWidget Class

Configuration widget for telemetry and survey contributions. [More...](#details)

- **Header:** `#include <KUserFeedback/FeedbackConfigWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackWidgets)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kuserfeedback-feedbackconfigwidget-members.md)

## Public Functions

- [FeedbackConfigWidget(QWidget \*parent = nullptr)](#FeedbackConfigWidget)
- [KUserFeedback::Provider \*feedbackProvider() const](#feedbackProvider)
- [void setFeedbackProvider(KUserFeedback::Provider \*provider)](#setFeedbackProvider)
- [int surveyInterval() const](#surveyInterval)
- [KUserFeedback::Provider::TelemetryMode telemetryMode() const](#telemetryMode)

## Signals

- [void configurationChanged()](#configurationChanged)

## Detailed Description {#details}

Use this rather than [FeedbackConfigDialog](kuserfeedback-feedbackconfigdialog.md) if you want to embed the feedback configuration for example into an existing configuration dialog.

*See also* [FeedbackConfigDialog](kuserfeedback-feedbackconfigdialog.md)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] FeedbackConfigWidget::FeedbackConfigWidget(QWidget \**parent* = nullptr) {#FeedbackConfigWidget}

Create a new feedback provider configuration widget.

`parent` The parent widget.

### \[signal\] void FeedbackConfigWidget::configurationChanged() {#configurationChanged}

Emitted when any changes are made to the configuration represented in this widget.

### KUserFeedback::Provider \*FeedbackConfigWidget::feedbackProvider() const {#feedbackProvider}

Returns the feedback provider configured by this widget.

*See also* [setFeedbackProvider](kuserfeedback-feedbackconfigwidget.md#setFeedbackProvider)()

### void FeedbackConfigWidget::setFeedbackProvider(KUserFeedback::Provider \**provider*) {#setFeedbackProvider}

Set the feedback provider that should be configured with this widget.

*See also* [feedbackProvider](kuserfeedback-feedbackconfigwidget.md#feedbackProvider)()

### int FeedbackConfigWidget::surveyInterval() const {#surveyInterval}

Returns the survey interval currently selected in this widget.

### KUserFeedback::Provider::TelemetryMode FeedbackConfigWidget::telemetryMode() const {#telemetryMode}

Returns the telemetry level currently selected in the widget.
