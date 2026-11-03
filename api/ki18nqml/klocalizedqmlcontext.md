---
title: "KLocalizedQmlContext Class"
description: "This class is meant to be used to simplify integration of the KI18n framework in QML. This class was introduced in Qt 6.8."
---

# KLocalizedQmlContext Class

This class is meant to be used to simplify integration of the KI18n framework in QML. This class was introduced in Qt 6.8. [More...](#details)

- **Header:** `#include <KLocalizedQmlContext>`
- **Since:** Qt 6.8
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS I18n)`  
  `target_link_libraries(mytarget PRIVATE KF6::I18nQml)`
- **In QML:** [KI18n](qml-org-kde-ki18n-ki18n.md) and [KI18nContext](qml-org-kde-ki18n-ki18ncontext.md)
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](klocalizedqmlcontext-members.md)

## Properties

- [translationDomain : QString](#translationDomain-prop)

## Public Functions

- [KLocalizedQmlContext(QObject \*parent = nullptr)](#KLocalizedQmlContext)
- [void setTranslationDomain(const QString &domain)](#setTranslationDomain)
- [QString translationDomain() const](#translationDomain)

## Detailed Description {#details}

The way to do so, is by creating this object and setting it as a context object:

```cpp
QQmlApplicationEngine engine;
auto ctx = new KLocalizedQmlContext(&engine);
engine->rootContext()->setContextObject(ctx);
QQmlEngine::setContextForObject(ctx, engine.rootContext());
ctx->setTranslationDomain(...);
```

In many cases this can be simplified using [KLocalization::setupLocalizedContext](klocalizedqmlcontext.md#setupLocalizedContext)():

```cpp
QQmlApplicationEngine engine;
KLocalization::setupLocalizedContext(&engine);
```

Then KI18n.i18n\*() and KI18n.xi18n\*() functions should be available for use from the code loaded in the engine, for the view.

Unlike its predecessor KLocalizedContext this does automatically trigger a binding re-evaluation when the application language is changed at runtime (with Qt 6.6 or higher).

> **Note:** Plural functions differ from the C/C++ version. On QML/JS we can get a real value easily. To solve warnings on those cases we'll cast the first argument to make sure it's taken into account for the plural.

> **Warning:** For history reasons the i18n functions are also available on the root context without KI18n.\* prefix. It is very recommended to use the KI18n.\* version moving forward, so QML tooling like qmlls and qmllint can inspect the API calls. KI18n.\* was introduced in version 6.21.

## Property Documentation {#property-documentation}

### translationDomain : QString {#translationDomain-prop}

This property only needs to be specified if the context is being run on a library. in an application there is no need to set the translation domain as the application's domain can be used.

**Access functions:**

- `QString` **[translationDomain](klocalizedqmlcontext.md#translationDomain)**() const
- `void` **[setTranslationDomain](klocalizedqmlcontext.md#setTranslationDomain)**(const `QString` &*domain*)

**Notifier signal:**

- `void` **translationDomainChanged**(const `QString` &*translationDomain*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KLocalizedQmlContext::KLocalizedQmlContext(QObject \**parent* = nullptr) {#KLocalizedQmlContext}

### void KLocalizedQmlContext::setTranslationDomain(const QString &*domain*) {#setTranslationDomain}

> **Note:** Setter function for property [translationDomain](klocalizedqmlcontext.md#translationDomain-prop).

*See also* [translationDomain](klocalizedqmlcontext.md#translationDomain)()

### QString KLocalizedQmlContext::translationDomain() const {#translationDomain}

> **Note:** Getter function for property [translationDomain](klocalizedqmlcontext.md#translationDomain-prop).

*See also* [setTranslationDomain](klocalizedqmlcontext.md#setTranslationDomain)()

## Related Non-Members {#related-non-members}

### \[since 6.8\] KLocalizedQmlContext \*setupLocalizedContext(QQmlEngine \**engine*) {#setupLocalizedContext}

Creates a [KLocalizedQmlContext](klocalizedqmlcontext.md) engine and sets it up in the root context of `engine`.

If `TRANSLATION_DOMAIN` is defined, that is also set on the created context.

This function was introduced in Qt 6.8.
