---
title: "WindowInsetsController QML Type (Singleton)"
description: "Access to window insets colors. This type was introduced in Qt 6.7."
---

# WindowInsetsController QML Type (Singleton)

Access to window insets colors. This type was introduced in Qt 6.7. [More...](#details)

- Import Statement: import org.kde.guiaddons
- Since: Qt 6.7
- In C++: [KWindowInsetsController](kwindowinsetscontroller.md)

> **Note:** **Note:** This type is a QML singleton. There is only one instance of this type in the QML engine.

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

### navigationBarBackgroundColor : color {#navigationBarBackgroundColor-prop}

Background color of the navigation bar.

### statusBarBackgroundColor : color {#statusBarBackgroundColor-prop}

Background color of the status bar.
