---
title: "KLocalization Namespace"
description: "Namespace containing helpers for localization. This namespace was introduced in Qt 6.5."
---

# KLocalization Namespace

Namespace containing helpers for localization. This namespace was introduced in Qt 6.5. [More...](#details)

- Header: KLocalization
- Since: Qt 6.5
- CMake: find\_package(KF6 REQUIRED COMPONENTS I18n) target\_link\_libraries(mytarget PRIVATE KF6::I18n)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### \[since 6.5\] template \<typename T\> void KLocalization::retranslateSpinBoxFormatString(T \**spinBox*) {#retranslateSpinBoxFormatString}

Retranslates a previously set up format string to the current language and updates the spin box.

The format string is initially set up by [setupSpinBoxFormatString](klocalization.md#setupSpinBoxFormatString)(). This function updates the prefix and suffix of a spin box to reflect the current language settings. It is useful for responding to language changes, such as those triggered by [QEvent::LanguageChange](https://doc.qt.io/qt-6/qevent.html#Type-enum).

`T` The type of the spin box, which must be either QSpinBox or QDoubleSpinBox.

`spinBox` Pointer to the spin box.

The prefix and suffix of the spin box are updated to reflect the current language.

This function was introduced in Qt 6.5.

*See also* [setupSpinBoxFormatString](klocalization.md#setupSpinBoxFormatString)

### \[since 6.5\] template \<typename T\> void KLocalization::setupSpinBoxFormatString(T \**spinBox*, const KLocalizedString &*formatString*) {#setupSpinBoxFormatString}

Sets up a format string for internationalizing spin boxes.

This function allows the customization of prefix and suffix for spin boxes (QSpinBox and QDoubleSpinBox), considering internationalization needs.

Spin boxes display a number and possibly a prefix and/or suffix. However, in some languages, the position of the prefix and suffix may be reversed compared to English. Example: In English, you write 50%, but in Turkish, you write %50. Qt does not offer an out-of-the-box solution for this. This helper now provides complete internationalization for prefixes and suffixes of spin boxes.

For QSpinBox it also provides correct plural handling by installing a handler for the valueChanged() signal to update prefix and suffix whenever the spin box value changes in the future.

Example usage:

```cpp
QDoubleSpinBox doubleBox;
KLocalization::setupSpinBoxFormatString(
    &doubleBox,
    ki18nc("@item %v is a number and the second % is the percent sign", "%v%"));
// Turkish translation: "%%v"

QSpinBox intBox;
KLocalization::setupSpinBoxFormatString(
    &intBox,
    ki18ncp("@item %v is a number", "Baking %v cake", "Baking %v cakes"));
```

`T` The type of the spin box, which must be either QSpinBox or QDoubleSpinBox.

`spinBox` Pointer to the spin box.

`formatString` A localized string in the format "PREFIX%vSUFFIX".

- For QDoubleSpinBox, plural forms in `formatString` are ignored and should be avoided. Use [KLocalizedString::ki18nc](klocalizedstring.md#ki18nc) "[ki18nc](klocalizedstring.md#ki18nc)()" to generate the format string.
- For QSpinBox, if `formatString` includes plural forms, they are utilized. While optional, their use is highly recommended for accurate pluralization. Use [KLocalizedString::ki18ncp](klocalizedstring.md#ki18ncp) "[ki18ncp](klocalizedstring.md#ki18ncp)()" to generate the format string.

It is safe to call this function multiple times on the same spin box.

This function was introduced in Qt 6.5.

*See also* [retranslateSpinBoxFormatString](klocalization.md#retranslateSpinBoxFormatString)
