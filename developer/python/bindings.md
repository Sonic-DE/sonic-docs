---
title: Using Python bindings for KDE Frameworks
description: Extend your application with SonicDE's frameworks from Python.
source_url: https://develop.kde.org/docs/getting-started/python/python-bindings/
source_authors: [Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "python/ folders and BUILD_PYTHON_BINDINGS of SonicDE's frameworks, ECMGeneratePythonBindings, API class pages; every class listed was imported from SonicDE's built bindings and the example run with Python 3.14, except KUnitConversion, which isn't built in the checked tree (its bindings were checked from source)"
---

# Using Python bindings for KDE Frameworks

Several of SonicDE's frameworks have Python bindings. Most notably:

* [KCoreAddons](/docs/api/kcoreaddons/kcoreaddons-index)
  * [KAboutData](/docs/api/kcoreaddons/kaboutdata)
  * [KAboutLicense](/docs/api/kcoreaddons/kaboutlicense)
  * [KSandbox](/docs/api/kcoreaddons/ksandbox)
* [KGuiAddons](/docs/api/kguiaddons/kguiaddons-index)
  * [KSystemClipboard](/docs/api/kguiaddons/ksystemclipboard)
  * [KCursorSaver](/docs/api/kguiaddons/kcursorsaver)
  * [KColorUtils](/docs/api/kguiaddons/kcolorutils)
* [KWidgetsAddons](/docs/api/kwidgetsaddons/kwidgetsaddons-index)
  * [KMessageDialog](/docs/api/kwidgetsaddons/kmessagedialog)
  * [KMessageBox](/docs/api/kwidgetsaddons/kmessagebox)
  * [KContextualHelpButton](/docs/api/kwidgetsaddons/kcontextualhelpbutton)
  * [KFontChooser](/docs/api/kwidgetsaddons/kfontchooser)
  * [KSeparator](/docs/api/kwidgetsaddons/kseparator)
* [KStatusNotifierItem](/docs/api/kstatusnotifieritem/kstatusnotifieritem-index)
  * [KStatusNotifierItem](/docs/api/kstatusnotifieritem/kstatusnotifieritem)
* [KNotifications](/docs/api/knotifications/knotifications-index)
  * [KNotification](/docs/api/knotifications/knotification)
* [KUnitConversion](/docs/api/kunitconversion/kunitconversion-index)
* [KXmlGui](/docs/api/kxmlgui/kxmlgui-index)
  * [KXmlGuiWindow](/docs/api/kxmlgui/kxmlguiwindow)
  * [KActionCollection](/docs/api/kxmlgui/kactioncollection)
  * [KBugReport](/docs/api/kxmlgui/kbugreport)
  * [KToolBar](/docs/api/kxmlgui/ktoolbar)

## Bindings installation

As with Kirigami and PySide6, the bindings must be built against the same Qt version as PySide6, so don't install them with `pip`: use the ones from your SonicDE installation (see [Building Sonic-DE](../building.md)). Frameworks that have bindings build them by default, through their `BUILD_PYTHON_BINDINGS` CMake option.

They must also match your Python version, as each binding is built for one: a virtual environment using another version of Python can't import them.

> **Contributing to the bindings:** To make another framework available in Python, its C++ library needs to use [ECMGeneratePythonBindings](https://github.com/Sonic-DE/sonic-frameworks-cmake-modules/blob/master/modules/ECMGeneratePythonBindings.cmake); the existing frameworks do this in their `python/` folders. When the project is built, this generates a CPython `.so` file that is installed in Python's `site-packages` directory, such as `/usr/lib64/python3.14/site-packages/`, which makes it available to Python scripts. If the `site-packages` files are installed elsewhere, point Python to them with `PYTHONPATH`. To propose a change, open a pull request in the [framework's repository](https://github.com/Sonic-DE).

## Reading C++ documentation for use in Python

In the [API reference](/docs/api), the top of each class page lists its include and the CMake component it belongs to:

```cpp
#include <KAboutData>
```

```cmake
find_package(KF6 REQUIRED COMPONENTS CoreAddons)
```

In Python, this translates to the following import, with the name of the framework's module:

```python
from KCoreAddons import KAboutData
```

Where in C++ you would use:

```cpp
KAboutData aboutData(
    QStringLiteral("foo"), QStringLiteral("Foo"), QStringLiteral("0.1"),
    QStringLiteral("To Foo or not To Foo"),
    KAboutLicense::GPL,
    QStringLiteral("Copyright 2017 Bar Foundation"), QString(),
    QStringLiteral("https://www.foo-the-app.net"));
aboutData.setDesktopFileName(QStringLiteral("org.barfoundation.foo"));
KAboutData::setApplicationData(aboutData);

auto icon = QIcon::fromTheme(QStringLiteral("start-here-sonicde"));
QApplication::setWindowIcon(icon);
```

In Python you would write:

```python
aboutData = KAboutData(
    "foo", "Foo", "0.1",
    "To Foo or not To Foo",
    KAboutLicense.GPL,
    "Copyright 2017 Bar Foundation", "",
    "https://www.foo-the-app.net")
aboutData.setDesktopFileName("org.barfoundation.foo")
KAboutData.setApplicationData(aboutData)

icon = QIcon.fromTheme("start-here-sonicde")
QApplication.setWindowIcon(icon)
```

PySide6 [has no QString or QStringLiteral](https://wiki.qt.io/Qt_for_Python/Considerations), and uses the native Python [str type](https://docs.python.org/3/library/stdtypes.html#textseq) instead. So the default `QString()` constructor, which creates an empty QString, becomes `""`, and `QStringLiteral()` can simply be left out.

Static functions written with `::` (like `QIcon::fromTheme()`) are called with `.` in Python. The same goes for enums (like `KAboutLicense::GPL`).
