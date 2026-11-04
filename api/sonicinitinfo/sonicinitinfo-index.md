---
title: "Sonic Init Info"
description: "Runtime information about the init system and seat manager."
---

# Sonic Init Info

Runtime information about the init system and seat manager.

Sonic Init Info tells SonicDE components, at runtime, which init system and seat manager the machine is running. Code can then do the right thing on systemd, OpenRC, runit, s6, dinit, sysvinit and the BSDs instead of assuming systemd.

- [Sonic::InitInfo](sonic-initinfo.md): what runs as PID 1, what manages services and seats, whether journald runs, and the VT a display manager starts on.

None of this needs root. Nothing is cached; callers keep the result.

```cpp
using namespace Sonic::InitInfo;

if (serviceManager() == ServiceManager::OpenRC) {
    // use rc-service / rc-update
}
```

## Using the Module {#using-the-module}

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the [SonicInitInfo](sonicinitinfo-module.md) package and link against its target:

```cpp
find_package(SonicInitInfo REQUIRED)
target_link_libraries(mytarget PRIVATE Sonic::InitInfo)
```

## API Reference {#api-reference}

- [Sonic Init Info C++ Classes](sonicinitinfo-module.md)
