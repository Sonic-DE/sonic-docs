---
title: "FormCard QML Type"
description: "A single card that follows a form style."
---

# FormCard QML Type

A single card that follows a form style. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md)

## Detailed Description {#details}

This is the entrypoint component for [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md).

A [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md) consists of a container that can be used to create your own Settings pages. It has a different color than the background.

Each [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md) can contain one or more Form delegates in its contentItem. To add more than one Form delegate to a [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md), use a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html) to group them.

Multiple FormCards can be grouped with a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html) to represent different Settings sections.

Each section is expected to contain a [FormHeader](qml-org-kde-kirigamiaddons-formcard-templates-formheader.md) as the first delegate, which serves the role of a section title.

The height of the [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md) matches the implicit height of the contentItem and does not need to be set, while the width is expected to be given by the parent, for example, via a [Layout.fillWidth](https://doc.qt.io/qt-6/qml-qtquick-layouts-layout.html#fillWidth-attached-prop).
