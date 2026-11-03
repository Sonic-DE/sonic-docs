---
title: "KI18nContext QML Type"
description: "Creatable variant of KI18n. This type was introduced in Qt 6.23."
---

# KI18nContext QML Type

Creatable variant of KI18n. This type was introduced in Qt 6.23. [More...](#details)

- Import Statement: import org.kde.ki18n
- Since: Qt 6.23
- In C++: [KLocalizedQmlContext](klocalizedqmlcontext.md)
- Inherits: [KI18n](qml-org-kde-ki18n-ki18n.md)

## Detailed Description {#details}

This is a creatable variant of KI18n and may be used to create multiple localized contexts right from within QML. In particular useful when working with multiple translation domains (such as in library use cases).

Unlike the KI18n variant this does not require help from the C++ side and can be used entirely from QML:

```qml
readonly property KI18nContext libI18n: KI18nContext {
    translationDomain: "librocketship"
}
text: libI18n.i18nc("@title", "Welcome to Space")
```

*See also* [KI18n](qml-org-kde-ki18n-ki18n.md), [KLocalizedQmlContext::KLocalizedQmlContext](klocalizedqmlcontext.md#KLocalizedQmlContext)()

## Property Documentation {#property-documentation}

### translationDomain : string {#translationDomain-prop}

The translation domain to use for this context. This must be explicitly set for the [KI18nContext](qml-org-kde-ki18n-ki18ncontext.md) to be functional.
