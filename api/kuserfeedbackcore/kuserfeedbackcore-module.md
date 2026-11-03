---
title: "KUserFeedbackCore C++ Classes"
description: "Framework for collecting feedback from application users via telemetry and targeted surveys."
---

# KUserFeedbackCore C++ Classes

Framework for collecting feedback from application users via telemetry and targeted surveys. [More...](#details)

## Namespaces {#namespaces}

- [KUserFeedback](kuserfeedback.md)

## Classes {#classes}

- [KUserFeedback::AbstractDataSource](kuserfeedback-abstractdatasource.md): Base class for data sources for telemetry data.
- [KUserFeedback::ApplicationVersionSource](kuserfeedback-applicationversionsource.md): Data source for the application version.
- [KUserFeedback::AuditLogUiController](kuserfeedback-auditloguicontroller.md): Widget/QtQuick-independent logic and data for the audit log browser UI.
- [KUserFeedback::CompilerInfoSource](kuserfeedback-compilerinfosource.md): Data source reporting which compiler was used to build this code.
- [KUserFeedback::CpuInfoSource](kuserfeedback-cpuinfosource.md): Data source reporting the type and amount of CPUs.
- [KUserFeedback::FeedbackConfigUiController](kuserfeedback-feedbackconfiguicontroller.md): Logic/behavior of the feedback configuration UI.
- [KUserFeedback::LocaleInfoSource](kuserfeedback-localeinfosource.md): Data source reporting the region and language settings.
- [KUserFeedback::OpenGLInfoSource](kuserfeedback-openglinfosource.md): Data source reporting type, version and vendor of the OpenGL stack.
- [KUserFeedback::PlatformInfoSource](kuserfeedback-platforminfosource.md): Reports information about the platform the application is running on.
- [KUserFeedback::PropertyRatioSource](kuserfeedback-propertyratiosource.md): Records the time ratio a given QObject property has a specific value.
- [KUserFeedback::Provider](kuserfeedback-provider.md): The central object managing data sources and transmitting feedback to the server.
- [KUserFeedback::QPAInfoSource](kuserfeedback-qpainfosource.md): Reports information about the Qt platform abstraction plugin the application is running on.
- [KUserFeedback::QtVersionSource](kuserfeedback-qtversionsource.md): Data source reporting the Qt version used at runtime.
- [KUserFeedback::ScreenInfoSource](kuserfeedback-screeninfosource.md): Data source for information about connected displays.
- [KUserFeedback::SelectionRatioSource](kuserfeedback-selectionratiosource.md): Records the time ratio a given entry is selected via a QItemSelectionModel.
- [KUserFeedback::StartCountSource](kuserfeedback-startcountsource.md): Data source reporting the total amount of applications starts.
- [KUserFeedback::SurveyInfo](kuserfeedback-surveyinfo.md): Information about a survey request.
- [KUserFeedback::UsageTimeSource](kuserfeedback-usagetimesource.md): Data source reporting the total usage time of the application.

## Detailed Description {#details}
