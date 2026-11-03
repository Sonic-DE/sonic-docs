---
title: "KDEDModule Class"
description: "The base class for KDED modules."
---

# KDEDModule Class

The base class for KDED modules. [More...](#details)

- **Header:** `#include <KDEDModule>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DBusAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::DBusAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kdedmodule-members.md)

## Public Functions

- [KDEDModule(QObject \*parent = nullptr)](#KDEDModule)
- [QString moduleName() const](#moduleName)
- [void setModuleName(const QString &name)](#setModuleName)

## Signals

- [void moduleRegistered(const QDBusObjectPath &path)](#moduleRegistered)
- [void windowRegistered(qlonglong windowId)](#windowRegistered)
- [void windowUnregistered(qlonglong windowId)](#windowUnregistered)

## Static Public Members

- [QString moduleForMessage(const QDBusMessage &message)](#moduleForMessage)

## Detailed Description {#details}

KDED modules are constructed as shared libraries that are loaded on-demand into the kded daemon at runtime.

See https://invent.kde.org/frameworks/kded/-/blob/master/docs/HOWTO for documentation about writing kded modules.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDEDModule::KDEDModule(QObject \**parent* = nullptr) {#KDEDModule}

Creates a new kded module with the given `parent`.

### \[static\] QString KDEDModule::moduleForMessage(const QDBusMessage &*message*) {#moduleForMessage}

Returns the module being called by this D-Bus `message`.

Useful for autoloading modules in kded and similar daemons.

### QString KDEDModule::moduleName() const {#moduleName}

The name of the module used to register to D-Bus.

*See also* [setModuleName](kdedmodule.md#setModuleName)()

### \[signal\] void KDEDModule::moduleRegistered(const QDBusObjectPath &*path*) {#moduleRegistered}

Emitted after the module is registered successfully with D-Bus under the specified D-Bus object `path`.

### void KDEDModule::setModuleName(const QString &*name*) {#setModuleName}

Sets the `name` of the module, and uses it to register the module to D-Bus.

For modules loaded as plugins by a daemon, this is called automatically by the daemon after loading the module. Module authors should NOT call this.

*See also* [moduleName](kdedmodule.md#moduleName)()

### \[signal\] void KDEDModule::windowRegistered(qlonglong *windowId*) {#windowRegistered}

Emitted when a mainwindow with the specified `windowId` registers itself.

### \[signal\] void KDEDModule::windowUnregistered(qlonglong *windowId*) {#windowUnregistered}

Emitted when a mainwindow with the specified `windowId` unregisters itself.
