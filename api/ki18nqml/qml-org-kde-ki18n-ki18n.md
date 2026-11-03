---
title: "KI18n QML Type"
description: "Advanced internationalization support for QML. This type was introduced in Qt 6.21."
---

# KI18n QML Type

Advanced internationalization support for QML. This type was introduced in Qt 6.21. [More...](#details)

- Import Statement: import org.kde.ki18n
- Since: Qt 6.21
- In C++: [KLocalizedQmlContext](klocalizedqmlcontext.md)
- Inherited By: [KI18nContext](qml-org-kde-ki18n-ki18ncontext.md)

## Detailed Description {#details}

To use it, create an instance and set it as the context object of your QML engine in C++:

```cpp
QQmlApplicationEngine engine;
KLocalization::setupLocalizedContext(&engine);
```

Then you can use the KI18n.i18n\*() and KI18n.xi18n\*() functions from QML code, for example:

```qml
import QtQuick
import org.kde.ki18n
Text {
    text: KI18n.i18nc("@label", "Hello World")
}
```

*See also* [KLocalizedQmlContext::KLocalizedQmlContext](klocalizedqmlcontext.md#KLocalizedQmlContext)()

## Method Documentation {#method-documentation}

### string i18n(message: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#i18n-method}

*See also* [KLocalizedString::i18n](../ki18n/klocalizedstring.md#i18n)()

### string i18nc(context: *string*, message: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#i18nc-method}

*See also* [KLocalizedString::i18nc](../ki18n/klocalizedstring.md#i18nc)()

### string i18ncp(context: *string*, singular: *string*, plural: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#i18ncp-method}

*See also* [KLocalizedString::i18ncp](../ki18n/klocalizedstring.md#i18ncp)()

### string i18nd(domain: *string*, message: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#i18nd-method}

*See also* [KLocalizedString::i18nd](../ki18n/klocalizedstring.md#i18nd)()

### string i18ndc(domain: *string*, context: *string*, message: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#i18ndc-method}

*See also* [KLocalizedString::i18ndc](../ki18n/klocalizedstring.md#i18ndc)()

### string i18ndcp(domain: *string*, context: *string*, singular: *string*, plural: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#i18ndcp-method}

*See also* [KLocalizedString::i18ndcp](../ki18n/klocalizedstring.md#i18ndcp)()

### string i18ndp(domain: *string*, singular: *string*, plural: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#i18ndp-method}

*See also* [KLocalizedString::i18ndp](../ki18n/klocalizedstring.md#i18ndp)()

### string i18np(singular: *string*, plural: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#i18np-method}

*See also* [KLocalizedString::i18np](../ki18n/klocalizedstring.md#i18np)()

### string xi18n(message: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#xi18n-method}

*See also* [KLocalizedString::xi18n](../ki18n/klocalizedstring.md#xi18n)()

### string xi18nc(context: *string*, message: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#xi18nc-method}

*See also* [KLocalizedString::xi18nc](../ki18n/klocalizedstring.md#xi18nc)()

### string xi18ncp(context: *string*, singular: *string*, plural: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#xi18ncp-method}

*See also* [KLocalizedString::xi18ncp](../ki18n/klocalizedstring.md#xi18ncp)()

### string xi18nd(domain: *string*, message: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#xi18nd-method}

*See also* [KLocalizedString::xi18nd](../ki18n/klocalizedstring.md#xi18nd)()

### string xi18ndc(domain: *string*, context: *string*, message: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#xi18ndc-method}

*See also* [KLocalizedString::xi18ndc](../ki18n/klocalizedstring.md#xi18ndc)()

### string xi18ndcp(domain: *string*, context: *string*, singular: *string*, plural: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#xi18ndcp-method}

*See also* [KLocalizedString::xi18ndcp](../ki18n/klocalizedstring.md#xi18ndcp)()

### string xi18ndp(domain: *string*, singular: *string*, plural: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#xi18ndp-method}

*See also* [KLocalizedString::xi18ndp](../ki18n/klocalizedstring.md#xi18ndp)()

### string xi18np(singular: *string*, plural: *string*, param1: *variant* = undefined, param2: *variant* = undefined, param3: *variant* = undefined, param4: *variant* = undefined, param5: *variant* = undefined, param6: *variant* = undefined, param7: *variant* = undefined, param8: *variant* = undefined, param9: *variant* = undefined, param10: *variant* = undefined) {#xi18np-method}

*See also* [KLocalizedString::xi18np](../ki18n/klocalizedstring.md#xi18np)()
