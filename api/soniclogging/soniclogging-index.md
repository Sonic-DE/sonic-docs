---
title: "Sonic Logging"
description: "The SonicDE message handler and logging API."
---

# Sonic Logging

The SonicDE message handler and logging API.

Sonic Logging is the logging library for SonicDE. It installs a Qt message handler that gives every executable its own log file, sends messages to journald where it runs, and gives SonicDE code a small logging API. Logs stay usable without systemd.

- [Sonic::Logging](sonic-logging.md): install() sets up the handler for a program.
- [SONIC\_LOGGING\_COMPONENT](sonic-logging.md#SONIC_LOGGING_COMPONENT)(): declares a binary's component, which [sonicDebug](sonic-logging.md#sonicDebug)(), [sonicInfo](sonic-logging.md#sonicInfo)(), [sonicWarning](sonic-logging.md#sonicWarning)(), [sonicCritical](sonic-logging.md#sonicCritical)() and [sonicFatal](sonic-logging.md#sonicFatal)() log under.

## Using the Module {#using-the-module}

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the [SonicLogging](soniclogging-module.md) package and link against its target:

```cpp
find_package(SonicLogging REQUIRED)
target_link_libraries(mytarget PRIVATE Sonic::Logging)
```

## API Reference {#api-reference}

- [Sonic Logging C++ Classes](soniclogging-module.md)
