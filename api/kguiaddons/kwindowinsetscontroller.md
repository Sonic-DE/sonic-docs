---
title: "KWindowInsetsController Class"
description: "Access to window insets colors. This class was introduced in Qt 6.7."
---

# KWindowInsetsController Class

Access to window insets colors. This class was introduced in Qt 6.7. [More...](#details)

- **Header:** `#include <KWindowInsetsController>`
- **Since:** Qt 6.7
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`
- **In QML:** [WindowInsetsController](qml-org-kde-guiaddons-windowinsetscontroller.md)
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kwindowinsetscontroller-members.md)

## Properties

- [navigationBarBackgroundColor : QColor](#navigationBarBackgroundColor-prop)
- [statusBarBackgroundColor : QColor](#statusBarBackgroundColor-prop)

## Detailed Description {#details}

On most platforms this does nothing, on Android it allows to customize the (top) status bar and (botton) navigation bar background colors, e.g. to match the current window or application colors.

Note that the foreground colors on Android are automatically chosen based on the background color.

```cpp
Component.onComplete: {
    WindowInsetsController.statusBarBackgroundColor = Kirigami.Theme.backgroundColor;
    WindowInsetsController.navigationBarBackgroundColor = Kirigami.Theme.backgroundColor;
}
```

## Property Documentation {#property-documentation}

### navigationBarBackgroundColor : QColor {#navigationBarBackgroundColor-prop}

Background color of the navigation bar.

**Access functions:**

- `QColor` **navigationBarBackgroundColor**() const
- `void` **setNavigationBarBackgroundColor**(const `QColor` &*color*)

**Notifier signal:**

- `void` **navigationBarBackgroundColorChanged**()

### statusBarBackgroundColor : QColor {#statusBarBackgroundColor-prop}

Background color of the status bar.

**Access functions:**

- `QColor` **statusBarBackgroundColor**() const
- `void` **setStatusBarBackgroundColor**(const `QColor` &*color*)

**Notifier signal:**

- `void` **statusBarBackgroundColorChanged**()
