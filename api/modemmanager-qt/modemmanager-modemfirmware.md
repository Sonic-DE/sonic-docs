---
title: "ModemManager::ModemFirmware Class"
description: "The ModemFirmware class."
---

# ModemManager::ModemFirmware Class

The [ModemFirmware](modemmanager-modemfirmware.md) class. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemFirmware>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modemfirmware-members.md)

## Public Types

- [ModemFirmware::List](#List-typedef)
- [ModemFirmware::Ptr](#Ptr-typedef)

## Public Functions

- [ModemFirmware(const QString &path, QObject \*parent = nullptr)](#ModemFirmware)
- [QDBusPendingReply\<QString, ModemManager::QVariantMapList\> listImages()](#listImages)
- [void selectImage(const QString &uniqueid)](#selectImage)
- [ModemManager::FirmwareUpdateSettings updateSettings() const](#updateSettings) (since 6.24.0)

## Signals

- [void updateSettingsChanged(const ModemManager::FirmwareUpdateSettings &settings)](#updateSettingsChanged) (since 6.24.0)

## Detailed Description {#details}

This class allows clients to select or install firmware images on modems.

Firmware slots and firmware images are identified by arbitrary opaque strings.

## Member Type Documentation {#member-type-documentation}

### ModemFirmware::List {#List-typedef}

### ModemFirmware::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ModemFirmware::ModemFirmware(const QString &*path*, QObject \**parent* = nullptr) {#ModemFirmware}

### QDBusPendingReply\<QString, ModemManager::QVariantMapList\> ModemFirmware::listImages() {#listImages}

List installed firmware images.

Depending on the type of modem, installed images may be stored on the host or the modem. Installed images can be selected non-destructively.

Returns `selected` ([QString](https://doc.qt.io/qt-6/qstring.html)) The unique name of the selected firmware image, or the empty string if no image is selected. `installed` ([QVariantMapList](modemmanager.md#QVariantMapList-typedef)) A map of dictionaries containing the properties of the installed firmware images.

### void ModemFirmware::selectImage(const QString &*uniqueid*) {#selectImage}

Selects a different firmware image to use, and immediately resets the modem so that it begins using the new firmware image.

The method will fail if the identifier does not match any of the names returned by [listImages](modemmanager-modemfirmware.md#listImages)(), or if the image could not be selected for some reason.

`uniqueid` The unique ID of the firmware image to select.

### \[since 6.24.0\] ModemManager::FirmwareUpdateSettings ModemFirmware::updateSettings() const {#updateSettings}

Returns firmware update settings.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void ModemFirmware::updateSettingsChanged(const ModemManager::FirmwareUpdateSettings &*settings*) {#updateSettingsChanged}

This function was introduced in Qt 6.24.0.
