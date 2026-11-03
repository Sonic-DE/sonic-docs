---
title: "KQuickConfigModule Class"
description: "The base class for QtQuick configuration modules. This class was introduced in Qt 6.0."
---

# KQuickConfigModule Class

The base class for [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) configuration modules. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KQuickConfigModule>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KCMUtilsQuick)`  
  `target_link_libraries(mytarget PRIVATE KF6::KCMUtilsQuick)`
- **Inherited By:** [KQuickManagedConfigModule](kquickmanagedconfigmodule.md)

[List of all members, including inherited members](kquickconfigmodule-members.md)

## Properties

- [columnWidth : int](#columnWidth-prop)
- [currentIndex : int](#currentIndex-prop)
- [\[read-only\] depth : int](#depth-prop)
- [\[read-only\] mainUi : QQuickItem\* const](#mainUi-prop)

## Public Functions

- [int columnWidth() const](#columnWidth)
- [int currentIndex() const](#currentIndex)
- [int depth() const](#depth)
- [std::shared\_ptr\<QQmlEngine\> engine() const](#engine)
- [QString errorString() const](#errorString)
- [QQuickItem \*mainUi()](#mainUi)
- [void setColumnWidth(int width)](#setColumnWidth)
- [void setCurrentIndex(int index)](#setCurrentIndex)
- [QQuickItem \*subPage(int index) const](#subPage)

## Public Slots

- [void pop()](#pop)
- [void push(const QString &fileName, const QVariantMap &initialProperties = QVariantMap())](#push)
- [void push(QQuickItem \*item)](#push-1)
- [QQuickItem \*takeLast()](#takeLast)

## Signals

- [void columnWidthChanged(int width)](#columnWidthChanged)
- [void currentIndexChanged(int index)](#currentIndexChanged)
- [void depthChanged(int index)](#depthChanged)
- [void mainUiReady()](#mainUiReady)
- [void pagePushed(QQuickItem \*page)](#pagePushed)
- [void pageRemoved()](#pageRemoved)

## Protected Functions

- [KQuickConfigModule(QObject \*parent, const KPluginMetaData &metaData)](#KQuickConfigModule)

## Detailed Description {#details}

Configuration modules are realized as plugins that are dynamically loaded.

All the necessary glue logic and the GUI bells and whistles are provided by the control center and must not concern the module author.

To write a config module, you have to create a C++ plugin and an accompanying QML user interface.

To allow KCMUtils to load your ConfigModule subclass, you must create a [KPluginFactory](../kcoreaddons/kpluginfactory.md) implementation.

```cpp
#include <KPluginFactory>

K_PLUGIN_CLASS_WITH_JSON(MyConfigModule, "yourmetadata.json")
```

The constructor of the ConfigModule then looks like this:

```cpp
YourConfigModule::YourConfigModule(QObject *parent, const KPluginMetaData &metaData)
  : KQuickConfigModule(parent, metaData)
{
}
```

The QML part must be in the KPackage format, installed under share/kpackage/kcms.

The package must have the same name as the plugin filename, to be installed by CMake with the command:

```cpp
kpackage_install_package(packagedir kcm_yourconfigmodule kcms)
```

The "packagedir" is the subdirectory in the source tree where the package sources are located, and "kcm\_yourconfigmodule" is id of the plugin. Finally "kcms" is the literal string "kcms", so that the package is installed as a configuration module (and not some other kind of package).

The QML part can access all the properties of ConfigModule (together with the properties defined in its subclass) by accessing to the global object "kcm", or with the import of "org.kde.kcmutils" the ConfigModule attached property.

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kcmutils as KCMUtils
import org.kde.kirigami as Kirigami

Item {
    // implicit size will be used as initial size when loaded in kcmshell6
    implicitWidth: Kirigami.Units.gridUnit * 30
    implicitHeight: Kirigami.Units.gridUnit * 30

    KCMUtils.ConfigModule.buttons: KCMUtils.ConfigModule.Help | KCMUtils.ConfigModule.Apply

    QQC2.Label {
        // The following two bindings are equivalent:
        text: kcm.needsSave
        enabled: KCMUtils.ConfigModule.needsSave
    }
}
```

