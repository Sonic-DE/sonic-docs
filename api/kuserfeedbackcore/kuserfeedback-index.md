---
title: "KUserFeedback"
description: "Framework for collecting feedback from application users via telemetry and targeted surveys.."
---

# KUserFeedback

Framework for collecting feedback from application users via telemetry and targeted surveys..

Framework for collecting feedback from application users via telemetry and targeted surveys.

## Using the Module {#using-the-module}

Using a Qt module's C++ API requires linking against the module library, either directly or through other dependencies. Several build tools have dedicated support for this, including CMake and [qmake](https://doc.qt.io/qt-6/resources.html#qmake).

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the needed module component in the `Qt6` package:

```cpp
find_package(Qt6 REQUIRED COMPONENTS KF6)
target_link_libraries(mytarget PRIVATE Qt6::KF6)
```

For more details, see the Build with CMake overview.

## API Reference {#api-reference}

- [KUserFeedbackCore C++ Classes](kuserfeedbackcore-module.md)
- [KUserFeedbackWidgets C++ Classes](../kuserfeedbackwidgets/kuserfeedbackwidgets-module.md)
- [KUserFeedback QML Types](../kuserfeedbackqml/org-kde-userfeedback-qmlmodule.md)
