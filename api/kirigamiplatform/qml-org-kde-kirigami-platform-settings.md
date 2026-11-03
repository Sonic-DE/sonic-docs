---
title: "Settings QML Type (Singleton)"
description: "Provides global kirigami settings about the current device setup under the singleton \"Settings\"."
---

# Settings QML Type (Singleton)

Provides global kirigami settings about the current device setup under the singleton "Settings". [More...](#details)

- Import Statement: import org.kde.kirigami.platform

> **Note:** **Note:** This type is a QML singleton. There is only one instance of this type in the QML engine.

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### applicationWindowIcon : var {#applicationWindowIcon-prop}

This property holds the name of the application window icon.

*See also* [QGuiApplication::windowIcon](https://doc.qt.io/qt-6/qguiapplication.html#windowIcon-prop)()

### hasPlatformMenuBar : bool {#hasPlatformMenuBar-prop}

This property holds whether the system has a platform menu bar; e.g. a user is on macOS or has a global menu on KDE Plasma.

> **Warning:** Android has a platform menu bar; which may not be what you expected.

### hasTransientTouchInput : bool {#hasTransientTouchInput-prop}

This property holds whether the user in this moment is interacting with the app with the touch screen.

### information : list\<string\> {#information-prop}

This property holds the runtime information about the libraries in use.

### isMobile : bool {#isMobile-prop}

This property holds whether the application is running on a small mobile device such as a mobile phone. This is used when we want to do specific adaptations to the UI for small screen form factors, such as having bigger touch areas.

### mouseWheelScrollLines : int {#mouseWheelScrollLines-prop}

This property holds the number of lines of text the mouse wheel should scroll.

### smoothScroll : bool {#smoothScroll-prop}

This property holds whether to display animated transitions when scrolling with a mouse wheel or the keyboard.

### style : string {#style-prop}

This property holds the name of the [QtQuickControls2](https://doc.qt.io/qt-6/qtquickcontrols2-module.html) style the application is using, for instance org.kde.desktop, Plasma, Material, Universal etc

### tabletMode : bool {#tabletMode-prop}

This property holds whether the application is running on a device that is behaving like a tablet.

> **Note:** This doesn't mean exactly a tablet form factor, but that the preferred input mode for the device is the touch screen and that pointer and keyboard are either secondary or not available.

### tabletModeAvailable : bool {#tabletModeAvailable-prop}

This property holds whether the system can dynamically enter and exit tablet mode (or the device is actually a tablet). This is the case for foldable convertibles and transformable laptops that support keyboard detachment.
