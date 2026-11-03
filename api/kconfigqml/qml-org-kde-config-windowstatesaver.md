---
title: "WindowStateSaver QML Type"
description: "Creates a KWindowStateSaver in QML, and assigns it to the window it's parented to. This type was introduced in Qt 6.5."
---

# WindowStateSaver QML Type

Creates a [KWindowStateSaver](../kconfiggui/kwindowstatesaver.md) in QML, and assigns it to the window it's parented to. This type was introduced in Qt 6.5. [More...](#details)

- Import Statement: import org.kde.config
- Since: Qt 6.5

## Detailed Description {#details}

Functions exactly as [KWindowStateSaver](../kconfiggui/kwindowstatesaver.md) in C++, as it's a small wrapper around it.

The generated file containing the position and size of the application will be stored under `~/.local/state/appnamerc`, where `appname` derives from the [QCoreApplication::setApplicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop) or the component name in KAboutData::KAboutData.

```cpp
import org.kde.config as KConfig

Kirigami.ApplicationWindow {
    id: root

    title: i18n("My Window")

    KConfig.WindowStateSaver {
        configGroupName: "MainWindow"
    }
}
```

*See also* [KWindowStateSaver](../kconfiggui/kwindowstatesaver.md)

## Property Documentation {#property-documentation}

### configGroupName : string {#configGroupName-prop}
