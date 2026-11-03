---
title: "ModemManager::ModemDevice Class"
description: "Qt wrapper for modemmanager API."
---

# ModemManager::ModemDevice Class

Qt wrapper for modemmanager API. [More...](#details)

- **Header:** `#include <ModemManager::ModemDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](modemmanager-modemdevice-members.md)

## Public Types

- [ModemDevice::List](#List-typedef)
- [ModemDevice::Ptr](#Ptr-typedef)

## Public Functions

- [ModemDevice(const QString &path, QObject \*parent = nullptr)](#ModemDevice-1)
- [ModemManager::Bearer::List bearers() const](#bearers)
- [ModemManager::ModemCellBroadcast::Ptr cellBroadcastInterface()](#cellBroadcastInterface) (since 6.24.0)
- [ModemManager::Bearer::Ptr findBearer(const QString &uni)](#findBearer)
- [bool hasInterface(ModemManager::ModemDevice::InterfaceType type) const](#hasInterface)
- [ModemManager::Interface::Ptr interface(ModemManager::ModemDevice::InterfaceType type) const](#interface)
- [ModemManager::Interface::List interfaces() const](#interfaces)
- [bool isCdmaModem() const](#isCdmaModem)
- [bool isGsmModem() const](#isGsmModem)
- [ModemManager::ModemMessaging::Ptr messagingInterface()](#messagingInterface)
- [ModemManager::Modem::Ptr modemInterface()](#modemInterface)
- [ModemManager::Sim::Ptr sim() const](#sim)
- [QString uni() const](#uni)

## Signals

- [void bearerAdded(const QString &udi)](#bearerAdded)
- [void bearerRemoved(const QString &udi)](#bearerRemoved)
- [void interfaceAdded(ModemManager::ModemDevice::InterfaceType type)](#interfaceAdded)
- [void interfaceRemoved(ModemManager::ModemDevice::InterfaceType type)](#interfaceRemoved)
- [void simAdded(const QString &udi)](#simAdded)
- [void simRemoved(const QString &udi)](#simRemoved)

## Protected Functions

- [ModemDevice(ModemManager::ModemDevicePrivate &dd, QObject \*parent = nullptr)](#ModemDevice)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### ModemDevice::List {#List-typedef}

### ModemDevice::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] ModemDevice::ModemDevice(ModemManager::ModemDevicePrivate &*dd*, QObject \**parent* = nullptr) {#ModemDevice}

### \[explicit\] ModemDevice::ModemDevice(const QString &*path*, QObject \**parent* = nullptr) {#ModemDevice-1}

### \[signal\] void ModemDevice::bearerAdded(const QString &*udi*) {#bearerAdded}

### \[signal\] void ModemDevice::bearerRemoved(const QString &*udi*) {#bearerRemoved}

### ModemManager::Bearer::List ModemDevice::bearers() const {#bearers}

### \[since 6.24.0\] ModemManager::ModemCellBroadcast::Ptr ModemDevice::cellBroadcastInterface() {#cellBroadcastInterface}

This function was introduced in Qt 6.24.0.

### ModemManager::Bearer::Ptr ModemDevice::findBearer(const QString &*uni*) {#findBearer}

### bool ModemDevice::hasInterface(ModemManager::ModemDevice::InterfaceType *type*) const {#hasInterface}

### ModemManager::Interface::Ptr ModemDevice::interface(ModemManager::ModemDevice::InterfaceType *type*) const {#interface}

### \[signal\] void ModemDevice::interfaceAdded(ModemManager::ModemDevice::InterfaceType *type*) {#interfaceAdded}

### \[signal\] void ModemDevice::interfaceRemoved(ModemManager::ModemDevice::InterfaceType *type*) {#interfaceRemoved}

### ModemManager::Interface::List ModemDevice::interfaces() const {#interfaces}

### bool ModemDevice::isCdmaModem() const {#isCdmaModem}

### bool ModemDevice::isGsmModem() const {#isGsmModem}

### ModemManager::ModemMessaging::Ptr ModemDevice::messagingInterface() {#messagingInterface}

### ModemManager::Modem::Ptr ModemDevice::modemInterface() {#modemInterface}

### ModemManager::Sim::Ptr ModemDevice::sim() const {#sim}

### \[signal\] void ModemDevice::simAdded(const QString &*udi*) {#simAdded}

### \[signal\] void ModemDevice::simRemoved(const QString &*udi*) {#simRemoved}

### QString ModemDevice::uni() const {#uni}

> **Note:** Getter function for property uni.
