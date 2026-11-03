---
title: "KUserFeedback::AbstractDataSource Class"
description: "Base class for data sources for telemetry data."
---

# KUserFeedback::AbstractDataSource Class

Base class for data sources for telemetry data. [More...](#details)

- **Header:** `#include <KUserFeedback/AbstractDataSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherited By:** [KUserFeedback::ApplicationVersionSource](kuserfeedback-applicationversionsource.md), [KUserFeedback::CompilerInfoSource](kuserfeedback-compilerinfosource.md), [KUserFeedback::CpuInfoSource](kuserfeedback-cpuinfosource.md), [KUserFeedback::LocaleInfoSource](kuserfeedback-localeinfosource.md), [KUserFeedback::OpenGLInfoSource](kuserfeedback-openglinfosource.md), [KUserFeedback::PlatformInfoSource](kuserfeedback-platforminfosource.md), [KUserFeedback::PropertyRatioSource](kuserfeedback-propertyratiosource.md), [KUserFeedback::QPAInfoSource](kuserfeedback-qpainfosource.md), [KUserFeedback::QtVersionSource](kuserfeedback-qtversionsource.md), [KUserFeedback::ScreenInfoSource](kuserfeedback-screeninfosource.md), [KUserFeedback::SelectionRatioSource](kuserfeedback-selectionratiosource.md), [KUserFeedback::StartCountSource](kuserfeedback-startcountsource.md), and [KUserFeedback::UsageTimeSource](kuserfeedback-usagetimesource.md)

[List of all members, including inherited members](kuserfeedback-abstractdatasource-members.md)

## Public Functions

- [QVariant data()](#data)
- [QString description() const](#description)
- [QString id() const](#id)
- [bool isActive() const](#isActive)
- [void load(QSettings \*settings)](#load)
- [QString name() const](#name)
- [void reset(QSettings \*settings)](#reset)
- [void setActive(bool active)](#setActive)
- [void setTelemetryMode(KUserFeedback::Provider::TelemetryMode mode)](#setTelemetryMode)
- [void store(QSettings \*settings)](#store)
- [KUserFeedback::Provider::TelemetryMode telemetryMode() const](#telemetryMode)

## Protected Functions

- [AbstractDataSource(const QString &id, KUserFeedback::Provider::TelemetryMode mode = Provider::DetailedUsageStatistics)](#AbstractDataSource)
- [AbstractDataSource(const QString &id, KUserFeedback::Provider::TelemetryMode mode, KUserFeedback::AbstractDataSourcePrivate \*dd)](#AbstractDataSource-1)
- [void loadImpl(QSettings \*settings)](#loadImpl)
- [void resetImpl(QSettings \*settings)](#resetImpl)
- [void setId(const QString &id)](#setId)
- [void storeImpl(QSettings \*settings)](#storeImpl)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] AbstractDataSource::AbstractDataSource(const QString &*id*, KUserFeedback::Provider::TelemetryMode *mode* = Provider::DetailedUsageStatistics) {#AbstractDataSource}

Create a new data source named `name`.

The name of the data source must match the corresponding product schema entry.

`id` Must not be empty.

`mode` The default telemetry mode.

### \[explicit protected\] AbstractDataSource::AbstractDataSource(const QString &*id*, KUserFeedback::Provider::TelemetryMode *mode*, KUserFeedback::AbstractDataSourcePrivate \**dd*) {#AbstractDataSource-1}

### \[pure virtual\] QVariant AbstractDataSource::data() {#data}

Returns the data gathered by this source.

Implement this to return the data provided by this source. One of the three following formats are expected:

- scalar entries: [QAssociativeIterable](https://doc.qt.io/qt-6/qassociativeiterable.html)
- list entries: [QSequentialIterable](https://doc.qt.io/qt-6/qsequentialiterable.html) containing [QAssociativeIterable](https://doc.qt.io/qt-6/qassociativeiterable.html)
- map entries: [QAssociativeIterable](https://doc.qt.io/qt-6/qassociativeiterable.html) containing [QAssociativeIterable](https://doc.qt.io/qt-6/qassociativeiterable.html)

The innermost [QAssociativeIterable](https://doc.qt.io/qt-6/qassociativeiterable.html) must only contain one of the following base types (which has to match the corresponding schema entry element):

- [QString](https://doc.qt.io/qt-6/qstring.html)
- int
- double
- bool

All keys must be strings.

Returns a variant complying with the above requirements.

### \[pure virtual\] QString AbstractDataSource::description() const {#description}

Returns a human-readable, translated description of what this source provides.

Returns a translated, human-readable string.

*See also* [id](kuserfeedback-abstractdatasource.md#id)()

### QString AbstractDataSource::id() const {#id}

Returns the ID of this data source. This is used as identifier towards the server and should not be shown to the user.

Returns the data source identifier configured on the feedback server.

*See also* [setId](kuserfeedback-abstractdatasource.md#setId)(), [description](kuserfeedback-abstractdatasource.md#description)()

### bool AbstractDataSource::isActive() const {#isActive}

Checks whether this data source is active or not

If the data source is not active, then collected data neither will be sent to a server nor appeared in the audit log.

Data source is active by default.

Returns `true` if active, false otherwise

### void AbstractDataSource::load(QSettings \**settings*) {#load}

Load persistent state for this data source.

`settings` A [QSettings](https://doc.qt.io/qt-6/qsettings.html) object opened in a dedicated group for loading persistent data.

### \[virtual protected\] void AbstractDataSource::loadImpl(QSettings \**settings*) {#loadImpl}

Invoked by [load](kuserfeedback-abstractdatasource.md#load)() in order to load individual settings of this data source.

`settings` A [QSettings](https://doc.qt.io/qt-6/qsettings.html) object opened in a dedicated group for loading persistent data.

*See also* [load](kuserfeedback-abstractdatasource.md#load)(), [description](kuserfeedback-abstractdatasource.md#description), for, further, details

### \[virtual\] QString AbstractDataSource::name() const {#name}

Returns a short name of this data source.

Can be empty if short name is meaningless for this data source.

Returns a translated, human-readable string.

### void AbstractDataSource::reset(QSettings \**settings*) {#reset}

Reset the persistent state of this data source.

This is called after a successful submission of data, and can be used by sources that track differential rather than absolute data to reset their counters.

`settings` A [QSettings](https://doc.qt.io/qt-6/qsettings.html) object opened in the dedicated group of this data source.

### \[virtual protected\] void AbstractDataSource::resetImpl(QSettings \**settings*) {#resetImpl}

Invoked by [reset](kuserfeedback-abstractdatasource.md#reset)() in order to reset individual settings of this data source.

See [reset](kuserfeedback-abstractdatasource.md#reset)() description for further details.

`settings` A [QSettings](https://doc.qt.io/qt-6/qsettings.html) object opened in a dedicated group for loading persistent data.

### void AbstractDataSource::setActive(bool *active*) {#setActive}

Changes active state of the data source

`active` The new active state for this data source

*See also* [isActive](kuserfeedback-abstractdatasource.md#isActive)()

### \[protected\] void AbstractDataSource::setId(const QString &*id*) {#setId}

Set the ID of this data source.

The ID should not change at runtime, this is only provided for enabling QML API for generic sources.

*See also* [id](kuserfeedback-abstractdatasource.md#id)()

### void AbstractDataSource::setTelemetryMode(KUserFeedback::Provider::TelemetryMode *mode*) {#setTelemetryMode}

Sets which telemetry colleciton mode this data source belongs to.

`mode` The data collection mode of this source.

[Provider::NoTelemetry](kuserfeedback-provider.md#TelemetryMode-enum) is not allowed here.

*See also* [telemetryMode](kuserfeedback-abstractdatasource.md#telemetryMode)()

### void AbstractDataSource::store(QSettings \**settings*) {#store}

Store persistent state for this data source.

`settings` A [QSettings](https://doc.qt.io/qt-6/qsettings.html) object opened in a dedicated group for storing persistent data.

### \[virtual protected\] void AbstractDataSource::storeImpl(QSettings \**settings*) {#storeImpl}

Invoked by [store](kuserfeedback-abstractdatasource.md#store)() in order to store individual settings of this data source.

`settings` A [QSettings](https://doc.qt.io/qt-6/qsettings.html) object opened in a dedicated group for loading persistent data.

*See also* [store](kuserfeedback-abstractdatasource.md#store)(), [description](kuserfeedback-abstractdatasource.md#description), for, further, details

### KUserFeedback::Provider::TelemetryMode AbstractDataSource::telemetryMode() const {#telemetryMode}

Returns which telemetry colleciton mode this data source belongs to.

*See also* [setTelemetryMode](kuserfeedback-abstractdatasource.md#setTelemetryMode)()
