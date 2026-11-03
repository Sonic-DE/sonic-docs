---
title: "KGuiItem Class"
description: "An abstract class for setting the text, icon, tooltip and WhatsThis data on a GUI item (e.g. a QPushButton)."
---

# KGuiItem Class

An abstract class for setting the text, icon, tooltip and WhatsThis data on a GUI item (e.g. a [QPushButton](https://doc.qt.io/qt-6/qpushbutton.html)). [More...](#details)

- **Header:** `#include <KGuiItem>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

[List of all members, including inherited members](kguiitem-members.md)

## Public Functions

- [KGuiItem()](#KGuiItem)
- [KGuiItem(const QString &text, const QIcon &icon, const QString &toolTip = QString(), const QString &whatsThis = QString())](#KGuiItem-1)
- [KGuiItem(const QString &text, const QString &iconName = QString(), const QString &toolTip = QString(), const QString &whatsThis = QString())](#KGuiItem-2)
- [bool hasIcon() const](#hasIcon)
- [QIcon icon() const](#icon)
- [QString iconName() const](#iconName)
- [bool isEnabled() const](#isEnabled)
- [QString plainText() const](#plainText)
- [void setEnabled(bool enable)](#setEnabled)
- [void setIcon(const QIcon &iconset)](#setIcon)
- [void setIconName(const QString &iconName)](#setIconName)
- [void setText(const QString &text)](#setText)
- [void setToolTip(const QString &tooltip)](#setToolTip)
- [void setWhatsThis(const QString &whatsThis)](#setWhatsThis)
- [QString text() const](#text)
- [QString toolTip() const](#toolTip)
- [QString whatsThis() const](#whatsThis)

## Static Public Members

- [void assign(QPushButton \*button, const KGuiItem &item)](#assign)

## Detailed Description {#details}

*See also* [KStandardGuiItem](kstandardguiitem.md)

## Member Function Documentation {#member-function-documentation}

### KGuiItem::KGuiItem() {#KGuiItem}

Constructs an empty [KGuiItem](kguiitem.md). You can use the various methods provided by this class to set the text, icon... etc.

### KGuiItem::KGuiItem(const QString &*text*, const QIcon &*icon*, const QString &*toolTip* = QString(), const QString &*whatsThis* = QString()) {#KGuiItem-1}

Constructs a [KGuiItem](kguiitem.md) with the provided arguments.

`text` the text to use with the GUI item

`icon` the [QIcon](https://doc.qt.io/qt-6/qicon.html) object used to get an icon to display next to the text on this item

`toolTip` the tooltip to use for this item

`whatsThis` the text to use for the WhatThis help message

### \[explicit\] KGuiItem::KGuiItem(const QString &*text*, const QString &*iconName* = QString(), const QString &*toolTip* = QString(), const QString &*whatsThis* = QString()) {#KGuiItem-2}

Constructs a [KGuiItem](kguiitem.md) with the provided arguments.

`text` the text to use with the GUI item

`iconName` the name of the icon to display next to the text on the item; [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme)() is used to get a icon with that name from the icon themes available on the system

`tooltip` the tooltip to use for this item

`whatsThis` the text to use for the WhatThis help message

### \[static\] void KGuiItem::assign(QPushButton \**button*, const KGuiItem &*item*) {#assign}

A static method that can be used to set the text, icon, tooltip and WhatThis properties from `item` on `button`.

```cpp
// Create a QDialogButtonBox with two buttons, of Yes and No standard type
auto *buttonBox = new QDialogButtonBox({QDialogButtonBox::Yes | QDialogButtonBox::No}, this);

// Assign the text and icon from KStandardGuiItem::quit()/continue() to the buttons in the
// button dialog box
KGuiItem::assign(buttonBox->button(QDialogButtonBox::Yes), KStandardGuiItem::quit());
KGuiItem::assign(buttonBox->button(QDialogButtonBox::No), KStandardGuiItem::continue());
```

### bool KGuiItem::hasIcon() const {#hasIcon}

Returns `true` if this GUI item has an icon set for it and `false` otherwise.

### QIcon KGuiItem::icon() const {#icon}

Returns the icon used by this GUI item.

This will return a null [QIcon](https://doc.qt.io/qt-6/qicon.html) if no icon was previously set for this item.

*See also* [setIcon](kguiitem.md#setIcon)()

### QString KGuiItem::iconName() const {#iconName}

Returns the name of the icon used by this GUI item.

This will return an empty string if no icon was previously set for this item.

*See also* [setIconName](kguiitem.md#setIconName)()

### bool KGuiItem::isEnabled() const {#isEnabled}

Returns `true` if this GUI item is enabled and `false` otherwise.

*See also* [QWidget::isEnabled](https://doc.qt.io/qt-6/qwidget.html#enabled-prop)()

### QString KGuiItem::plainText() const {#plainText}

Returns the text used by this GUI item after stripping all existing '&' characters which denote keyboard accelerators.

*See also* [text](kguiitem.md#text)()

### void KGuiItem::setEnabled(bool *enable*) {#setEnabled}

Toggles the enabled property of this GUI item.

*See also* [isEnabled](kguiitem.md#isEnabled)(), [QWidget::setEnabled](https://doc.qt.io/qt-6/qwidget.html#enabled-prop)()

### void KGuiItem::setIcon(const QIcon &*iconset*) {#setIcon}

Sets the icon to be shown next to the text of this GUI item.

*See also* [icon](kguiitem.md#icon)()

### void KGuiItem::setIconName(const QString &*iconName*) {#setIconName}

Sets the name of the icon that will be shown next to the text of this GUI item. The actual [QIcon](https://doc.qt.io/qt-6/qicon.html) will be obtained by using [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme)().

*See also* [iconName](kguiitem.md#iconName)()

### void KGuiItem::setText(const QString &*text*) {#setText}

Sets the text to use for this GUI item.

*See also* [text](kguiitem.md#text)()

### void KGuiItem::setToolTip(const QString &*tooltip*) {#setToolTip}

Sets the tooltip text.

*See also* [toolTip](kguiitem.md#toolTip)()

### void KGuiItem::setWhatsThis(const QString &*whatsThis*) {#setWhatsThis}

Sets the WhatThis text.

*See also* [whatsThis](kguiitem.md#whatsThis)()

### QString KGuiItem::text() const {#text}

Returns the text used by this GUI item.

This may contain '&' characters which denote a keyboard accelerator shortcut that can be used to invoke the GUI item, e.g. Alt + 'O' for button "&OK". (Note that the '&' is not visible to the user).

You can get the plain text without the accelerator denoting character '&', by using [plainText](kguiitem.md#plainText)().

*See also* [setText](kguiitem.md#setText)()

### QString KGuiItem::toolTip() const {#toolTip}

Returns the tooltip used for this GUI item.

This will return an empty string if no tooltip was previously set for this item.

*See also* [setToolTip](kguiitem.md#setToolTip)()

### QString KGuiItem::whatsThis() const {#whatsThis}

Returns the WhatThis text used for this GUI item.

This will return an empty string if no WhatThis text was previously set for this item.

*See also* [setWhatsThis](kguiitem.md#setWhatsThis)()
