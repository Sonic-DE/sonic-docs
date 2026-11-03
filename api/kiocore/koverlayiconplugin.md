---
title: "KOverlayIconPlugin Class"
description: "Base class for overlay icon plugins."
---

# KOverlayIconPlugin Class

Base class for overlay icon plugins. [More...](#details)

- **Header:** `#include <KOverlayIconPlugin>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](koverlayiconplugin-members.md)

## Public Functions

- [QStringList getOverlays(const QUrl &item)](#getOverlays)

## Signals

- [void overlaysChanged(const QUrl &url, const QStringList &overlays)](#overlaysChanged)

## Detailed Description {#details}

Enables file managers to show custom overlay icons on files.

This plugin can be created and installed through kcoreaddons\_add\_plugin

```cpp
kcoreaddons_add_plugin(myoverlayplugin SOURCES myoverlayplugin.cpp INSTALL_NAMESPACE "kf6/overlayicon")
target_link_libraries(myoverlayplugin KF6::KIOCore)
```

The C++ file should look like this:

```cpp
#include <KOverlayIconPlugin>

class MyOverlayPlugin : public KOverlayIconPlugin
{
    Q_PLUGIN_METADATA(IID "org.kde.overlayicon.myplugin")
    Q_OBJECT

public:
    MyOverlayPlugin() {
    }

    QStringList getOverlays(const QUrl &url) override {
        // Implement your logic
    }
};

#include "myoverlayplugin.moc"
```

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] QStringList KOverlayIconPlugin::getOverlays(const QUrl &*item*) {#getOverlays}

Returns a list of overlay icons to add to a file This can be a path to an icon, or the icon name

This function is called from the main thread and must not block. It is recommended to have a cache. And if the item is not in cache just return an empty list and call the [overlaysChanged](koverlayiconplugin.md#overlaysChanged) when the information is available.

### \[signal\] void KOverlayIconPlugin::overlaysChanged(const QUrl &*url*, const QStringList &*overlays*) {#overlaysChanged}

Emit this signal when the list of overlay icons changed for a given URL
