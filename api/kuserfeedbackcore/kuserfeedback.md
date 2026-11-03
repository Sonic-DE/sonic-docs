---
title: "KUserFeedback Namespace"
description: "Framework for collecting feedback from application users via telemetry and targeted surveys.."
---

# KUserFeedback Namespace

Framework for collecting feedback from application users via telemetry and targeted surveys.. [More...](#details)

- Header: KUserFeedback
- CMake: find\_package(KF6 REQUIRED COMPONENTS UserFeedbackCore) target\_link\_libraries(mytarget PRIVATE KF6::UserFeedbackCore)

## Detailed Description {#details}

## Classes {#classes}

### class [AbstractDataSource](kuserfeedback-abstractdatasource.md)

Base class for data sources for telemetry data.

### class [ApplicationVersionSource](kuserfeedback-applicationversionsource.md)

Data source for the application version.

### class [AuditLogUiController](kuserfeedback-auditloguicontroller.md)

Widget/QtQuick-independent logic and data for the audit log browser UI.

### class [CompilerInfoSource](kuserfeedback-compilerinfosource.md)

Data source reporting which compiler was used to build this code.

### class [CpuInfoSource](kuserfeedback-cpuinfosource.md)

Data source reporting the type and amount of CPUs.

### class [FeedbackConfigUiController](kuserfeedback-feedbackconfiguicontroller.md)

Logic/behavior of the feedback configuration UI.

### class [LocaleInfoSource](kuserfeedback-localeinfosource.md)

Data source reporting the region and language settings.

### class [OpenGLInfoSource](kuserfeedback-openglinfosource.md)

Data source reporting type, version and vendor of the OpenGL stack.

### class [PlatformInfoSource](kuserfeedback-platforminfosource.md)

Reports information about the platform the application is running on.

### class [PropertyRatioSource](kuserfeedback-propertyratiosource.md)

Records the time ratio a given [QObject](https://doc.qt.io/qt-6/qobject.html) property has a specific value.

### class [Provider](kuserfeedback-provider.md)

The central object managing data sources and transmitting feedback to the server.

### class [QPAInfoSource](kuserfeedback-qpainfosource.md)

Reports information about the Qt platform abstraction plugin the application is running on.

### class [QtVersionSource](kuserfeedback-qtversionsource.md)

Data source reporting the Qt version used at runtime.

### class [ScreenInfoSource](kuserfeedback-screeninfosource.md)

Data source for information about connected displays.

### class [SelectionRatioSource](kuserfeedback-selectionratiosource.md)

Records the time ratio a given entry is selected via a [QItemSelectionModel](https://doc.qt.io/qt-6/qitemselectionmodel.html).

### class [StartCountSource](kuserfeedback-startcountsource.md)

Data source reporting the total amount of applications starts.

### class [SurveyInfo](kuserfeedback-surveyinfo.md)

Information about a survey request.

### class [UsageTimeSource](kuserfeedback-usagetimesource.md)

Data source reporting the total usage time of the application.
