---
title: "KI18n"
description: "Advanced internationalization framework."
---

# KI18n

Advanced internationalization framework.

There's two libraries provided, KI18n for Gettext-based text internationalization, and [KI18nLocaleData](../ki18nlocaledata/ki18nlocaledata-module.md) for access to data about countries and timezones.

KI18n provides functionality for internationalizing user interface text in applications, based on the GNU Gettext translation system. It wraps the standard Gettext functionality, so that the programmers and translators can use the familiar Gettext tools and workflows.

KI18n provides additional functionality as well, for both programmers and translators, which can help to achieve a higher overall quality of source and translated text. This includes argument capturing, customizable markup, and translation scripting.

You can read more about how to localize your software with ki18n in the [Programmer's Guide](https://invent.kde.org/frameworks/ki18n/-/blob/master/docs/programmers-guide.md).

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

- [KI18n C++ Classes](ki18n-module.md)
- [KI18nQml C++ Classes](../ki18nqml/ki18nqml-module.md)
- [KI18nQml QML Types](../ki18nqml/org-kde-ki18n-qmlmodule.md)
- [KI18nLocaleData C++ Classes](../ki18nlocaledata/ki18nlocaledata-module.md)
- [KI18nLocaleData QML Types](../ki18nlocaledataqml/org-kde-i18n-localedata-qmlmodule.md)
- Obsolete Classes
