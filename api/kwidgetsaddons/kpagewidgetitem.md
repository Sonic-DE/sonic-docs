---
title: "KPageWidgetItem Class"
description: "KPageWidgetItem is used by KPageWidget and represents a page."
---

# KPageWidgetItem Class

[KPageWidgetItem](kpagewidgetitem.md) is used by [KPageWidget](kpagewidget.md) and represents a page. [More...](#details)

- **Header:** `#include <KPageWidgetModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kpagewidgetitem-members.md)

## Properties

- [\[since 6.6\] actions : QList\<QAction \*\>](#actions-prop)
- [checkable : bool](#checkable-prop)
- [checked : bool](#checked-prop)
- [enabled : bool](#enabled-prop)
- [header : QString](#header-prop)
- [headerVisible : bool](#headerVisible-prop)
- [icon : QIcon](#icon-prop)
- [name : QString](#name-prop)

## Public Functions

- [KPageWidgetItem(QWidget \*widget)](#KPageWidgetItem)
- [KPageWidgetItem(QWidget \*widget, const QString &name)](#KPageWidgetItem-1)
- [QList\<QAction \*\> actions() const](#actions) (since 6.6)
- [QString header() const](#header)
- [QIcon icon() const](#icon)
- [bool isCheckable() const](#isCheckable)
- [bool isChecked() const](#isChecked)
- [bool isEnabled() const](#isEnabled)
- [bool isHeaderVisible() const](#isHeaderVisible)
- [QString name() const](#name)
- [void setActions(QList\<QAction \*\> actions)](#setActions) (since 6.6)
- [void setCheckable(bool checkable)](#setCheckable)
- [void setHeader(const QString &header)](#setHeader)
- [void setHeaderVisible(bool visible)](#setHeaderVisible)
- [void setIcon(const QIcon &icon)](#setIcon)
- [void setName(const QString &name)](#setName)
- [QWidget \*widget() const](#widget)

## Public Slots

- [void setChecked(bool checked)](#setChecked)
- [void setEnabled(bool)](#setEnabled)

## Signals

- [void actionsChanged()](#actionsChanged) (since 6.6)
- [void changed()](#changed)
- [void toggled(bool checked)](#toggled)

## Detailed Description {#details}

Example:

```cpp
ColorPage *page = new ColorPage;

KPageWidgetItem *item = new KPageWidgetItem( page, i18n( "Colors" ) );
item->setHeader( i18n( "Colors of Main Window" ) );
item->setIcon( QIcon::fromTheme( "colors" ) );

KPageWidget *pageWidget = new KPageWidget( this );
pageWidget->addPage( item );
```

## Property Documentation {#property-documentation}

### \[since 6.6\] actions : QList\<QAction \*\> {#actions-prop}

This property holds the actions associated to the page.

> **Warning:** This is not supported when using a [KPageView](kpageview.md)/[KPageWidget](kpagewidget.md)/[KPageDialog](kpagedialog.md) with the Tabbed face type.

This property was introduced in Qt 6.6.

**Access functions:**

- `QList`\<`QAction` \*\> **[actions](kpagewidgetitem.md#actions)**() const
- `void` **[setActions](kpagewidgetitem.md#setActions)**(`QList`\<`QAction` \*\> *actions*)

**Notifier signal:**

- `void` **[actionsChanged](kpagewidgetitem.md#actionsChanged)**()

### checkable : bool {#checkable-prop}

**Access functions:**

- `bool` **[isCheckable](kpagewidgetitem.md#isCheckable)**() const
- `void` **[setCheckable](kpagewidgetitem.md#setCheckable)**(`bool` *checkable*)

### checked : bool {#checked-prop}

**Access functions:**

- `bool` **[isChecked](kpagewidgetitem.md#isChecked)**() const
- `void` **[setChecked](kpagewidgetitem.md#setChecked)**(`bool` *checked*)

### enabled : bool {#enabled-prop}

This property holds whether the item is enabled.

It dis-/enables both the widget and the item in the list-/treeview.

**Access functions:**

- `bool` **[isEnabled](kpagewidgetitem.md#isEnabled)**() const
- `void` **[setEnabled](kpagewidgetitem.md#setEnabled)**(*bool*)

### header : QString {#header-prop}

**Access functions:**

- `QString` **[header](kpagewidgetitem.md#header)**() const
- `void` **[setHeader](kpagewidgetitem.md#setHeader)**(const `QString` &*header*)

### headerVisible : bool {#headerVisible-prop}

**Access functions:**

- `bool` **[isHeaderVisible](kpagewidgetitem.md#isHeaderVisible)**() const
- `void` **[setHeaderVisible](kpagewidgetitem.md#setHeaderVisible)**(`bool` *visible*)

### icon : QIcon {#icon-prop}

**Access functions:**

- `QIcon` **[icon](kpagewidgetitem.md#icon)**() const
- `void` **[setIcon](kpagewidgetitem.md#setIcon)**(const `QIcon` &*icon*)

### name : QString {#name-prop}

**Access functions:**

- `QString` **[name](kpagewidgetitem.md#name)**() const
- `void` **[setName](kpagewidgetitem.md#setName)**(const `QString` &*name*)

## Member Function Documentation {#member-function-documentation}

### KPageWidgetItem::KPageWidgetItem(QWidget \**widget*) {#KPageWidgetItem}

Creates a new page widget item.

`widget` The widget that is shown as page in the [KPageWidget](kpagewidget.md).

### KPageWidgetItem::KPageWidgetItem(QWidget \**widget*, const QString &*name*) {#KPageWidgetItem-1}

Creates a new page widget item.

`widget` The widget that is shown as page in the [KPageWidget](kpagewidget.md).

`name` The localized string that is show in the navigation view of the [KPageWidget](kpagewidget.md).

### \[since 6.6\] QList\<QAction \*\> KPageWidgetItem::actions() const {#actions}

Returns the actions associated to the page.

> **Note:** Getter function for property [actions](kpagewidgetitem.md#actions-prop).

This function was introduced in Qt 6.6.

*See also* [setActions](kpagewidgetitem.md#setActions)()

### \[signal, since 6.6\] void KPageWidgetItem::actionsChanged() {#actionsChanged}

This signal is emitted whenever the actions associated to the page are changed.

> **Note:** Notifier signal for property [actions](kpagewidgetitem.md#actions-prop).

This function was introduced in Qt 6.6.

### \[signal\] void KPageWidgetItem::changed() {#changed}

This signal is emitted whenever the icon or header is changed.

### QString KPageWidgetItem::header() const {#header}

Returns the header of the page widget item.

> **Note:** Getter function for property [header](kpagewidgetitem.md#header-prop).

*See also* [setHeader](kpagewidgetitem.md#setHeader)()

### QIcon KPageWidgetItem::icon() const {#icon}

Returns the icon of the page widget item.

> **Note:** Getter function for property [icon](kpagewidgetitem.md#icon-prop).

*See also* [setIcon](kpagewidgetitem.md#setIcon)()

### bool KPageWidgetItem::isCheckable() const {#isCheckable}

Returns whether the page widget item is checkable.

> **Note:** Getter function for property [checkable](kpagewidgetitem.md#checkable-prop).

### bool KPageWidgetItem::isChecked() const {#isChecked}

Returns whether the page widget item is checked.

> **Note:** Getter function for property [checked](kpagewidgetitem.md#checked-prop).

### bool KPageWidgetItem::isEnabled() const {#isEnabled}

Returns whether the page widget item is enabled.

> **Note:** Getter function for property [enabled](kpagewidgetitem.md#enabled-prop).

### bool KPageWidgetItem::isHeaderVisible() const {#isHeaderVisible}

Returns whether the page will show the header title

> **Note:** Getter function for property [headerVisible](kpagewidgetitem.md#headerVisible-prop).

### QString KPageWidgetItem::name() const {#name}

Returns the name of the page widget item.

> **Note:** Getter function for property [name](kpagewidgetitem.md#name-prop).

*See also* [setName](kpagewidgetitem.md#setName)()

### \[since 6.6\] void KPageWidgetItem::setActions(QList\<QAction \*\> *actions*) {#setActions}

Set the actions associated to the page.

> **Note:** Setter function for property [actions](kpagewidgetitem.md#actions-prop).

This function was introduced in Qt 6.6.

*See also* [actions](kpagewidgetitem.md#actions)()

### void KPageWidgetItem::setCheckable(bool *checkable*) {#setCheckable}

Sets whether the page widget item is checkable in the view. `checkable` True if the page widget is checkable, otherwise false.

> **Note:** Setter function for property [checkable](kpagewidgetitem.md#checkable-prop).

*See also* [isCheckable](kpagewidgetitem.md#isCheckable)()

### \[slot\] void KPageWidgetItem::setChecked(bool *checked*) {#setChecked}

Sets whether the page widget item is checked.

> **Note:** Setter function for property [checked](kpagewidgetitem.md#checked-prop).

*See also* [isChecked](kpagewidgetitem.md#isChecked)()

### \[slot\] void KPageWidgetItem::setEnabled(*bool*) {#setEnabled}

Sets whether the page widget item is enabled.

> **Note:** Setter function for property [enabled](kpagewidgetitem.md#enabled-prop).

*See also* [isEnabled](kpagewidgetitem.md#isEnabled)()

### void KPageWidgetItem::setHeader(const QString &*header*) {#setHeader}

Sets the header of the page widget item.

If setHeader(QString()) is used, what is the default if the header does not got set explicit, then the defined [name](kpagewidgetitem.md#name)() will also be used for the header.

`header` Header of the page widget item.

> **Note:** Setter function for property [header](kpagewidgetitem.md#header-prop).

*See also* [header](kpagewidgetitem.md#header)()

### void KPageWidgetItem::setHeaderVisible(bool *visible*) {#setHeaderVisible}

Set whether the page should show the header title

> **Note:** Setter function for property [headerVisible](kpagewidgetitem.md#headerVisible-prop).

*See also* [isHeaderVisible](kpagewidgetitem.md#isHeaderVisible)()

### void KPageWidgetItem::setIcon(const QIcon &*icon*) {#setIcon}

Sets the icon of the page widget item. `icon` Icon of the page widget item.

> **Note:** Setter function for property [icon](kpagewidgetitem.md#icon-prop).

*See also* [icon](kpagewidgetitem.md#icon)()

### void KPageWidgetItem::setName(const QString &*name*) {#setName}

Sets the name of the item as shown in the navigation view of the page widget.

> **Note:** Setter function for property [name](kpagewidgetitem.md#name-prop).

*See also* [name](kpagewidgetitem.md#name)()

### \[signal\] void KPageWidgetItem::toggled(bool *checked*) {#toggled}

This signal is emitted whenever the user checks or unchecks the item of [setChecked](kpagewidgetitem.md#setChecked)() is called.

### QWidget \*KPageWidgetItem::widget() const {#widget}

Returns the widget of the page widget item.
