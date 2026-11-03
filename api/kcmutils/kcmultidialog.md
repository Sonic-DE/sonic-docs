---
title: "KCMultiDialog Class"
description: "A class that offers a KPageDialog containing config modules."
---

# KCMultiDialog Class

A class that offers a KPageDialog containing config modules. [More...](#details)

- **Header:** `#include <KCMultiDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KCMUtils)`  
  `target_link_libraries(mytarget PRIVATE KF6::KCMUtils)`

[List of all members, including inherited members](kcmultidialog-members.md)

## Public Functions

- [KCMultiDialog(QWidget \*parent = nullptr)](#KCMultiDialog)
- [KPageWidgetItem \*addModule(const KPluginMetaData &metaData, const QVariantList &args = {})](#addModule)
- [void clear()](#clear)
- [bool hasError() const](#hasError) (since 6.27)
- [void setDefaultsIndicatorsVisible(bool show)](#setDefaultsIndicatorsVisible) (since 6.0)

## Public Slots

- [void slotApplyClicked()](#slotApplyClicked)
- [void slotDefaultClicked()](#slotDefaultClicked)
- [void slotHelpClicked()](#slotHelpClicked)
- [void slotOkClicked()](#slotOkClicked)
- [void slotUser1Clicked()](#slotUser1Clicked)

## Signals

- [void configCommitted()](#configCommitted)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCMultiDialog::KCMultiDialog(QWidget \**parent* = nullptr) {#KCMultiDialog}

Constructs a new [KCMultiDialog](kcmultidialog.md).

`parent` The parent widget.

### KPageWidgetItem \*KCMultiDialog::addModule(const KPluginMetaData &*metaData*, const QVariantList &*args* = {}) {#addModule}

Adds a module to the dialog. Its position will be determined based on the `X-KDE-Weight` value.

`metaData` [KPluginMetaData](../kcoreaddons/kpluginmetadata.md) that will be used to load the plugin.

`args` The arguments that should be given to the [KCModule](kcmodule.md) when it is created.

### void KCMultiDialog::clear() {#clear}

Removes all modules from the dialog.

### \[signal\] void KCMultiDialog::configCommitted() {#configCommitted}

Emitted after all KCModules have been told to save their configuration.

The applyClicked and okClicked signals are emitted before the configuration is saved.

### \[since 6.27\] bool KCMultiDialog::hasError() const {#hasError}

Returns whether any of the modules failed to load

This function was introduced in Qt 6.27.

### \[since 6.0\] void KCMultiDialog::setDefaultsIndicatorsVisible(bool *show*) {#setDefaultsIndicatorsVisible}

Whether to `show` or hide an indicator when settings have changed from their default value.

This function was introduced in Qt 6.0.

### \[protected slot\] void KCMultiDialog::slotApplyClicked() {#slotApplyClicked}

This slot is called when the user presses the "Apply" Button. You can reimplement it if needed.

> **Note:** Make sure you call the original implementation.

### \[protected slot\] void KCMultiDialog::slotDefaultClicked() {#slotDefaultClicked}

This slot is called when the user presses the "Default" Button.

You can reimplement it if needed.

> **Note:** Make sure you call the original implementation.

### \[protected slot\] void KCMultiDialog::slotHelpClicked() {#slotHelpClicked}

This slot is called when the user presses the "Help" Button.

It reads the X-DocPath field of the currently selected KControl module's .desktop file to find the path to the documentation, which it then attempts to load.

You can reimplement this slot if needed.

> **Note:** Make sure you call the original implementation.

### \[protected slot\] void KCMultiDialog::slotOkClicked() {#slotOkClicked}

This slot is called when the user presses the "OK" Button. You can reimplement it if needed.

> **Note:** Make sure you call the original implementation.

### \[protected slot\] void KCMultiDialog::slotUser1Clicked() {#slotUser1Clicked}

This slot is called when the user presses the "Reset" Button. You can reimplement it if needed.

> **Note:** Make sure you call the original implementation.
