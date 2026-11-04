---
title: "Sonic::Logging Namespace"
description: "The SonicDE message handler."
---

# Sonic::Logging Namespace

The SonicDE message handler. [More...](#details)

- **Header:** `#include <Sonic/Logging/Logging>`
- **CMake:** `find_package(SonicLogging REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::Logging)`

## Detailed Description {#details}

Every executable writes its own log file: /var/log/sonic/\<binary\>.log when it runs as root, ~/.local/state/sonic/\<binary\>.log otherwise. Messages also go to journald when it is running. When a service manager already captures the program's output (systemd, runit, s6, OpenRC's supervise-daemon, dinit, or an X session's ~/.xsession-errors), lines go to that output instead and no file is written.

Each line reads "\<ISO timestamp with ms\> (DD\|II\|WW\|EE) \[\<source\>\] \<message\>", where \<source\> is the category for the executable's own messages, the library's ID for messages from a library, and the binary name for messages without a category.

## Classes {#classes}

### struct [Logging::Options](sonic-logging-options.md)

Callers set only the members they change, for example `Sonic::Logging::install({.rotateOnStartup = true})`.

## Function Documentation {#function-documentation}

### void Logging::handleMessage(QtMsgType *type*, const QMessageLogContext &*context*, const QString &*message*) {#handleMessage}

The message handler [install](sonic-logging.md#install)() installs: writes `message` of `type`, with its `context`, to the program's log outputs. Before [install](sonic-logging.md#install)(), lines go to stderr.

### QtMessageHandler Logging::install(const Sonic::Logging::Options &*options* = {}) {#install}

Installs the handler for this program, set up by `options`; returns the handler that was in place before any Sonic install. Works before or after the Q\*Application exists. A second call returns nullptr and changes nothing.

### QString Logging::logFilePath() {#logFilePath}

The file chosen by [install](sonic-logging.md#install)(); empty before [install](sonic-logging.md#install)() and when a service manager captures the output.

### bool Logging::prepareRootLogDirectory() {#prepareRootLogDirectory}

Root only: creates or repairs the root log directory; false, with one stderr line, if it can't.

### QString Logging::rootLogDirectory() {#rootLogDirectory}

The compiled-in root log directory.

## Macro Documentation {#macro-documentation}

### SONIC\_LOGGING\_AUTO\_INSTALL(*...*) {#SONIC_LOGGING_AUTO_INSTALL}

For plugins: installs the handler in the host process, unless the host installed its own. The optional argument is a void() function to run once at the same point, also in plugins loaded after the application exists.

### SONIC\_LOGGING\_COMPONENT(*id*) {#SONIC_LOGGING_COMPONENT}

Logging for SonicDE code.

Each library, plugin or executable declares its component once, in exactly one .cpp file:

```cpp
SONIC_LOGGING_COMPONENT("org.sonicde.frameworks.ipc");
```

and then logs anywhere in that binary with [sonicDebug](sonic-logging.md#sonicDebug)(), [sonicInfo](sonic-logging.md#sonicInfo)(), [sonicWarning](sonic-logging.md#sonicWarning)() and [sonicCritical](sonic-logging.md#sonicCritical)(), or [sonicFatal](sonic-logging.md#sonicFatal)() to log a critical line and abort. The component ID `id` is the category name, so the standard rules apply, for example QT\_LOGGING\_RULES="org.sonicde.frameworks.ipc.debug=true".

Debug messages are on by default only when the declaring code is a debug build.

A second declaration in the same binary is a duplicate-definition link error, and logging without any declaration is an undefined-symbol link error. Code compiled into several binaries never declares a component.

### sonicCritical() {#sonicCritical}

Returns a [QDebug](https://doc.qt.io/qt-6/qdebug.html) stream for a critical message under the binary's component, declared with [SONIC\_LOGGING\_COMPONENT](sonic-logging.md#SONIC_LOGGING_COMPONENT)().

### sonicDebug() {#sonicDebug}

Returns a [QDebug](https://doc.qt.io/qt-6/qdebug.html) stream for a debug message under the binary's component, declared with [SONIC\_LOGGING\_COMPONENT](sonic-logging.md#SONIC_LOGGING_COMPONENT)(). Nothing is formatted when debug messages are off for the component.

### sonicFatal() {#sonicFatal}

Logs a critical line under the component, then aborts; logging rules can't turn it off.

### sonicInfo() {#sonicInfo}

Returns a [QDebug](https://doc.qt.io/qt-6/qdebug.html) stream for an info message under the binary's component, declared with [SONIC\_LOGGING\_COMPONENT](sonic-logging.md#SONIC_LOGGING_COMPONENT)().

### sonicWarning() {#sonicWarning}

Returns a [QDebug](https://doc.qt.io/qt-6/qdebug.html) stream for a warning under the binary's component, declared with [SONIC\_LOGGING\_COMPONENT](sonic-logging.md#SONIC_LOGGING_COMPONENT)().
