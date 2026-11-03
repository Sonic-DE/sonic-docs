---
title: "NetworkManager::SettingsNotifier Class"
description: "This class manages provides access to connections and notify about new ones."
---

# NetworkManager::SettingsNotifier Class

This class manages provides access to connections and notify about new ones. [More...](#details)

- **Header:** `#include <NetworkManagerQt/Settings>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-settingsnotifier-members.md)

## Signals

- [void canModifyChanged(bool canModify)](#canModifyChanged)
- [void connectionAdded(const QString &path)](#connectionAdded)
- [void connectionRemoved(const QString &path)](#connectionRemoved)
- [void hostnameChanged(const QString &hostname)](#hostnameChanged)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[signal\] void SettingsNotifier::canModifyChanged(bool *canModify*) {#canModifyChanged}

Emitted when the settings are modifiable by user

`canModify` `true` if the user can modify the settings

### \[signal\] void SettingsNotifier::connectionAdded(const QString &*path*) {#connectionAdded}

Emitted when a new connection is added

> **Note:** This signal is not emitted when the Network Manager daemon starts, if you are interested in keeping an updated listing of connections you must also watch for [NetworkManager::Notifier::serviceAppeared](networkmanager-notifier.md#serviceAppeared)() and [NetworkManager::Notifier::serviceDisappeared](networkmanager-notifier.md#serviceDisappeared)() signals

### \[signal\] void SettingsNotifier::connectionRemoved(const QString &*path*) {#connectionRemoved}

Emitted when a new connection is removed

> **Note:** This signal is not emitted when the Network Manager daemon starts, if you are interested in keeping an updated listing of connections you must also watch for [NetworkManager::Notifier::serviceAppeared](networkmanager-notifier.md#serviceAppeared)() and [NetworkManager::Notifier::serviceDisappeared](networkmanager-notifier.md#serviceDisappeared)() signals

### \[signal\] void SettingsNotifier::hostnameChanged(const QString &*hostname*) {#hostnameChanged}

Emitted when the hostname has changed

`hostname` new hostname
