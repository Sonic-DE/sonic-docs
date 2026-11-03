---
title: "KLocalizedString Class"
description: "Class for producing and handling localized messages."
---

# KLocalizedString Class

Class for producing and handling localized messages. [More...](#details)

- **Header:** `#include <KLocalizedString>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS I18n)`  
  `target_link_libraries(mytarget PRIVATE KF6::I18n)`

[List of all members, including inherited members](klocalizedstring-members.md)

## Public Functions

- [KLocalizedString()](#KLocalizedString)
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
- [QByteArray untranslatedText() const](#untranslatedText)
- [KLocalizedString withDomain(const char \*domain) const](#withDomain)
- [KLocalizedString withFormat(Kuit::VisualFormat format) const](#withFormat)
- [KLocalizedString withLanguages(const QStringList &languages) const](#withLanguages)

## Static Public Members

- [void addDomainLocaleDir(const QByteArray &domain, const QString &path)](#addDomainLocaleDir)
- [QByteArray applicationDomain()](#applicationDomain)
- [QSet\<QString\> availableApplicationTranslations()](#availableApplicationTranslations)
- [QSet\<QString\> availableDomainTranslations(const QByteArray &domain)](#availableDomainTranslations)
- [void clearLanguages()](#clearLanguages)
- [bool isApplicationTranslatedInto(const QString &language)](#isApplicationTranslatedInto)
- [QStringList languages()](#languages)
- [QString localizedFilePath(const QString &filePath)](#localizedFilePath)
- [QString removeAcceleratorMarker(const QString &label)](#removeAcceleratorMarker)
- [void setApplicationDomain(const QByteArray &domain)](#setApplicationDomain)
- [void setLanguages(const QStringList &languages)](#setLanguages)

## Detailed Description {#details}

[KLocalizedString](klocalizedstring.md) handles translation and argument substitution and formatting of user-visible text.

[KLocalizedString](klocalizedstring.md) instances are usually not constructed directly, but through one of the wrapper \*i18n\* calls.

For detailed information on how to use KI18n functions please refer to the [Programmer's Guide](https://invent.kde.org/frameworks/ki18n/-/blob/master/docs/programmers-guide.md)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KLocalizedString::KLocalizedString() {#KLocalizedString}

Construct an empty message.

Direct construction is used when another [KLocalizedString](klocalizedstring.md) instance, obtained by one of ki18n\* calls, should later be assigned to directly constructed instance. Before the assignment happens, directly constructed instance is not valid for finalization by [toString](klocalizedstring.md#toString) methods.

*See also* [isEmpty](klocalizedstring.md#isEmpty)

### \[static\] void KLocalizedString::addDomainLocaleDir(const QByteArray &*domain*, const QString &*path*) {#addDomainLocaleDir}

Load locales for a domain from a specific location This is useful for resources which have their translation files outside of the usual $XDG\_DATA\_DIRS/locales location

`domain` the domain to load resources from

`path` the full file path to the locale directory

### \[static\] QByteArray KLocalizedString::applicationDomain() {#applicationDomain}

Get the application's main translation domain.

Returns the domain set by [setApplicationDomain](klocalizedstring.md#setApplicationDomain).

*See also* [setApplicationDomain](klocalizedstring.md#setApplicationDomain)()

### \[static\] QSet\<QString\> KLocalizedString::availableApplicationTranslations() {#availableApplicationTranslations}

Get the languages for which there exists the translation catalog file for the set application translation domain.

The application domain is set by [setApplicationDomain](klocalizedstring.md#setApplicationDomain). If the application domain was not set, empty set is returned. If the application domain was set, the language set will always contain at least the source code language (en\_US).

Returns set of language codes for existing translation catalogs

*See also* [setApplicationDomain](klocalizedstring.md#setApplicationDomain)

### \[static\] QSet\<QString\> KLocalizedString::availableDomainTranslations(const QByteArray &*domain*) {#availableDomainTranslations}

Get the languages for which a translation catalog file for the passed translation domain exists.

If the translation domain was not specified in the domain parameter an empty set is returned.

If the application domain was set, the language set will always contain at least the source code language (en\_US).

`domain` query for translations of a specific domain, if an empty [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) is passed, an empty set will be returned

Returns set of language codes for existing translation catalogs

*See also* [setApplicationDomain](klocalizedstring.md#setApplicationDomain), [availableApplicationTranslations](klocalizedstring.md#availableApplicationTranslations)

### \[static\] void KLocalizedString::clearLanguages() {#clearLanguages}

Clear override languages.

This clears the override languages, going back to those provided by the locale.

*See also* [setLanguages](klocalizedstring.md#setLanguages), [languages](klocalizedstring.md#languages)

### KLocalizedString KLocalizedString::ignoreMarkup() const {#ignoreMarkup}

Do not resolve KUIT markup.

If the message is markup-aware (constructed by one of \*xi18n\* calls), this function can be used to make it non-markup-aware. This may be useful for debugging markup.

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::inContext(const QString &*key*, const QString &*value*) const {#inContext}

Add dynamic context to the message.

See dyn\_ctxt for use cases.

`key` context key

`value` context value

Returns updated [KLocalizedString](klocalizedstring.md)

### \[static\] bool KLocalizedString::isApplicationTranslatedInto(const QString &*language*) {#isApplicationTranslatedInto}

Check whether the translation catalog file in the given language for the set application translation domain exists.

`language` the language code to check

Returns `true` if the translation catalog for `language` exits, `false` otherwise

*See also* [setApplicationDomain](klocalizedstring.md#setApplicationDomain)

### bool KLocalizedString::isEmpty() const {#isEmpty}

Check whether the message is empty.

The message is considered empty if the object was constructed via the default constructor.

Empty messages are not valid for finalization. The behavior of calling [toString](klocalizedstring.md#toString) on them is undefined. In debug mode, an error mark may appear in the returned string.

Returns `true` if the message is empty, `false` otherwise

### \[static\] QStringList KLocalizedString::languages() {#languages}

Get the languages for which translations will be made.

Returned languages are ordered with decreasing priority.

Returns languages ordered list of language codes

*See also* [setLanguages](klocalizedstring.md#setLanguages), [clearLanguages](klocalizedstring.md#clearLanguages)

### \[static\] QString KLocalizedString::localizedFilePath(const QString &*filePath*) {#localizedFilePath}

Find a path to the localized file for the given original path.

This is intended mainly for non-text resources (images, sounds, etc). Text resources should be handled in more specific ways.

Possible localized paths are checked in turn by priority of set languages, in form of \<dirname\>/l10n/\<lang\>/\<basename\>, where \<dirname\> and \<basename\> are those of the original path, and \<lang\> is the language code.

`filePath` path to the original file

Returns path to the localized file if found, original path otherwise

### KLocalizedString KLocalizedString::relaxSubs() const {#relaxSubs}

Relax matching between placeholders and arguments.

Normally the placeholders should start from %1 and have no gaps, and on finalization there must be exactly as many arguments supplied through subs methods as there are unique plaecholders. If this is not satisfied, in debug mode warnings are printed and the finalized string may contain error marks.

This method relaxes the placeholder-argument matching, such that there must only be an argument available for every present unique placeholder (taking placeholder numbers to be 1-based indices into the argument list). This can come useful in some situations.

Returns updated [KLocalizedString](klocalizedstring.md)

### \[static\] QString KLocalizedString::removeAcceleratorMarker(const QString &*label*) {#removeAcceleratorMarker}

Remove accelerator marker from a UI text label.

Accelerator marker is not always a plain ampersand (&), so it is not enough to just remove it by [QString::remove](https://doc.qt.io/qt-6/qstring.html#remove). The label may contain escaped markers ("&&") which must be resolved and skipped, as well as CJK-style markers ("Foo (&F)") where the whole parenthesis construct should be removed. Therefore always use this function to remove accelerator marker from UI labels.

`label` UI label which may contain an accelerator marker

Returns label without the accelerator marker

### \[static\] void KLocalizedString::setApplicationDomain(const QByteArray &*domain*) {#setApplicationDomain}

Set the given domain as application's main domain.

This function must be called in applications, in order to have any translations at all. It should never be called in libraries. This allows to check whether the application is translated into a given language, so that if it is not, translations from underlying libraries will not appear even if they are translated. This prevents mixing of translated and untranslated text in the user interface.

This function should be called right after creating the instance of [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html) or one of its subclasses. At that time the locale setup has been made, including what is hooked into the [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html) startup, like KXMLGUI's language switching support. So the initialisation done by this function sees all the data it should.

`domain` the translation domain of the application

*See also* [applicationDomain](klocalizedstring.md#applicationDomain)()

### \[static\] void KLocalizedString::setLanguages(const QStringList &*languages*) {#setLanguages}

Set the languages for which translations will be made.

This overrides the languages provided by the locale. Languages should be ordered with decreasing priority.

`languages` ordered list of language codes

*See also* setLocale, [clearLanguages](klocalizedstring.md#clearLanguages), [languages](klocalizedstring.md#languages)

### KLocalizedString KLocalizedString::subs(QChar *a*, int *fieldWidth* = 0, QChar *fillChar* = QLatin1Char(' ')) const {#subs}

Substitute a [QChar](https://doc.qt.io/qt-6/qchar.html) argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::subs(const KLocalizedString &*a*, int *fieldWidth* = 0, QChar *fillChar* = QLatin1Char(' ')) const {#subs-1}

Substitute another [KLocalizedString](klocalizedstring.md) into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::subs(const QString &*a*, int *fieldWidth* = 0, QChar *fillChar* = QLatin1Char(' ')) const {#subs-2}

Substitute a [QString](https://doc.qt.io/qt-6/qstring.html) argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::subs(int *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-3}

Substitute an int argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::subs(long *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-4}

Substitute a long argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::subs(qlonglong *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-5}

Substitute a long long argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::subs(qulonglong *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-6}

Substitute an unsigned long long argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::subs(uint *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-7}

Substitute an unsigned int argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::subs(ulong *a*, int *fieldWidth* = 0, int *base* = 10, QChar *fillChar* = QLatin1Char(' ')) const {#subs-8}

Substitute an unsigned long argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`base` the radix used to represent the number as a string. Valid values range from 2 to 36

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::subs(double *a*, int *fieldWidth* = 0, char *format* = 'g', int *precision* = -1, QChar *fillChar* = QLatin1Char(' ')) const {#subs-9}

Substitute a double argument into the message.

`a` the argument

`fieldWidth` width of the formatted field, padded by spaces. Positive value aligns right, negative aligns left

`format` type of floating point formatting, like in [QString::arg](https://doc.qt.io/qt-6/qstring.html#arg)

`precision` number of digits after the decimal separator

`fillChar` the character used to fill up the empty places when field width is greater than argument width

Returns updated [KLocalizedString](klocalizedstring.md)

### QString KLocalizedString::toString() const {#toString}

Finalize the translation.

Creates translated [QString](https://doc.qt.io/qt-6/qstring.html), with placeholders substituted by arguments given by [KLocalizedString::subs](klocalizedstring.md#subs) methods. Translated text is searched for and arguments are formatted based on the global locale.

If there was any mismatch between placeholders and arguments, in debug mode the returned string may contain error marks.

Returns finalized translation

### QString KLocalizedString::toString(Kuit::VisualFormat *format*) const {#toString-1}

Like [toString](klocalizedstring.md#toString), but resolve KUIT markup into given visual format.

Given visual format overrides that implied by the context UI marker or set earlier using [withFormat](klocalizedstring.md#withFormat). If the message is not markup-aware, this is same as [toString](klocalizedstring.md#toString) without arguments.

`format` the target visual format

Returns finalized translation

### QString KLocalizedString::toString(const QStringList &*languages*) const {#toString-2}

Like [toString](klocalizedstring.md#toString), but look for translation only in given languages.

Given languages override languages defined by the global locale, and any languages set earlier using [withLanguages](klocalizedstring.md#withLanguages). If `languages` is empty, original message is returned.

`languages` list of language codes (by decreasing priority) Returns finalized translation

### QString KLocalizedString::toString(const char \**domain*) const {#toString-3}

Like [toString](klocalizedstring.md#toString), but look for translation in the given domain.

Given domain overrides any set earlier using [withDomain](klocalizedstring.md#withDomain).

`domain` the translation domain

Returns finalized translation

### QByteArray KLocalizedString::untranslatedText() const {#untranslatedText}

Returns the untranslated text.

### KLocalizedString KLocalizedString::withDomain(const char \**domain*) const {#withDomain}

Indicate to look for translation in the given domain.

`domain` the translation domain Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::withFormat(Kuit::VisualFormat *format*) const {#withFormat}

Indicate to resolve KUIT markup into given visual format.

If the message is not markup-aware, this has no effect.

`format` the target visual format

Returns updated [KLocalizedString](klocalizedstring.md)

### KLocalizedString KLocalizedString::withLanguages(const QStringList &*languages*) const {#withLanguages}

Indicate to look for translation only in given languages.

`languages` list of language codes (by decreasing priority)

Returns updated [KLocalizedString](klocalizedstring.md)

## Related Non-Members {#related-non-members}

### QString i18n(const char \**text*, const int &*arg*, *...*) {#i18n}

Translate a string and substitute any arguments.

`text` string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString i18nc(const char \**context*, const char \**text*, const int &*arg*, *...*) {#i18nc}

Translate a string with context and substitute any arguments.

`context` context of the string

`text` string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString i18ncp(const char \**context*, const char \**singular*, const char \**plural*, const int &*arg*, *...*) {#i18ncp}

Translate a string with context and plural and substitute any arguments.

`context` context of the string

`singular` singular form of the string to translate

`plural` plural form of the string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString i18nd(const char \**domain*, const char \**text*, const int &*arg*, *...*) {#i18nd}

Translate a string from domain and substitute any arguments.

`domain` domain in which to look for translations

`text` string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString i18ndc(const char \**domain*, const char \**context*, const char \**text*, const int &*arg*, *...*) {#i18ndc}

Translate a string from domain with context and substitute any arguments.

`domain` domain in which to look for translations

`context` context of the string

`text` string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString i18ndcp(const char \**domain*, const char \**context*, const char \**singular*, const char \**plural*, const int &*arg*, *...*) {#i18ndcp}

Translate a string from domain with context and plural and substitute any arguments.

`domain` domain in which to look for translations

`context` context of the string

`singular` singular form of the string to translate

`plural` plural form of the string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString i18ndp(const char \**domain*, const char \**singular*, const char \**plural*, const int &*arg*, *...*) {#i18ndp}

Translate a string from domain with plural and substitute any arguments.

`domain` domain in which to look for translations

`singular` singular form of the string to translate

`plural` plural form of the string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString i18np(const char \**singular*, const char \**plural*, const int &*arg*, *...*) {#i18np}

Translate a string with plural and substitute any arguments.

`singular` singular form of the string to translate

`plural` plural form of the string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### KLocalizedString ki18n(const char \**text*) {#ki18n}

Create non-finalized translated string.

`text` string to translate

Returns non-finalized translated string

### KLocalizedString ki18nc(const char \**context*, const char \**text*) {#ki18nc}

Create non-finalized translated string with context.

`context` context of the string

`text` string to translate

Returns non-finalized translated string

### KLocalizedString ki18ncp(const char \**context*, const char \**singular*, const char \**plural*) {#ki18ncp}

Create non-finalized translated string with context and plural.

`context` context of the string

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns non-finalized translated string

### KLocalizedString ki18nd(const char \**domain*, const char \**text*) {#ki18nd}

Create non-finalized translated string from domain.

`domain` domain in which to look for translations

`text` string to translate

Returns non-finalized translated string

### KLocalizedString ki18ndc(const char \**domain*, const char \**context*, const char \**text*) {#ki18ndc}

Create non-finalized translated string from domain with context.

`domain` domain in which to look for translations

`context` context of the string

`text` string to translate

Returns non-finalized translated string

### KLocalizedString ki18ndcp(const char \**domain*, const char \**context*, const char \**singular*, const char \**plural*) {#ki18ndcp}

Create non-finalized translated string from domain with context and plural.

`domain` domain in which to look for translations

`context` context of the string

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns non-finalized translated string

### KLocalizedString ki18ndp(const char \**domain*, const char \**singular*, const char \**plural*) {#ki18ndp}

Create non-finalized translated string from domain with plural.

`domain` domain in which to look for translations

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns non-finalized translated string

### KLocalizedString ki18np(const char \**singular*, const char \**plural*) {#ki18np}

Create non-finalized translated string with plural.

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns non-finalized translated string

### KLocalizedString kxi18n(const char \**text*) {#kxi18n}

Create non-finalized markup-aware translated string.

`text` string to translate

Returns non-finalized translated string

### KLocalizedString kxi18nc(const char \**context*, const char \**text*) {#kxi18nc}

Create non-finalized markup-aware translated string with context.

`context` context of the string

`text` string to translate

Returns non-finalized translated string

### KLocalizedString kxi18ncp(const char \**context*, const char \**singular*, const char \**plural*) {#kxi18ncp}

Create non-finalized markup-aware translated string. with context and plural.

`context` context of the string

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns non-finalized translated string

### KLocalizedString kxi18nd(const char \**domain*, const char \**text*) {#kxi18nd}

Create non-finalized markup-aware translated string from domain.

`domain` domain in which to look for translations

`text` string to translate

Returns non-finalized translated string

### KLocalizedString kxi18ndc(const char \**domain*, const char \**context*, const char \**text*) {#kxi18ndc}

Create non-finalized markup-aware translated string from domain with context.

`domain` domain in which to look for translations

`context` context of the string

`text` string to translate

Returns non-finalized translated string

### KLocalizedString kxi18ndcp(const char \**domain*, const char \**context*, const char \**singular*, const char \**plural*) {#kxi18ndcp}

Create non-finalized markup-aware translated string from domain with context and plural.

`domain` domain in which to look for translations

`context` context of the string

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns non-finalized translated string

### KLocalizedString kxi18ndp(const char \**domain*, const char \**singular*, const char \**plural*) {#kxi18ndp}

Create non-finalized markup-aware translated string from domain with plural.

`domain` domain in which to look for translations

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns non-finalized translated string

### KLocalizedString kxi18np(const char \**singular*, const char \**plural*) {#kxi18np}

Create non-finalized markup-aware translated string with plural.

`singular` singular form of the string to translate

`plural` plural form of the string to translate

Returns non-finalized translated string

### QString tr2i18n(const char \**text*, const char \**comment* = nullptr) {#tr2i18n}

Redirect Qt's uic-generated translation calls to Ki18n.

Use -tr tr2i18n option to uic to have it redirect calls.

`text` string to translate

`comment` Qt equivalent of disambiguation context

Returns translated string

### QString tr2i18nd(const char \**domain*, const char \**text*, const char \**comment* = nullptr) {#tr2i18nd}

Like tr2i18n, but look for translation in a specific domain.

Use -tr tr2i18nd option to uic to have it redirect calls.

`domain` domain in which to look for translations

`text` string to translate

`comment` Qt equivalent of disambiguation context

Returns translated string

### QString tr2xi18n(const char \**text*, const char \**comment* = nullptr) {#tr2xi18n}

Like tr2i18n, but when UI strings are KUIT markup-aware.

Use -tr tr2xi18n option to uic to have it redirect calls.

`text` markup-aware string to translate

`comment` Qt equivalent of disambiguation context

Returns translated string

### QString tr2xi18nd(const char \**domain*, const char \**text*, const char \**comment* = nullptr) {#tr2xi18nd}

Like tr2xi18n, but look for translation in a specific domain.

Use -tr tr2xi18nd option to uic to have it redirect calls.

`domain` domain in which to look for translations

`text` markup-aware string to translate

`comment` Qt equivalent of disambiguation context

Returns translated string

### QString xi18n(const char \**text*, const int &*arg*, *...*) {#xi18n}

Translate a markup-aware string and substitute any arguments.

`text` string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString xi18nc(const char \**context*, const char \**text*, const int &*arg*, *...*) {#xi18nc}

Translate a markup-aware string with context and substitute any arguments.

`context` context of the string

`text` string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString xi18ncp(const char \**context*, const char \**singular*, const char \**plural*, const int &*arg*, *...*) {#xi18ncp}

Translate a markup-aware string with context and plural and substitute any arguments.

`context` context of the string

`singular` singular form of the string to translate

`plural` plural form of the string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString xi18nd(const char \**domain*, const char \**text*, const int &*arg*, *...*) {#xi18nd}

Translate a markup-aware string from domain and substitute any arguments.

`domain` domain in which to look for translations

`text` string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString xi18ndc(const char \**domain*, const char \**context*, const char \**text*, const int &*arg*, *...*) {#xi18ndc}

Translate a markup-aware string from domain with context and substitute any arguments.

`domain` domain in which to look for translations

`context` context of the string

`text` string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString xi18ndcp(const char \**domain*, const char \**context*, const char \**singular*, const char \**plural*, const int &*arg*, *...*) {#xi18ndcp}

Translate a markup-aware string from domain with context and plural and substitute any arguments.

`domain` domain in which to look for translations

`context` context of the string

`singular` singular form of the string to translate

`plural` plural form of the string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString xi18ndp(const char \**domain*, const char \**singular*, const char \**plural*, const int &*arg*, *...*) {#xi18ndp}

Translate a markup-aware string from domain with plural and substitute any arguments.

`domain` domain in which to look for translations

`singular` singular form of the string to translate

`plural` plural form of the string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string

### QString xi18np(const char \**singular*, const char \**plural*, const int &*arg*, *...*) {#xi18np}

Translate a markup-aware string with plural and substitute any arguments.

`singular` singular form of the string to translate

`plural` plural form of the string to translate

`arg` arguments to insert (0 to 9), admissible types according to [KLocalizedString::subs](klocalizedstring.md#subs) methods

Returns translated string
