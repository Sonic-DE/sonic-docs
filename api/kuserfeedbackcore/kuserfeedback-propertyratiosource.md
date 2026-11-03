---
title: "KUserFeedback::PropertyRatioSource Class"
description: "Records the time ratio a given QObject property has a specific value."
---

# KUserFeedback::PropertyRatioSource Class

Records the time ratio a given [QObject](https://doc.qt.io/qt-6/qobject.html) property has a specific value. [More...](#details)

- **Header:** `#include <KUserFeedback/PropertyRatioSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackCore)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackCore)`
- **Inherits:** [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md)

[List of all members, including inherited members](kuserfeedback-propertyratiosource-members.md)

## Public Functions

- [PropertyRatioSource(QObject \*obj, const char \*propertyName, const QString &sampleName)](#PropertyRatioSource)
- [void addValueMapping(const QVariant &value, const QString &str)](#addValueMapping)
- [QObject \*object() const](#object)
- [QString propertyName() const](#propertyName)
- [void setDescription(const QString &desc)](#setDescription)
- [void setName(const QString &name)](#setName)
- [void setObject(QObject \*object)](#setObject)
- [void setPropertyName(const QString &name)](#setPropertyName)

## Detailed Description {#details}

An example use-case would be the usage ratio of a applications views/modes selected by a QTabWidget or QRadioButton.

The default telemetry mode for this source is [Provider::DetailedUsageStatistics](kuserfeedback-provider.md#TelemetryMode-enum).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] PropertyRatioSource::PropertyRatioSource(QObject \**obj*, const char \**propertyName*, const QString &*sampleName*) {#PropertyRatioSource}

Create a new property ratio data source.

`obj` the [QObject](https://doc.qt.io/qt-6/qobject.html) of which a property should be monitored.

`propertyName` The name of the property to monitor. This property must have a change notification signal. The value must have comparison operators registered.

`sampleName` This is the name of the database field this data source is associated with.

### void PropertyRatioSource::addValueMapping(const QVariant &*value*, const QString &*str*) {#addValueMapping}

Map property value `value` to `str` for sending to the server.

This is useful to map internal identifiers to portable and persistable values, such as turning pointers or indexes into meaningful descriptions.

`value` The property value to map.

`str` The string the property value `value` should be mapped to.

### QObject \*PropertyRatioSource::object() const {#object}

Returns the monitored object.

*See also* [setObject](kuserfeedback-propertyratiosource.md#setObject)()

### QString PropertyRatioSource::propertyName() const {#propertyName}

Returns the property name.

*See also* [setPropertyName](kuserfeedback-propertyratiosource.md#setPropertyName)()

### void PropertyRatioSource::setDescription(const QString &*desc*) {#setDescription}

Set human-readable and translated description of the data provided by this source.

> **Note:** This must be set before adding this source, sources without description are discarded.

`desc` The description.

### void PropertyRatioSource::setName(const QString &*name*) {#setName}

Set human readable name.

*See also* [AbstractDataSource::name](kuserfeedback-abstractdatasource.md#name)()

### void PropertyRatioSource::setObject(QObject \**object*) {#setObject}

Sets the monitoried object.

*See also* [object](kuserfeedback-propertyratiosource.md#object)()

### void PropertyRatioSource::setPropertyName(const QString &*name*) {#setPropertyName}

Sets the property name that should be monitored.

*See also* [propertyName](kuserfeedback-propertyratiosource.md#propertyName)()