See https://develop.kde.org/docs/features/configuration/kcm/ for more detailed documentation.

*See also* KPackage::Package

## Property Documentation {#property-documentation}

### columnWidth : int {#columnWidth-prop}

**Access functions:**

- `int` **[columnWidth](kquickconfigmodule.md#columnWidth)**() const
- `void` **[setColumnWidth](kquickconfigmodule.md#setColumnWidth)**(`int` *width*)

**Notifier signal:**

- `void` **[columnWidthChanged](kquickconfigmodule.md#columnWidthChanged)**(`int` *width*)

### currentIndex : int {#currentIndex-prop}

**Access functions:**

- `int` **[currentIndex](kquickconfigmodule.md#currentIndex)**() const
- `void` **[setCurrentIndex](kquickconfigmodule.md#setCurrentIndex)**(`int` *index*)

**Notifier signal:**

- `void` **[currentIndexChanged](kquickconfigmodule.md#currentIndexChanged)**(`int` *index*)

### \[read-only\] depth : int {#depth-prop}

**Access functions:**

- `int` **[depth](kquickconfigmodule.md#depth)**() const

**Notifier signal:**

- `void` **[depthChanged](kquickconfigmodule.md#depthChanged)**(`int` *index*)

### \[read-only\] mainUi : QQuickItem\* const {#mainUi-prop}

**Access functions:**

- `QQuickItem` \***[mainUi](kquickconfigmodule.md#mainUi)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] KQuickConfigModule::KQuickConfigModule(QObject \**parent*, const KPluginMetaData &*metaData*) {#KQuickConfigModule}

Base class for all [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) config modules.

Creates a new [KQuickConfigModule](kquickconfigmodule.md) with the given `metaData` as a child of `parent`. Use [KQuickConfigModuleLoader](kquickconfigmoduleloader.md) to instantiate this class.

> **Note:** Do not emit changed signals here, since they are not yet connected to any slot.

### int KQuickConfigModule::columnWidth() const {#columnWidth}

Returns the width the kcm wants in column mode.

If a columnWidth is valid ( \> 0 ) and less than the systemsettings' view width, more than one will be visible at once, and the first page will be a sidebar to the last page pushed. As default, this is -1 which will make the shell always show only one page at a time.

> **Note:** Getter function for property [columnWidth](kquickconfigmodule.md#columnWidth-prop).

*See also* [setColumnWidth](kquickconfigmodule.md#setColumnWidth)()

### \[signal\] void KQuickConfigModule::columnWidthChanged(int *width*) {#columnWidthChanged}

Emitted when the wanted column `width` of the KCM changes.

> **Note:** Notifier signal for property [columnWidth](kquickconfigmodule.md#columnWidth-prop).

### int KQuickConfigModule::currentIndex() const {#currentIndex}

Returns the index of the page this KCM should display.

> **Note:** Getter function for property [currentIndex](kquickconfigmodule.md#currentIndex-prop).

*See also* [setCurrentIndex](kquickconfigmodule.md#setCurrentIndex)()

### \[signal\] void KQuickConfigModule::currentIndexChanged(int *index*) {#currentIndexChanged}

Emitted when the `index` of the current page changed.

> **Note:** Notifier signal for property [currentIndex](kquickconfigmodule.md#currentIndex-prop).

### int KQuickConfigModule::depth() const {#depth}

Returns how many pages this kcm has.

It is guaranteed to be at least 1 (the main ui) plus how many times a new page has been pushed without pop.

> **Note:** Getter function for property [depth](kquickconfigmodule.md#depth-prop).

### \[signal\] void KQuickConfigModule::depthChanged(int *index*) {#depthChanged}

Emitted when the number of pages changed, and so their `index`.

> **Note:** Notifier signal for property [depth](kquickconfigmodule.md#depth-prop).

### std::shared\_ptr\<QQmlEngine\> KQuickConfigModule::engine() const {#engine}

Returns the qml engine that built the main config UI.

### QString KQuickConfigModule::errorString() const {#errorString}

The error string in case the [mainUi](kquickconfigmodule.md#mainUi) failed to load.

### QQuickItem \*KQuickConfigModule::mainUi() {#mainUi}

Returns the main UI for this configuration module.

It's a [QQuickItem](https://doc.qt.io/qt-6/qquickitem.html) coming from the QML package named the same as the [KAboutData](../kcoreaddons/kaboutdata.md)'s component name for this config module.

Normally, ui/main.qml will be loaded from the qrc baked into the plugin. However, if the PLASMA\_PLATFORM environmental variable is set, the module will try to load a platform-specific QML file as its mainUi starting point.

For example:

environment has set `export PLASMA_PLATFORM=phone:handset`

The module will try to find main\_phone.qml, then main\_handset.qml, then main.qml. The first file that is found will be used as mainUi. If none is found and main.qml doesn't exist, the module is broken and an error will be displayed.

> **Note:** Getter function for property [mainUi](kquickconfigmodule.md#mainUi-prop).

### \[signal\] void KQuickConfigModule::mainUiReady() {#mainUiReady}

Emitted when the main Ui has loaded successfully and [mainUi](kquickconfigmodule.md#mainUi)() is available.

### \[signal\] void KQuickConfigModule::pagePushed(QQuickItem \**page*) {#pagePushed}

Emitted when a new sub `page` is pushed.

### \[signal\] void KQuickConfigModule::pageRemoved() {#pageRemoved}

Emitted when a sub page is popped.

### \[slot\] void KQuickConfigModule::pop() {#pop}

Pop the last page of the KCM hierarchy, the page is destroyed.

### \[slot\] void KQuickConfigModule::push(const QString &*fileName*, const QVariantMap &*initialProperties* = QVariantMap()) {#push}

Push a new sub page with the given `fileName` with optional `initialProperties` in the KCM hierarchy: pages will be seen as a Kirigami [PageRow](../kirigami/qml-org-kde-kirigami-pagerow.md).

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kQuickConfigModule, qOverload<const QString &, const QVariantMap &>(&KQuickConfigModule::push));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kQuickConfigModule, [receiver = kQuickConfigModule](const QString &fileName, const QVariantMap &initialProperties) { receiver->push(fileName, initialProperties); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[slot\] void KQuickConfigModule::push(QQuickItem \**item*) {#push-1}

Push a given QQuick `item` as a new sub page in the KCM hierarchy.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kQuickConfigModule, qOverload<QQuickItem *>(&KQuickConfigModule::push));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kQuickConfigModule, [receiver = kQuickConfigModule](QQuickItem *item) { receiver->push(item); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### void KQuickConfigModule::setColumnWidth(int *width*) {#setColumnWidth}

Sets the column `width` we want.

> **Note:** Setter function for property [columnWidth](kquickconfigmodule.md#columnWidth-prop).

*See also* [columnWidth](kquickconfigmodule.md#columnWidth)()

### void KQuickConfigModule::setCurrentIndex(int *index*) {#setCurrentIndex}

Sets the current page `index` this KCM should display.

> **Note:** Setter function for property [currentIndex](kquickconfigmodule.md#currentIndex-prop).

*See also* [currentIndex](kquickconfigmodule.md#currentIndex)()

### QQuickItem \*KQuickConfigModule::subPage(int *index*) const {#subPage}

Returns a subpage at a given depth `index`.

> **Note:** This does not include the [mainUi](kquickconfigmodule.md#mainUi). That is, a depth of 2 is a [mainUi](kquickconfigmodule.md#mainUi) and one subPage at index 0.

### \[slot\] QQuickItem \*KQuickConfigModule::takeLast() {#takeLast}

Remove and return the last page of the KCM hierarchy.

The popped page won't be deleted, it's the caller's responsibility to manage the lifetime of the returned item.

Returns the last page if any, `nullptr` otherwise.
