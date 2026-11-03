---
title: "KLocalizedTranslator Class"
description: "A QTranslator using KLocalizedString for translations."
---

# KLocalizedTranslator Class

A [QTranslator](https://doc.qt.io/qt-6/qtranslator.html) using [KLocalizedString](klocalizedstring.md) for translations. [More...](#details)

- **Header:** `#include <KLocalizedTranslator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS I18n)`  
  `target_link_libraries(mytarget PRIVATE KF6::I18n)`
- **Inherits:** [QTranslator](https://doc.qt.io/qt-6/qtranslator.html)

[List of all members, including inherited members](klocalizedtranslator-members.md)

## Public Functions

- [KLocalizedTranslator(QObject \*parent = nullptr)](#KLocalizedTranslator)
- [void addContextToMonitor(const QString &context)](#addContextToMonitor)
- [void removeContextToMonitor(const QString &context)](#removeContextToMonitor)
- [void setTranslationDomain(const QString &translationDomain)](#setTranslationDomain)

## Detailed Description {#details}

This class allows to translate strings in Qt's translation system with [KLocalizedString](klocalizedstring.md). An example is the translation of a dynamically loaded user interface through QUILoader.

To use this Translator install it in the [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html) and provide the translation domain to be used. The Translator can operate for multiple contexts, those needs to be specified.

Example for translating a UI loaded through QUILoader:

```cpp
// create translator and install in QCoreApplication
KLocalizedTranslator *translator = new KLocalizedTranslator(this);
QCoreApplication::instance()->installTranslator(translator);
translator->setTranslationDomain(QStringLiteral("MyAppsDomain"));

// create the QUILoader
QUiLoader *loader = new QUiLoader(this);
loader->setLanguageChangeEnabled(true);

// load the UI
QFile uiFile(QStringLiteral("/path/to/userInterface.ui"));
uiFile.open(QFile::ReadOnly);
QWidget *loadedWidget = loader->load(&uiFile, this);
uiFile.close();

// the object name of the loaded UI is the context in this case
translator->addContextToMonitor(loadedWidget->objectName());

// send a LanguageChange event, this will re-translate using our translator
QEvent le(QEvent::LanguageChange);
QCoreApplication::sendEvent(loadedWidget, &le);
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KLocalizedTranslator::KLocalizedTranslator(QObject \**parent* = nullptr) {#KLocalizedTranslator}

### void KLocalizedTranslator::addContextToMonitor(const QString &*context*) {#addContextToMonitor}

Adds a `context` for which this Translator should be active.

The Translator only translates texts with a context matching one of the monitored contexts. If the context is not monitored, the [translate](https://doc.qt.io/qt-6/qtranslator.html#translate)() method delegates to the base class.

`context` The context for which the Translator should be active

*See also* [removeContextToMonitor](klocalizedtranslator.md#removeContextToMonitor)

### void KLocalizedTranslator::removeContextToMonitor(const QString &*context*) {#removeContextToMonitor}

Stop translating for the given `context`.

`context` The context for which the Translator should no longer be active

*See also* [addContextToMonitor](klocalizedtranslator.md#addContextToMonitor)

### void KLocalizedTranslator::setTranslationDomain(const QString &*translationDomain*) {#setTranslationDomain}

Sets the `translationDomain` to be used.

The translation domain is required. Without the translation domain any invocation of [translate](https://doc.qt.io/qt-6/qtranslator.html#translate)() will be delegated to the base class.

`translationDomain` The translation domain to be used.
