---
title: "KUserFeedback::Provider Class"
description: "The central object managing data sources and transmitting feedback to the server."
---

# KUserFeedback::Provider Class

The central object managing data sources and transmitting feedback to the server. [More...](#details)

- **Header:** `#include <KUserFeedback/Provider>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kuserfeedback-provider-members.md)

## Public Types

- [enum Provider::TelemetryMode](#TelemetryMode-enum)

## Properties

- [applicationStartsUntilEncouragement : int](#applicationStartsUntilEncouragement-prop)
- [applicationUsageTimeUntilEncouragement : int](#applicationUsageTimeUntilEncouragement-prop)
- [\[read-only\] describeDataSources : QString](#describeDataSources-prop)
- [enabled : bool](#enabled-prop)
- [encouragementDelay : int](#encouragementDelay-prop)
- [encouragementInterval : int](#encouragementInterval-prop)
- [feedbackServer : QUrl](#feedbackServer-prop)
- [productIdentifier : QString](#productIdentifier-prop)
- [submissionInterval : int](#submissionInterval-prop)
- [surveyInterval : int](#surveyInterval-prop)
- [telemetryMode : TelemetryMode](#telemetryMode-prop)

## Public Functions

- [Provider(QObject \*parent = nullptr)](#Provider)
- [void addDataSource(KUserFeedback::AbstractDataSource \*source)](#addDataSource)
- [int applicationStartsUntilEncouragement() const](#applicationStartsUntilEncouragement)
- [int applicationUsageTimeUntilEncouragement() const](#applicationUsageTimeUntilEncouragement)
- [KUserFeedback::AbstractDataSource \*dataSource(const QString &id) const](#dataSource)
- [QVector\<KUserFeedback::AbstractDataSource \*\> dataSources() const](#dataSources)
- [QString describeDataSources() const](#describeDataSources)
- [int encouragementDelay() const](#encouragementDelay)
- [int encouragementInterval() const](#encouragementInterval)
- [QUrl feedbackServer() const](#feedbackServer)
- [bool isEnabled() const](#isEnabled)
- [QString productIdentifier() const](#productIdentifier)
- [void restoreDefaults()](#restoreDefaults)
- [void setApplicationStartsUntilEncouragement(int starts)](#setApplicationStartsUntilEncouragement)
- [void setApplicationUsageTimeUntilEncouragement(int secs)](#setApplicationUsageTimeUntilEncouragement)
- [void setEnabled(bool enabled)](#setEnabled)
- [void setEncouragementDelay(int secs)](#setEncouragementDelay)
- [void setEncouragementInterval(int days)](#setEncouragementInterval)
- [void setFeedbackServer(const QUrl &url)](#setFeedbackServer)
- [void setProductIdentifier(const QString &productId)](#setProductIdentifier)
- [void setSubmissionInterval(int days)](#setSubmissionInterval)
- [void setSurveyInterval(int days)](#setSurveyInterval)
- [void setTelemetryMode(KUserFeedback::Provider::TelemetryMode mode)](#setTelemetryMode)
- [int submissionInterval() const](#submissionInterval)
- [int surveyInterval() const](#surveyInterval)
- [KUserFeedback::Provider::TelemetryMode telemetryMode() const](#telemetryMode)

## Public Slots

- [void load()](#load)
- [void store()](#store)
- [void submit()](#submit)
- [void surveyCompleted(const KUserFeedback::SurveyInfo &info)](#surveyCompleted)

## Signals

- [void dataSourcesChanged()](#dataSourcesChanged)
- [void enabledChanged()](#enabledChanged)
- [void providerSettingsChanged()](#providerSettingsChanged)
- [void showEncouragementMessage()](#showEncouragementMessage)
- [void surveyAvailable(const KUserFeedback::SurveyInfo &survey)](#surveyAvailable)
- [void surveyIntervalChanged()](#surveyIntervalChanged)
- [void telemetryModeChanged()](#telemetryModeChanged)

## Detailed Description {#details}

The defaults for this class are very defensive, so in order to make it actually operational and submit data, there is a number of settings you need to set in code, namely submission intervals, encouragement settings and adding data sources.

The settings about what data to submit ([telemetryMode](kuserfeedback-provider.md#telemetryMode)) and how often to bother the user with surveys ([surveyInterval](kuserfeedback-provider.md#surveyInterval)) should not be set to hardcoded values in code, but left as choices to the user.

## Member Type Documentation {#member-type-documentation}

### enum Provider::TelemetryMode {#TelemetryMode-enum}

Telemetry collection modes.

Collection modes are inclusive, ie. higher modes always imply data from lower modes too.

| Constant | Value | Description |
| --- | --- | --- |
| `KUserFeedback::Provider::NoTelemetry` | `0` | Transmit no data at all. |
| `KUserFeedback::Provider::BasicSystemInformation` | `0x10` | Transmit basic information about the\* system. |
| `KUserFeedback::Provider::BasicUsageStatistics` | `0x20` | Transmit basic usage statistics. |
| `KUserFeedback::Provider::DetailedSystemInformation` | `0x30` | Transmit detailed system information. |
| `KUserFeedback::Provider::DetailedUsageStatistics` | `0x40` | Transmit detailed usage statistics. |

## Property Documentation {#property-documentation}

### applicationStartsUntilEncouragement : int {#applicationStartsUntilEncouragement-prop}

Times the application has to be started before an encouragement message is shown.

**Access functions:**

- `int` **[applicationStartsUntilEncouragement](kuserfeedback-provider.md#applicationStartsUntilEncouragement)**() const
- `void` **[setApplicationStartsUntilEncouragement](kuserfeedback-provider.md#setApplicationStartsUntilEncouragement)**(`int` *starts*)

**Notifier signal:**

- `void` **[providerSettingsChanged](kuserfeedback-provider.md#providerSettingsChanged)**()

*See also* [setApplicationStartsUntilEncouragement](kuserfeedback-provider.md#setApplicationStartsUntilEncouragement)

### applicationUsageTimeUntilEncouragement : int {#applicationUsageTimeUntilEncouragement-prop}

Application usage time in seconds before an encouragement message is shown.

**Access functions:**

- `int` **[applicationUsageTimeUntilEncouragement](kuserfeedback-provider.md#applicationUsageTimeUntilEncouragement)**() const
- `void` **[setApplicationUsageTimeUntilEncouragement](kuserfeedback-provider.md#setApplicationUsageTimeUntilEncouragement)**(`int` *secs*)

**Notifier signal:**

- `void` **[providerSettingsChanged](kuserfeedback-provider.md#providerSettingsChanged)**()

*See also* [setApplicationUsageTimeUntilEncouragement](kuserfeedback-provider.md#setApplicationUsageTimeUntilEncouragement)

### \[read-only\] describeDataSources : QString {#describeDataSources-prop}

**Access functions:**

- `QString` **[describeDataSources](kuserfeedback-provider.md#describeDataSources)**() const

**Notifier signal:**

- `void` **[dataSourcesChanged](kuserfeedback-provider.md#dataSourcesChanged)**()

### enabled : bool {#enabled-prop}

The global enabled state of the feedback functionality.

If this is `false`, all feedback functionality has to be disabled completely.

**Access functions:**

- `bool` **[isEnabled](kuserfeedback-provider.md#isEnabled)**() const
- `void` **[setEnabled](kuserfeedback-provider.md#setEnabled)**(`bool` *enabled*)

**Notifier signal:**

- `void` **[enabledChanged](kuserfeedback-provider.md#enabledChanged)**()

### encouragementDelay : int {#encouragementDelay-prop}

Encouragement delay after application start in seconds.

**Access functions:**

- `int` **[encouragementDelay](kuserfeedback-provider.md#encouragementDelay)**() const
- `void` **[setEncouragementDelay](kuserfeedback-provider.md#setEncouragementDelay)**(`int` *secs*)

**Notifier signal:**

- `void` **[providerSettingsChanged](kuserfeedback-provider.md#providerSettingsChanged)**()

*See also* [setEncouragementDelay](kuserfeedback-provider.md#setEncouragementDelay)

### encouragementInterval : int {#encouragementInterval-prop}

Encouragement interval.

**Access functions:**

- `int` **[encouragementInterval](kuserfeedback-provider.md#encouragementInterval)**() const
- `void` **[setEncouragementInterval](kuserfeedback-provider.md#setEncouragementInterval)**(`int` *days*)

**Notifier signal:**

- `void` **[providerSettingsChanged](kuserfeedback-provider.md#providerSettingsChanged)**()

*See also* [setEncouragementInterval](kuserfeedback-provider.md#setEncouragementInterval)

### feedbackServer : QUrl {#feedbackServer-prop}

URL of the feedback server.

**Access functions:**

- `QUrl` **[feedbackServer](kuserfeedback-provider.md#feedbackServer)**() const
- `void` **[setFeedbackServer](kuserfeedback-provider.md#setFeedbackServer)**(const `QUrl` &*url*)

**Notifier signal:**

- `void` **[providerSettingsChanged](kuserfeedback-provider.md#providerSettingsChanged)**()

*See also* [setFeedbackServer](kuserfeedback-provider.md#setFeedbackServer)

### productIdentifier : QString {#productIdentifier-prop}

Unique product id as set on the feedback server.

**Access functions:**

- `QString` **[productIdentifier](kuserfeedback-provider.md#productIdentifier)**() const
- `void` **[setProductIdentifier](kuserfeedback-provider.md#setProductIdentifier)**(const `QString` &*productId*)

**Notifier signal:**

- `void` **[providerSettingsChanged](kuserfeedback-provider.md#providerSettingsChanged)**()

*See also* [setProductIdentifier](kuserfeedback-provider.md#setProductIdentifier)

### submissionInterval : int {#submissionInterval-prop}

Submission interval in days.

**Access functions:**

- `int` **[submissionInterval](kuserfeedback-provider.md#submissionInterval)**() const
- `void` **[setSubmissionInterval](kuserfeedback-provider.md#setSubmissionInterval)**(`int` *days*)

**Notifier signal:**

- `void` **[providerSettingsChanged](kuserfeedback-provider.md#providerSettingsChanged)**()

*See also* [setSubmissionInterval](kuserfeedback-provider.md#setSubmissionInterval)

### surveyInterval : int {#surveyInterval-prop}

The interval in which the user accepts surveys.

This should be configurable for the user.

`-1` indicates surveys are disabled.

**Access functions:**

- `int` **[surveyInterval](kuserfeedback-provider.md#surveyInterval)**() const
- `void` **[setSurveyInterval](kuserfeedback-provider.md#setSurveyInterval)**(`int` *days*)

**Notifier signal:**

- `void` **[surveyIntervalChanged](kuserfeedback-provider.md#surveyIntervalChanged)**()

*See also* [surveyInterval](kuserfeedback-provider.md#surveyInterval)(), [setSurveyInterval](kuserfeedback-provider.md#setSurveyInterval)()

### telemetryMode : TelemetryMode {#telemetryMode-prop}

The telemetry mode the user has configured.

This should be configurable for the user.

**Access functions:**

- `KUserFeedback::Provider::TelemetryMode` **[telemetryMode](kuserfeedback-provider.md#telemetryMode)**() const
- `void` **[setTelemetryMode](kuserfeedback-provider.md#setTelemetryMode)**(`KUserFeedback::Provider::TelemetryMode` *mode*)

**Notifier signal:**

- `void` **[telemetryModeChanged](kuserfeedback-provider.md#telemetryModeChanged)**()

*See also* [telemetryMode](kuserfeedback-provider.md#telemetryMode)(), [setTelemetryMode](kuserfeedback-provider.md#setTelemetryMode)()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Provider::Provider(QObject \**parent* = nullptr) {#Provider}

Create a new feedback provider.

`parent` The parent object.

### void Provider::addDataSource(KUserFeedback::AbstractDataSource \**source*) {#addDataSource}

Adds a data source for telemetry data collection.

`source` The data source to add. The Provider takes ownership of `source`.

### int Provider::applicationStartsUntilEncouragement() const {#applicationStartsUntilEncouragement}

Returns the amount of application starts before an encouragement message is shown.

> **Note:** Getter function for property [applicationStartsUntilEncouragement](kuserfeedback-provider.md#applicationStartsUntilEncouragement-prop).

*See also* [setApplicationStartsUntilEncouragement](kuserfeedback-provider.md#setApplicationStartsUntilEncouragement)()

### int Provider::applicationUsageTimeUntilEncouragement() const {#applicationUsageTimeUntilEncouragement}

Returns the amount of application usage time before an encouragement message is shown.

> **Note:** Getter function for property [applicationUsageTimeUntilEncouragement](kuserfeedback-provider.md#applicationUsageTimeUntilEncouragement-prop).

*See also* [setApplicationUsageTimeUntilEncouragement](kuserfeedback-provider.md#setApplicationUsageTimeUntilEncouragement)()

### KUserFeedback::AbstractDataSource \*Provider::dataSource(const QString &*id*) const {#dataSource}

Returns a data source with matched `id`

`id` data source unique identifier

Returns pointer to found data source or nullptr if data source is not found

### QVector\<KUserFeedback::AbstractDataSource \*\> Provider::dataSources() const {#dataSources}

Returns all data sources that have been added to this provider.

*See also* [addDataSource](kuserfeedback-provider.md#addDataSource)

### \[signal\] void Provider::dataSourcesChanged() {#dataSourcesChanged}

Emitted when a data source is added or removed.

> **Note:** Notifier signal for property [describeDataSources](kuserfeedback-provider.md#describeDataSources-prop).

### QString Provider::describeDataSources() const {#describeDataSources}

Returns a string with each source and its enable mode.

> **Note:** Getter function for property [describeDataSources](kuserfeedback-provider.md#describeDataSources-prop).

### \[signal\] void Provider::enabledChanged() {#enabledChanged}

Emitted when the global enabled state changed.

> **Note:** Notifier signal for property [enabled](kuserfeedback-provider.md#enabled-prop).

### int Provider::encouragementDelay() const {#encouragementDelay}

Returns the current encouragement delay in seconds.

> **Note:** Getter function for property [encouragementDelay](kuserfeedback-provider.md#encouragementDelay-prop).

*See also* [setEncouragementDelay](kuserfeedback-provider.md#setEncouragementDelay)()

### int Provider::encouragementInterval() const {#encouragementInterval}

Returns the current encouragement interval.

> **Note:** Getter function for property [encouragementInterval](kuserfeedback-provider.md#encouragementInterval-prop).

*See also* [setEncouragementInterval](kuserfeedback-provider.md#setEncouragementInterval)()

### QUrl Provider::feedbackServer() const {#feedbackServer}

Returns the current feedback server URL.

> **Note:** Getter function for property [feedbackServer](kuserfeedback-provider.md#feedbackServer-prop).

*See also* [setFeedbackServer](kuserfeedback-provider.md#setFeedbackServer)()

### bool Provider::isEnabled() const {#isEnabled}

Returns whether feedback functionality is enabled on this system.

This should be checked everywhere showing feedback UI to the user to respect the global "kill switch" for this. Provider does check this internally for encouragements, surveys and telemetry submission.

> **Note:** Getter function for property [enabled](kuserfeedback-provider.md#enabled-prop).

### \[slot\] void Provider::load() {#load}

Manually load settings of the provider and all added data sources.

Automatically invoked after object construction and changing product ID.

> **Note:** Potentially long operation.

### QString Provider::productIdentifier() const {#productIdentifier}

Returns the current product identifier.

> **Note:** Getter function for property [productIdentifier](kuserfeedback-provider.md#productIdentifier-prop).

*See also* [setProductIdentifier](kuserfeedback-provider.md#setProductIdentifier)()

### \[signal\] void Provider::providerSettingsChanged() {#providerSettingsChanged}

Emitted when any provider setting changed.

> **Note:** Notifier signal for properties [applicationStartsUntilEncouragement](kuserfeedback-provider.md#applicationStartsUntilEncouragement-prop), [applicationUsageTimeUntilEncouragement](kuserfeedback-provider.md#applicationUsageTimeUntilEncouragement-prop), [encouragementDelay](kuserfeedback-provider.md#encouragementDelay-prop), [encouragementInterval](kuserfeedback-provider.md#encouragementInterval-prop), [feedbackServer](kuserfeedback-provider.md#feedbackServer-prop), [productIdentifier](kuserfeedback-provider.md#productIdentifier-prop), and [submissionInterval](kuserfeedback-provider.md#submissionInterval-prop).

### void Provider::restoreDefaults() {#restoreDefaults}

Set the telemetry mode and the survey interval back to their default values.

*See also* [telemetryMode](kuserfeedback-provider.md#telemetryMode)(), [surveyInterval](kuserfeedback-provider.md#surveyInterval)()

### void Provider::setApplicationStartsUntilEncouragement(int *starts*) {#setApplicationStartsUntilEncouragement}

Set the amount of application starts until the encouragement message should be shown.

The default is -1, ie. no encouragement based on application starts.

`starts` The amount of application starts after which an encouragement message should be displayed.

> **Note:** Setter function for property [applicationStartsUntilEncouragement](kuserfeedback-provider.md#applicationStartsUntilEncouragement-prop).

*See also* [applicationStartsUntilEncouragement](kuserfeedback-provider.md#applicationStartsUntilEncouragement)()

### void Provider::setApplicationUsageTimeUntilEncouragement(int *secs*) {#setApplicationUsageTimeUntilEncouragement}

Set the amount of usage time until the encouragement message should be shown.

The default is -1, ie. no encouragement based on application usage time.

`secs` Amount of seconds until the encouragement should be shown.

> **Note:** Setter function for property [applicationUsageTimeUntilEncouragement](kuserfeedback-provider.md#applicationUsageTimeUntilEncouragement-prop).

*See also* [applicationUsageTimeUntilEncouragement](kuserfeedback-provider.md#applicationUsageTimeUntilEncouragement)()

### void Provider::setEnabled(bool *enabled*) {#setEnabled}

Set the global (user-wide) activation state for feedback functionality.

> **Note:** Setter function for property [enabled](kuserfeedback-provider.md#enabled-prop).

*See also* [isEnabled](kuserfeedback-provider.md#isEnabled)

### void Provider::setEncouragementDelay(int *secs*) {#setEncouragementDelay}

Set the delay after application start for the earliest display of the encouragement message.

The default is 300, ie. 5 minutes after the application start.

> **Note:** This only adds an additional constraint on usage time and startup count based encouragement messages, it does not actually trigger encouragement messages itself.

`secs` Amount of seconds after the application start for the earliest display of an encouragement message.

> **Note:** Setter function for property [encouragementDelay](kuserfeedback-provider.md#encouragementDelay-prop).

*See also* [encouragementDelay](kuserfeedback-provider.md#encouragementDelay)(), [setApplicationStartsUntilEncouragement](kuserfeedback-provider.md#setApplicationStartsUntilEncouragement), [setApplicationUsageTimeUntilEncouragement](kuserfeedback-provider.md#setApplicationUsageTimeUntilEncouragement)

### void Provider::setEncouragementInterval(int *days*) {#setEncouragementInterval}

Sets the interval after the encouragement should be repeated.

Encouragement messages are only repeated if no feedback options have been enabled.

The default is -1, that is no repeated encouragement at all.

`days` Days between encouragement messages, 0 disables repeated encouragements.

> **Note:** Setter function for property [encouragementInterval](kuserfeedback-provider.md#encouragementInterval-prop).

*See also* [encouragementInterval](kuserfeedback-provider.md#encouragementInterval)()

### void Provider::setFeedbackServer(const QUrl &*url*) {#setFeedbackServer}

Set the feedback server URL.

This must be called with an appropriate URL for this class to be operational.

`url` The URL of the feedback server.

> **Note:** Setter function for property [feedbackServer](kuserfeedback-provider.md#feedbackServer-prop).

*See also* [feedbackServer](kuserfeedback-provider.md#feedbackServer)()

### void Provider::setProductIdentifier(const QString &*productId*) {#setProductIdentifier}

Set the product identifier.

This is used to distinguish independent products on the same server.

If this is not specified, the product identifier is derived from the application name organisation domain specified in [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html).

`productId` Unique product identifier, as configured on the feedback server.

> **Note:** Setter function for property [productIdentifier](kuserfeedback-provider.md#productIdentifier-prop).

*See also* [productIdentifier](kuserfeedback-provider.md#productIdentifier)()

### void Provider::setSubmissionInterval(int *days*) {#setSubmissionInterval}

Set the automatic submission interval in days.

This must be called with a positive number for this class to be operational, as the default is -1 (no submission ever).

> **Note:** Setter function for property [submissionInterval](kuserfeedback-provider.md#submissionInterval-prop).

*See also* [submissionInterval](kuserfeedback-provider.md#submissionInterval)()

### void Provider::setSurveyInterval(int *days*) {#setSurveyInterval}

Sets the minimum time in days between two surveys.

`-1` indicates no surveys should be requested.

`0` indicates no minimum time between surveys at all (i.e. bother the user as often as you want).

> **Note:** Setter function for property [surveyInterval](kuserfeedback-provider.md#surveyInterval-prop).

*See also* [surveyInterval](kuserfeedback-provider.md#surveyInterval)()

### void Provider::setTelemetryMode(KUserFeedback::Provider::TelemetryMode *mode*) {#setTelemetryMode}

Set which telemetry data should be submitted.

> **Note:** Setter function for property [telemetryMode](kuserfeedback-provider.md#telemetryMode-prop).

*See also* [telemetryMode](kuserfeedback-provider.md#telemetryMode)()

### \[signal\] void Provider::showEncouragementMessage() {#showEncouragementMessage}

Indicate that the encouragement notice should be shown.

### \[slot\] void Provider::store() {#store}

Manually store settings of the provider and all added data sources.

Will be automatically invoked upon [QCoreApplication::aboutToQuit](https://doc.qt.io/qt-6/qcoreapplication.html#aboutToQuit)() signal.

> **Note:** Potentially long operation.

### int Provider::submissionInterval() const {#submissionInterval}

Returns the current submission interval.

Returns days between telemetry submissions, or -1 if submission is off.

> **Note:** Getter function for property [submissionInterval](kuserfeedback-provider.md#submissionInterval-prop).

*See also* [setSubmissionInterval](kuserfeedback-provider.md#setSubmissionInterval)()

### \[slot\] void Provider::submit() {#submit}

Manually submit currently recorded data.

### \[signal\] void Provider::surveyAvailable(const KUserFeedback::SurveyInfo &*survey*) {#surveyAvailable}

Emitted whenever there is a new survey available that can be presented to the user.

### \[slot\] void Provider::surveyCompleted(const KUserFeedback::SurveyInfo &*info*) {#surveyCompleted}

Marks the given survey as completed. This avoids getting further notification about the same survey.

### int Provider::surveyInterval() const {#surveyInterval}

Returns the minimum time between two surveys in days.

The default is -1 (no surveys enabled).

> **Note:** Getter function for property [surveyInterval](kuserfeedback-provider.md#surveyInterval-prop).

*See also* [setSurveyInterval](kuserfeedback-provider.md#setSurveyInterval)()

### \[signal\] void Provider::surveyIntervalChanged() {#surveyIntervalChanged}

Emitted when the survey interval changed.

> **Note:** Notifier signal for property [surveyInterval](kuserfeedback-provider.md#surveyInterval-prop).

### KUserFeedback::Provider::TelemetryMode Provider::telemetryMode() const {#telemetryMode}

Returns the current telemetry collection mode.

The default is [NoTelemetry](kuserfeedback-provider.md#TelemetryMode-enum).

> **Note:** Getter function for property [telemetryMode](kuserfeedback-provider.md#telemetryMode-prop).

*See also* [setTelemetryMode](kuserfeedback-provider.md#setTelemetryMode)()

### \[signal\] void Provider::telemetryModeChanged() {#telemetryModeChanged}

Emitted when the telemetry collection mode has changed.

> **Note:** Notifier signal for property [telemetryMode](kuserfeedback-provider.md#telemetryMode-prop).
