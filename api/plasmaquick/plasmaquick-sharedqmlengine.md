---
title: "PlasmaQuick::SharedQmlEngine Class"
description: "An object that instantiates an entire QML context, with its own declarative engine. This class was introduced in Qt 6.0."
---

# PlasmaQuick::SharedQmlEngine Class

An object that instantiates an entire QML context, with its own declarative engine. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <SharedQmlEngine>`
- **Since:** Qt 6.0
- **CMake:** `find_package(PlasmaQuick REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::PlasmaQuick)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](plasmaquick-sharedqmlengine-members.md)

## Public Functions

- [SharedQmlEngine(QObject \*parent = nullptr)](#SharedQmlEngine)
- [QObject \*createObjectFromComponent(QQmlComponent \*component, QQmlContext \*context = nullptr, const QVariantHash &initialProperties = QVariantHash())](#createObjectFromComponent)
- [QObject \*createObjectFromSource(const QUrl &source, QQmlContext \*context = nullptr, const QVariantHash &initialProperties = QVariantHash())](#createObjectFromSource)
- [std::shared\_ptr\<QQmlEngine\> engine()](#engine)
- [bool isInitializationDelayed() const](#isInitializationDelayed)
- [QQmlComponent \*mainComponent() const](#mainComponent)
- [QQmlContext \*rootContext() const](#rootContext)
- [QObject \*rootObject() const](#rootObject)
- [void setInitializationDelayed(const bool delay)](#setInitializationDelayed)
- [void setSource(const QUrl &source)](#setSource)
- [void setSourceFromModule(QAnyStringView module, QAnyStringView type)](#setSourceFromModule)
- [void setTranslationDomain(const QString &translationDomain)](#setTranslationDomain)
- [QUrl source() const](#source)
- [QQmlComponent::Status status() const](#status)
- [QString translationDomain() const](#translationDomain)

## Public Slots

- [void completeInitialization(const QVariantHash &initialProperties = QVariantHash())](#completeInitialization)

## Signals

- [void finished()](#finished)

## Detailed Description {#details}

[PlasmaQuick::SharedQmlEngine](plasmaquick-sharedqmlengine.md) provides a class to conveniently use QML based declarative user interfaces. A [SharedQmlEngine](plasmaquick-sharedqmlengine.md) corresponds to one QML file (which can include others). It will a shared QQmlEngine with a single root object, described in the QML file.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] SharedQmlEngine::SharedQmlEngine(QObject \**parent* = nullptr) {#SharedQmlEngine}

Construct a new [PlasmaQuick::SharedQmlEngine](plasmaquick-sharedqmlengine.md)

`parent` The [QObject](https://doc.qt.io/qt-6/qobject.html) parent for this object.

### \[slot\] void SharedQmlEngine::completeInitialization(const QVariantHash &*initialProperties* = QVariantHash()) {#completeInitialization}

Finishes the process of initialization. If [isInitializationDelayed](plasmaquick-sharedqmlengine.md#isInitializationDelayed)() is false, calling this will have no effect.

`initialProperties` optional properties that will be set on the object when created (and before Component.onCompleted gets emitted

### QObject \*SharedQmlEngine::createObjectFromComponent(QQmlComponent \**component*, QQmlContext \**context* = nullptr, const QVariantHash &*initialProperties* = QVariantHash()) {#createObjectFromComponent}

Creates and returns an object based on the provided QQmlComponent with the same QQmlEngine and the same root context as the admin object, that will be the parent of the newly created object

`component` the component we want to instantiate

`context` The QQmlContext in which we will create the object, if 0 it will use the engine's root context

`initialProperties` optional properties that will be set on the object when created (and before Component.onCompleted gets emitted

### QObject \*SharedQmlEngine::createObjectFromSource(const QUrl &*source*, QQmlContext \**context* = nullptr, const QVariantHash &*initialProperties* = QVariantHash()) {#createObjectFromSource}

Creates and returns an object based on the provided url to a Qml file with the same QQmlEngine and the same root context as the main object, that will be the parent of the newly created object

`source` Url where the QML file is located

`context` The QQmlContext in which we will create the object, if 0 it will use the engine's root context.

`initialProperties` Optional properties that will be set on the object when created (and before Component.onCompleted gets emitted

### std::shared\_ptr\<QQmlEngine\> SharedQmlEngine::engine() {#engine}

Returns the declarative engine that runs the qml file assigned to this widget.

### \[signal\] void SharedQmlEngine::finished() {#finished}

Emitted when the parsing and execution of the QML file is terminated

### bool SharedQmlEngine::isInitializationDelayed() const {#isInitializationDelayed}

Returns `true` if the initialization of the QML file will be delayed at the end of the event loop

> **Note:** Getter function for property initializationDelayed.

### QQmlComponent \*SharedQmlEngine::mainComponent() const {#mainComponent}

Returns the main QQmlComponent of the engine

### QQmlContext \*SharedQmlEngine::rootContext() const {#rootContext}

The components's creation context.

### QObject \*SharedQmlEngine::rootObject() const {#rootObject}

Returns the root object of the declarative object tree

> **Note:** Getter function for property rootObject.

### void SharedQmlEngine::setInitializationDelayed(const bool *delay*) {#setInitializationDelayed}

Sets whether the execution of the QML file has to be delayed later in the event loop. It has to be called before setQmlPath().

In this case it will be possible to assign new objects in the main engine context before the main component gets initialized. In that case it will be possible to access it immediately from the QML code. The initialization will either be completed automatically asynchronously or explicitly by calling [completeInitialization](plasmaquick-sharedqmlengine.md#completeInitialization)()

`delay` If true the initialization of the QML file will be delayed at the end of the event loop

> **Note:** Setter function for property initializationDelayed.

*See also* [isInitializationDelayed](plasmaquick-sharedqmlengine.md#isInitializationDelayed)()

### void SharedQmlEngine::setSource(const QUrl &*source*) {#setSource}

Sets the path of the QML file to parse and execute

`source` The absolute path of a QML file

> **Note:** Setter function for property source.

*See also* [source](plasmaquick-sharedqmlengine.md#source)()

### void SharedQmlEngine::setSourceFromModule(QAnyStringView *module*, QAnyStringView *type*) {#setSourceFromModule}

Sets the QML source to execute from a type in a module.

`module` The module to load the type from.

`type` The type to load from the module.

### void SharedQmlEngine::setTranslationDomain(const QString &*translationDomain*) {#setTranslationDomain}

Call this method before calling setupBindings to install a translation domain for all i18n global functions. If a translation domain is set all i18n calls delegate to the matching i18nd calls with the provided translation domain.

The [translationDomain](plasmaquick-sharedqmlengine.md#translationDomain) affects all i18n calls including those from imports. Because of that modules intended to be used as imports should prefer the i18nd variants and set the translation domain explicitly in each call.

This method is only required if your declarative usage is inside a library. If it's in an application there is no need to set the translation domain as the application's domain can be used.

`translationDomain` The translation domain to be used for i18n calls.

> **Note:** Setter function for property translationDomain.

*See also* [translationDomain](plasmaquick-sharedqmlengine.md#translationDomain)()

### QUrl SharedQmlEngine::source() const {#source}

Returns the absolute path of the current QML file

> **Note:** Getter function for property source.

*See also* [setSource](plasmaquick-sharedqmlengine.md#setSource)()

### QQmlComponent::Status SharedQmlEngine::status() const {#status}

The component's current status.

> **Note:** Getter function for property status.

### QString SharedQmlEngine::translationDomain() const {#translationDomain}

Returns the translation domain for the i18n calls done in this QML engine

> **Note:** Getter function for property translationDomain.

*See also* [setTranslationDomain](plasmaquick-sharedqmlengine.md#setTranslationDomain)()
