---
title: "Purpose::Menu Class"
description: "A menu showing different alternatives."
---

# Purpose::Menu Class

A menu showing different alternatives. [More...](#details)

- **Header:** `#include <Purpose/Menu>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Purpose)`  
  `target_link_libraries(mytarget PRIVATE KF6::PurposeWidgets)`
- **Inherits:** [QMenu](https://doc.qt.io/qt-6/qmenu.html)

[List of all members, including inherited members](purpose-menu-members.md)

## Public Functions

- [Menu(QWidget \*parent = nullptr)](#Menu)
- [Purpose::AlternativesModel \*model() const](#model)
- [void reload()](#reload)

## Signals

- [void aboutToShare()](#aboutToShare) (since 6.2)
- [void finished(const QJsonObject &output, int error, const QString &errorMessage)](#finished)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Menu::Menu(QWidget \**parent* = nullptr) {#Menu}

### \[signal, since 6.2\] void Menu::aboutToShare() {#aboutToShare}

Emitted just before triggered, just before starting the share operation.

Can be used to do adjustments to the configuration, such as setting a new Url.

This function was introduced in Qt 6.2.

### \[signal\] void Menu::finished(const QJsonObject &*output*, int *error*, const QString &*errorMessage*) {#finished}

Emitted when a triggered job finishes

`output` contains the information offered by the plugin. The information offered will depend on the plugin type.

`error` will be 0 if the execution was successful, KIO::ERR\_USER\_CANCELED if cancelled by the user, otherwise it will provide an error message

`errorMessage` the error message

*See also* [Purpose::Job](../purpose/purpose-job.md)

### Purpose::AlternativesModel \*Menu::model() const {#model}

Exposes the used AlternativesModel so that it can be configured to suit the application needs

### void Menu::reload() {#reload}

Forces a reload of the menu in case something changed in the model
