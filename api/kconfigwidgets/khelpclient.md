---
title: "KHelpClient Namespace"
description: "Provides utility functions for access to help manuals."
---

# KHelpClient Namespace

Provides utility functions for access to help manuals. [More...](#details)

- **Header:** `#include <KHelpClient>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### void KHelpClient::invokeHelp(const QString &*anchor* = QString(), const QString &*appname* = QString()) {#invokeHelp}

Invokes the KHelpCenter HTML help viewer from docbook sources.

The HTML file will be found using the X-DocPath entry in the application's desktop file. It can be either a relative path, or a website URL.

`anchor` This has to be a defined anchor in your docbook sources or website. If empty the main index is loaded.

`appname` This allows you to specify the .desktop file to get the help path from. If empty the [QCoreApplication::applicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop)() is used.
