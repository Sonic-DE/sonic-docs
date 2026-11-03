---
title: "PlasmaQuick::QuickViewSharedEngine Class"
description: "Plasma Quick."
---

# PlasmaQuick::QuickViewSharedEngine Class

Plasma Quick. [More...](#details)

- **Header:** `#include <KQuickAddons/QuickViewSharedEngine>`
- **CMake:** `find_package(PlasmaQuick REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::PlasmaQuick)`
- **Inherits:** [QQuickWindow](https://doc.qt.io/qt-6/qquickwindow.html)

[List of all members, including inherited members](plasmaquick-quickviewsharedengine-members.md)

## Public Functions

- [void setTranslationDomain(const QString &translationDomain)](#setTranslationDomain)
- [QString translationDomain() const](#translationDomain)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### void QuickViewSharedEngine::setTranslationDomain(const QString &*translationDomain*) {#setTranslationDomain}

Installs a translation domain for all i18n global functions. If a translation domain is set all i18n calls delegate to the matching i18nd calls with the provided translation domain.

The [translationDomain](plasmaquick-quickviewsharedengine.md#translationDomain) affects all i18n calls including those from imports. Because of that modules intended to be used as imports should prefer the i18nd variants and set the translation domain explicitly in each call.

This method is only required if your declarative usage is inside a library. If it's in an application there is no need to set the translation domain as the application's domain can be used.

`translationDomain` The translation domain to be used for i18n calls.

*See also* [translationDomain](plasmaquick-quickviewsharedengine.md#translationDomain)()

### QString QuickViewSharedEngine::translationDomain() const {#translationDomain}

Returns the translation domain for the i18n calls done in this QML engine

*See also* [setTranslationDomain](plasmaquick-quickviewsharedengine.md#setTranslationDomain)()
