---
title: "KLazyLocalizedString Class"
description: "Lazy-initialized variant of KLocalizedString."
---

# KLazyLocalizedString Class

Lazy-initialized variant of [KLocalizedString](klocalizedstring.md). [More...](#details)

- **Header:** `#include <KLazyLocalizedString>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS I18n)`  
  `target_link_libraries(mytarget PRIVATE KF6::I18n)`

[List of all members, including inherited members](klazylocalizedstring-members.md)

## Public Functions

- [KLazyLocalizedString()](#KLazyLocalizedString)
- [KLocalizedString ignoreMarkup() const](#ignoreMarkup)
- [KLocalizedString inContext(const QString &key, const QString &value) const](#inContext)
- [bool isEmpty() const](#isEmpty)
- [KLocalizedString relaxSubs() const](#relaxSubs)
- [KLocalizedString subs(QChar a, int fieldWidth = 0, QChar fillChar = QLatin1Char(' ')) const](#subs)
- [KLocalizedString subs(const KLocalizedString &a, int fieldWidth = 0, QChar fillChar = QLatin1Char(' ')) const](#subs-1)
- [KLocalizedString subs(const QString &a, int fieldWidth = 0, QChar fillChar = QLatin1Char(' ')) const](#subs-2)
- [KLocalizedString subs(int a, int fieldWidth = 0, int base = 10, QChar fillChar = QLatin1Char(' ')) const](#subs-3)
- [KLocalizedString subs(long a, int fieldWidth = 0, int base = 10, QChar fillChar = QLatin1Char(' ')) const](#subs-4)
- [KLocalizedString subs(qlonglong a, int fieldWidth = 0, int base = 10, QChar fillChar = QLatin1Char(' ')) const](#subs-5)
- [KLocalizedString subs(qulonglong a, int fieldWidth = 0, int base = 10, QChar fillChar = QLatin1Char(' ')) const](#subs-6)
- [KLocalizedString subs(uint a, int fieldWidth = 0, int base = 10, QChar fillChar = QLatin1Char(' ')) const](#subs-7)
- [KLocalizedString subs(ulong a, int fieldWidth = 0, int base = 10, QChar fillChar = QLatin1Char(' ')) const](#subs-8)
- [KLocalizedString subs(double a, int fieldWidth = 0, char format = 'g', int precision = -1, QChar fillChar = QLatin1Char(' ')) const](#subs-9)
- [QString toString() const](#toString)
- [QString toString(Kuit::VisualFormat format) const](#toString-1)
- [QString toString(const QStringList &languages) const](#toString-2)
- [QString toString(const char \*domain) const](#toString-3)
- [const char \*untranslatedText() const](#untranslatedText)
- [KLocalizedString withDomain(const char \*domain) const](#withDomain)
- [KLocalizedString withFormat(Kuit::VisualFormat format) const](#withFormat)
- [KLocalizedString withLanguages(const QStringList &languages) const](#withLanguages)
- [KLazyLocalizedString::operator KLocalizedString() const](#operator-KLocalizedString)

## Detailed Description {#details}

This is a safer replacement for the I18N\_NOOP set of macros and allows marking strings for extraction without runtime-initializing [KLocalizedString](klocalizedstring.md) instances, for storing in static data tables.

Instances of [KLazyLocalizedString](klazylocalizedstring.md) are not created directly, unless they should be empty. Instead they have to be obtained via the kli18n\* functions (similar to [KLocalizedString](klocalizedstring.md) and the ki18n\* functions).

Example usage in a static message table:

```cpp
struct {
    MyClass::VehicleType type;
    KLazyLocalizedString msg;
} static constexpr const vehicle_msg_table[] = {
    { MyClass::Train, kli18np("%1 train", "%1 trains") },
    { MyClass::Bus, kli18ncp("the vehicle, not the USB one", "%1 bus", "%1 buses") },
    ...
};

...

const auto it = std::find_if(std::begin(vehicle_msg_table), std::end(vehicle_msg_table), [vehicleType](const auto &m) { return m.type == vehicleType; });
QString translatedMessage = (*it).msg.subs(vehicleCount).toString();
```

> **Note:** [KLazyLocalizedString](klazylocalizedstring.md) is primarily meant for storage in e.g. message tables, not for use in API, especially not across translation domains. This is due to it not carrying the translation domain in which it was created, but using the active translation domain at the point of converting to a [KLocalizedString](klocalizedstring.md).

## Member Function Documentation {#member-function-documentation}

### \[constexpr noexcept\] KLazyLocalizedString::KLazyLocalizedString() {#KLazyLocalizedString}

Construct an empty message.

Direct construction is used when e.g. a [KLazyLocalizedString](klazylocalizedstring.md) field in a data table needs to be set, but there is not message to be used. Directly constructed instances are not valid for finalization by [toString](klazylocalizedstring.md#toString) methods.

*See also* [isEmpty](klazylocalizedstring.md#isEmpty)

### KLocalizedString KLazyLocalizedString::ignoreMarkup() const {#ignoreMarkup}

Do not resolve KUIT markup.

If the message is markup-aware (constructed by one of xi18n calls), this function can be used to make it non-markup-aware. This may be useful for debugging markup.

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::inContext(const QString &*key*, const QString &*value*) const {#inContext}

Add dynamic context to the message.

See dyn\_ctxt for use cases.

`key` context key

`value` context value

Returns updated [KLocalizedString](klocalizedstring.md)

### \[constexpr\] bool KLazyLocalizedString::isEmpty() const {#isEmpty}

Check whether the message is empty.

The message is considered empty if the object was constructed via the default constructor.

Empty messages are not valid for finalization. The behavior of calling [toString](klazylocalizedstring.md#toString)() on them is undefined. In debug mode, an error mark may appear in the returned string.

Returns `true` if the message is empty, `false` otherwise

### KLocalizedString KLazyLocalizedString::relaxSubs() const {#relaxSubs}

Relax matching between placeholders and arguments.

Normally the placeholders should start from %1 and have no gaps, and on finalization there must be exactly as many arguments supplied through subs methods as there are unique plaecholders. If this is not satisfied, in debug mode warnings are printed and the finalized string may contain error marks.

This method relaxes the placeholder-argument matching, such that there must only be an argument available for every present unique placeholder (taking placeholder numbers to be 1-based indices into the argument list). This can come useful in some situations.

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::subs(QChar *a*, int *fieldWidth* = 0, QChar *fillChar* = QLatin1Char(' ')) const {#subs}

Substitute a [QChar](https://doc.qt.io/qt-6/qchar.html) argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::subs(const KLocalizedString &*a*, int *fieldWidth* = 0, QChar *fillChar* = QLatin1Char(' ')) const {#subs-1}

Substitute another [KLocalizedString](klocalizedstring.md) into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::subs(const QString &*a*, int *fieldWidth* = 0, QChar *fillChar* = QLatin1Char(' ')) const {#subs-2}

Substitute a [QString](https://doc.qt.io/qt-6/qstring.html) argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::subs(int *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-3}

Substitute an int argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::subs(long *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-4}

Substitute a long argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::subs(qlonglong *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-5}

Substitute a long long argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::subs(qulonglong *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-6}

Substitute an unsigned long long argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::subs(uint *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-7}

Substitute an unsigned int argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::subs(ulong *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-8}

Substitute an unsigned long argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::subs(double *a*, int *fieldWidth* = 0, char *format* = 'g', int *precision* = -1, QChar *fillChar* = QLatin1Char(' ')) const {#subs-9}

Substitute a double argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`format` type of floating point formatting, like in [QString::arg](https://doc.qt.io/qt-6/qstring.html#arg)

`precision` number of digits after the decimal separator

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### QString KLazyLocalizedString::toString() const {#toString}

Finalize the translation.

Creates translated [QString](https://doc.qt.io/qt-6/qstring.html). If the string has placeholders, make sure to call instead [KLazyLocalizedString::subs](klazylocalizedstring.md#subs) and further [KLocalizedString::subs](klocalizedstring.md#subs) methods before finalizing. Translated text is searched for based on the global locale.

Returns finalized translation

### QString KLazyLocalizedString::toString(Kuit::VisualFormat *format*) const {#toString-1}

Like [toString](klazylocalizedstring.md#toString)(), but resolve KUIT markup into given visual format.

Given visual format overrides that implied by the context UI marker. If the message is not markup-aware, this is same as [toString](klazylocalizedstring.md#toString)().

`format` the target visual format

Returns finalized translation

### QString KLazyLocalizedString::toString(const QStringList &*languages*) const {#toString-2}

Like [toString](klazylocalizedstring.md#toString)(), but look for translation only in given languages.

Given languages override languages defined by the global locale. If `languages` is empty, original message is returned.

`languages` list of language codes (by decreasing priority) Returns finalized translation

### QString KLazyLocalizedString::toString(const char \**domain*) const {#toString-3}

Like [toString](klazylocalizedstring.md#toString)(), but look for translation in the given domain.

`domain` the translation domain

Returns finalized translation

### \[constexpr\] const char \*KLazyLocalizedString::untranslatedText() const {#untranslatedText}

Returns the raw untranslated text as passed to `kli18n*`.

### KLocalizedString KLazyLocalizedString::withDomain(const char \**domain*) const {#withDomain}

Indicate to look for translation in the given domain.

`domain` the translation domain

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::withFormat(Kuit::VisualFormat *format*) const {#withFormat}

Indicate to resolve KUIT markup into given visual format.

If the message is not markup-aware, this has no effect.

`format` the target visual format

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLazyLocalizedString::withLanguages(const QStringList &*languages*) const {#withLanguages}

Indicate to look for translation only in given languages.

`languages` list of language codes (by decreasing priority)

Returns updated [KLocalizedString](klocalizedstring.md)

### KLazyLocalizedString::operator KLocalizedString() const {#operator-KLocalizedString}

Convert to a [KLocalizedString](klocalizedstring.md) to actually perform the translation and obtain a concrete localized string.

The translation domain active at this point will be used. This means this has to be called in the same translation domain the corresponding kli18n call is in.

## Related Non-Members {#related-non-members}

### KLazyLocalizedString kli18n(const char \**text*) {#kli18n}

Mark the string `text` for extraction.

`text` string to translate

Returns [KLazyLocalizedString](klazylocalizedstring.md) for deferred translation.

### KLazyLocalizedString kli18nc(const char \**context*, const char \**text*) {#kli18nc}

Mark the string `text` with `context` for extraction.

`context` context of the string

`text` string to translate

Returns [KLazyLocalizedString](klazylocalizedstring.md) for deferred translation.

### KLazyLocalizedString kli18ncp(const char \**context*, const char \**singular*, const char \**plural*) {#kli18ncp}

Mark the string `singular` and `plural` with `context` for extraction.

`context` context of the string

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns [KLazyLocalizedString](klazylocalizedstring.md) for deferred translation.

### KLazyLocalizedString kli18np(const char \**singular*, const char \**plural*) {#kli18np}

Mark the string `singular` and `plural` for extraction.

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns [KLazyLocalizedString](klazylocalizedstring.md) for deferred translation.

### KLazyLocalizedString klxi18n(const char \**text*) {#klxi18n}

Mark the markup-aware string `text` for extraction.

`text` string to translate

Returns [KLazyLocalizedString](klazylocalizedstring.md) for deferred translation.

### KLazyLocalizedString klxi18nc(const char \**context*, const char \**text*) {#klxi18nc}

Mark the markup-aware string `text` with `context` for extraction.

`context` context of the string

`text` string to translate

Returns [KLazyLocalizedString](klazylocalizedstring.md) for deferred translation.

### KLazyLocalizedString klxi18ncp(const char \**context*, const char \**singular*, const char \**plural*) {#klxi18ncp}

Mark the markup-aware string `singular` and `plural` with `context` for extraction.

`context` context of the string

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns [KLazyLocalizedString](klazylocalizedstring.md) for deferred translation.

### KLazyLocalizedString klxi18np(const char \**singular*, const char \**plural*) {#klxi18np}

Mark the markup-aware string `singular` and `plural` for extraction.

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns [KLazyLocalizedString](klazylocalizedstring.md) for deferred translation.
