---
title: "KLocalizedContext Class"
description: "This class is meant to be used to simplify integration of the KI18n framework in QML. This class is deprecated since 6.8. We strongly advise against using it in new code."
---

# KLocalizedContext Class

This class is meant to be used to simplify integration of the KI18n framework in QML. **This class is deprecated since 6.8. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <KLocalizedContext>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS I18n)`  
  `target_link_libraries(mytarget PRIVATE KF6::I18n)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Status:** Deprecated since 6.8

[List of all members, including inherited members](klocalizedcontext-members.md)

## Properties

- [translationDomain : QString](#translationDomain-prop)

## Public Functions

- [KLocalizedContext(QObject \*parent = nullptr)](#KLocalizedContext)
- [void setTranslationDomain(const QString &domain)](#setTranslationDomain)
- [QString translationDomain() const](#translationDomain)

**This class is deprecated since 6.8. We strongly advise against using it in new code.**

## Detailed Description {#details}

The way to do so, is by creating this object and setting it as a context object:

```cpp
QQuickView* view = new QQuickView;
view.engine()->rootContext()->setContextObject(new KLocalizedContext(view));
```

Then i18n\*() and xi18n\*() functions should be available for use from the code loaded in the engine, for the view.

> **Note:** Plural functions differ from the C/C++ version. On QML/JS we can get a real value easily. To solve warnings on those cases we'll cast the first argument to make sure it's taken into account for the plural.

Use [KLocalizedQmlContext](../ki18nqml/klocalizedqmlcontext.md) or [KLocalization::setupLocalizedContext](../ki18nqml/klocalizedqmlcontext.md#setupLocalizedContext) instead.

## Property Documentation {#property-documentation}

### translationDomain : QString {#translationDomain-prop}

This property only needs to be specified if the context is being run on a library. in an application there is no need to set the translation domain as the application's domain can be used.

**Access functions:**

- `QString` **[translationDomain](klocalizedcontext.md#translationDomain)**() const
- `void` **[setTranslationDomain](klocalizedcontext.md#setTranslationDomain)**(const `QString` &*domain*)

**Notifier signal:**

- `void` **translationDomainChanged**(const `QString` &*translationDomain*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KLocalizedContext::KLocalizedContext(QObject \**parent* = nullptr) {#KLocalizedContext}

### void KLocalizedContext::setTranslationDomain(const QString &*domain*) {#setTranslationDomain}

> **Note:** Setter function for property [translationDomain](klocalizedcontext.md#translationDomain-prop).

*See also* [translationDomain](klocalizedcontext.md#translationDomain)()

### QString KLocalizedContext::translationDomain() const {#translationDomain}

> **Note:** Getter function for property [translationDomain](klocalizedcontext.md#translationDomain-prop).

*See also* [setTranslationDomain](klocalizedcontext.md#setTranslationDomain)()
