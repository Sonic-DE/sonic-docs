---
title: "KSandbox Namespace"
description: "Utility functions for use inside application sandboxes such as Flatpak or Snap."
---

# KSandbox Namespace

Utility functions for use inside application sandboxes such as Flatpak or Snap. [More...](#details)

- **Header:** `#include <KSandbox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

## Detailed Description {#details}

## Classes {#classes}

### struct [KSandbox::ProcessContext](ksandbox-processcontext.md)

## Function Documentation {#function-documentation}

### bool KSandbox::isFlatpak() {#isFlatpak}

Returns whether the application is inside a Flatpak sandbox

### bool KSandbox::isInside() {#isInside}

Returns whether the application is inside one of the supported sandboxes

### bool KSandbox::isSnap() {#isSnap}

Returns whether the application is inside a Snap sandbox

### KSandbox::ProcessContext KSandbox::makeHostContext(const QProcess &*process*) {#makeHostContext}

Returns the actual program and arguments for running the [QProcess](https://doc.qt.io/qt-6/qprocess.html) on the host (e.g. a flatpak-spawn-wrapped argument list)

### void KSandbox::startHostProcess(QProcess &*process*, QProcess::OpenMode *mode* = QProcess::ReadWrite) {#startHostProcess}

Starts the [QProcess](https://doc.qt.io/qt-6/qprocess.html) on the host (if the current context is inside a sandbox, otherwise it simply runs [QProcess::start](https://doc.qt.io/qt-6/qprocess.html#start))
