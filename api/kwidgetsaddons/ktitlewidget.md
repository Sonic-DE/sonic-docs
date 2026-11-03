---
title: "KTitleWidget Class"
description: "Standard title widget."
---

# KTitleWidget Class

Standard title widget. [More...](#details)

- **Header:** `#include <KTitleWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](ktitlewidget-members.md)

## Public Types

- [enum KTitleWidget::ImageAlignment](#ImageAlignment-enum)
- [enum KTitleWidget::MessageType](#MessageType-enum)

## Properties

- [autoHideTimeout : int](#autoHideTimeout-prop)
- [comment : QString](#comment-prop)
- [icon : QIcon](#icon-prop)
- [iconSize : QSize](#iconSize-prop)
- [text : QString](#text-prop)
- [\[since 6.26\] textSelectable : int](#textSelectable-prop)

## Public Functions

- [KTitleWidget(QWidget \*parent = nullptr)](#KTitleWidget)
- [int autoHideTimeout() const](#autoHideTimeout)
- [QString comment() const](#comment)
- [QIcon icon() const](#icon)
- [QSize iconSize() const](#iconSize)
- [int level()](#level)
- [void setBuddy(QWidget \*buddy)](#setBuddy)
- [void setWidget(QWidget \*widget)](#setWidget)
- [QString text() const](#text)
- [bool textSelectable() const](#textSelectable) (since 6.26)

## Public Slots

- [void setAutoHideTimeout(int msecs)](#setAutoHideTimeout)
- [void setComment(const QString &comment, KTitleWidget::MessageType type = PlainMessage)](#setComment)
- [void setIcon(KTitleWidget::MessageType type, KTitleWidget::ImageAlignment alignment = ImageRight)](#setIcon)
- [void setIcon(const QIcon &icon, KTitleWidget::ImageAlignment alignment = ImageRight)](#setIcon-1)
- [void setIconSize(const QSize &iconSize)](#setIconSize)
- [void setLevel(int level)](#setLevel)
- [void setText(const QString &text, KTitleWidget::MessageType type)](#setText)
- [void setText(const QString &text, Qt::Alignment alignment = Qt::AlignLeft \| Qt::AlignVCenter)](#setText-1)
- [void setTextSelectable(bool selectable)](#setTextSelectable) (since 6.26)

## Detailed Description {#details}

This class provides a widget often used for dialog titles.

[KTitleWidget](ktitlewidget.md) uses the general application font at 1.4 times its size to style the text. This is a visual change from 4.x.

Usage:

[KTitleWidget](ktitlewidget.md) is very simple to use. You can either use its default text (and pixmap) properties or display your own widgets in the title widget.

A title text with a right-aligned pixmap:

```cpp
KTitleWidget *titleWidget = new KTitleWidget(this);
titleWidget->setText(i18n("Title"));
titleWidget->setIcon(QIcon::fromTheme("screen"));
```

Use it with an own widget:

```cpp
KTitleWidget *checkboxTitleWidget = new KTitleWidget(this);

QWidget *checkBoxTitleMainWidget = new QWidget(this);
QVBoxLayout *titleLayout = new QVBoxLayout(checkBoxTitleMainWidget);
titleLayout->setContentsMargins(6, 6, 6, 6);

QCheckBox *checkBox = new QCheckBox("Text Checkbox", checkBoxTitleMainWidget);
titleLayout->addWidget(checkBox);

checkboxTitleWidget->setWidget(checkBoxTitleMainWidget);
```

*See also* [KPageView](kpageview.md)

## Member Type Documentation {#member-type-documentation}

### enum KTitleWidget::ImageAlignment {#ImageAlignment-enum}

Possible title pixmap alignments.

| Constant | Value | Description |
| --- | --- | --- |
| `KTitleWidget::ImageLeft` | `0` | Display the pixmap left |
| `KTitleWidget::ImageRight` | `1` | Display the pixmap right (default) |

### enum KTitleWidget::MessageType {#MessageType-enum}

Comment message types

| Constant | Value | Description |
| --- | --- | --- |
| `KTitleWidget::PlainMessage` | `0` | Normal comment |
| `KTitleWidget::InfoMessage` | `1` | Information the user should be alerted to |
| `KTitleWidget::WarningMessage` | `2` | A warning the user should be alerted to |
| `KTitleWidget::ErrorMessage` | `3` | An error message |

## Property Documentation {#property-documentation}

### autoHideTimeout : int {#autoHideTimeout-prop}

**Access functions:**

- `int` **[autoHideTimeout](ktitlewidget.md#autoHideTimeout)**() const
- `void` **[setAutoHideTimeout](ktitlewidget.md#setAutoHideTimeout)**(`int` *msecs*)

### comment : QString {#comment-prop}

**Access functions:**

- `QString` **[comment](ktitlewidget.md#comment)**() const
- `void` **[setComment](ktitlewidget.md#setComment)**(const `QString` &*comment*, `KTitleWidget::MessageType` *type* = PlainMessage)

### icon : QIcon {#icon-prop}

**Access functions:**

- `QIcon` **[icon](ktitlewidget.md#icon)**() const
- `void` **[setIcon](ktitlewidget.md#setIcon-1)**(const `QIcon` &*icon*, `KTitleWidget::ImageAlignment` *alignment* = ImageRight)
- `void` **[setIcon](ktitlewidget.md#setIcon)**(`KTitleWidget::MessageType` *type*, `KTitleWidget::ImageAlignment` *alignment* = ImageRight)

### iconSize : QSize {#iconSize-prop}

**Access functions:**

- `QSize` **[iconSize](ktitlewidget.md#iconSize)**() const
- `void` **[setIconSize](ktitlewidget.md#setIconSize)**(const `QSize` &*iconSize*)

### text : QString {#text-prop}

**Access functions:**

- `QString` **[text](ktitlewidget.md#text)**() const
- `void` **[setText](ktitlewidget.md#setText-1)**(const `QString` &*text*, `Qt::Alignment` *alignment* = Qt::AlignLeft \| Qt::AlignVCenter)
- `void` **[setText](ktitlewidget.md#setText)**(const `QString` &*text*, `KTitleWidget::MessageType` *type*)

### \[since 6.26\] textSelectable : int {#textSelectable-prop}

This property was introduced in Qt 6.26.

**Access functions:**

- `bool` **[textSelectable](ktitlewidget.md#textSelectable)**() const
- `void` **[setTextSelectable](ktitlewidget.md#setTextSelectable)**(`bool` *selectable*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KTitleWidget::KTitleWidget(QWidget \**parent* = nullptr) {#KTitleWidget}

Constructs a title widget.

### int KTitleWidget::autoHideTimeout() const {#autoHideTimeout}

Get the current timeout value in milliseconds

Returns timeout value in msecs

> **Note:** Getter function for property [autoHideTimeout](ktitlewidget.md#autoHideTimeout-prop).

*See also* [setAutoHideTimeout](ktitlewidget.md#setAutoHideTimeout)()

### QString KTitleWidget::comment() const {#comment}

Returns the text displayed in the comment below the title, if any

> **Note:** Getter function for property [comment](ktitlewidget.md#comment-prop).

*See also* [setComment](ktitlewidget.md#setComment)()

### QIcon KTitleWidget::icon() const {#icon}

Returns the icon displayed in the title

> **Note:** Getter function for property [icon](ktitlewidget.md#icon-prop).

*See also* [setIcon](ktitlewidget.md#setIcon)()

### QSize KTitleWidget::iconSize() const {#iconSize}

Returns the size of the icon displayed in the title

> **Note:** Getter function for property [iconSize](ktitlewidget.md#iconSize-prop).

*See also* [setIconSize](ktitlewidget.md#setIconSize)()

### int KTitleWidget::level() {#level}

Returns the level of this title: it influences the font size following the guidelines in the [KDE HIG](https://develop.kde.org/hig/text_and_labels/). It also corresponds to the level api of Kirigami Heading for QML applications

> **Note:** The default level is 1.

*See also* [setLevel](ktitlewidget.md#setLevel)()

### \[slot\] void KTitleWidget::setAutoHideTimeout(int *msecs*) {#setAutoHideTimeout}

Set the autohide timeout of the label

Set value to 0 to disable autohide, which is the default.

`msecs` timeout value in milliseconds

> **Note:** Setter function for property [autoHideTimeout](ktitlewidget.md#autoHideTimeout-prop).

*See also* [autoHideTimeout](ktitlewidget.md#autoHideTimeout)()

### void KTitleWidget::setBuddy(QWidget \**buddy*) {#setBuddy}

Sets this label's buddy to buddy.

When the user presses the shortcut key indicated by the label in this title widget, the keyboard focus is transferred to the label's buddy widget.

`buddy` the widget to activate when the shortcut key is activated

### \[slot\] void KTitleWidget::setComment(const QString &*comment*, KTitleWidget::MessageType *type* = PlainMessage) {#setComment}

`comment` Text displayed beneath the main title as a comment. It can either be plain text or rich text.

`type` The sort of message it is.

> **Note:** Setter function for property [comment](ktitlewidget.md#comment-prop).

*See also* [comment](ktitlewidget.md#comment)()

### \[slot\] void KTitleWidget::setIcon(KTitleWidget::MessageType *type*, KTitleWidget::ImageAlignment *alignment* = ImageRight) {#setIcon}

`type` the type of message icon to display in the header

`alignment` alignment of the icon (default is right aligned).

> **Note:** Setter function for property [icon](ktitlewidget.md#icon-prop).

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kTitleWidget, qOverload<KTitleWidget::MessageType, KTitleWidget::ImageAlignment>(&KTitleWidget::setIcon));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kTitleWidget, [receiver = kTitleWidget](KTitleWidget::MessageType type, KTitleWidget::ImageAlignment alignment) { receiver->setIcon(type, alignment); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

*See also* [icon](ktitlewidget.md#icon)()

### \[slot\] void KTitleWidget::setIcon(const QIcon &*icon*, KTitleWidget::ImageAlignment *alignment* = ImageRight) {#setIcon-1}

Set the icon to display in the header.

`icon` the icon to display in the header.

`alignment` alignment of the icon (default is right aligned).

> **Note:** Setter function for property [icon](ktitlewidget.md#icon-prop).

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kTitleWidget, qOverload<const QIcon &, KTitleWidget::ImageAlignment>(&KTitleWidget::setIcon));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kTitleWidget, [receiver = kTitleWidget](const QIcon &icon, KTitleWidget::ImageAlignment alignment) { receiver->setIcon(icon, alignment); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[slot\] void KTitleWidget::setIconSize(const QSize &*iconSize*) {#setIconSize}

Set the size of the icon to display in the header.

`iconSize` the size of the icon, or an invalid [QSize](https://doc.qt.io/qt-6/qsize.html) to reset to the default

The default size is defined by the GUI style and its value for [QStyle::PM\_MessageBoxIconSize](https://doc.qt.io/qt-6/qstyle.html#PixelMetric-enum).

> **Note:** Setter function for property [iconSize](ktitlewidget.md#iconSize-prop).

*See also* [iconSize](ktitlewidget.md#iconSize)()

### \[slot\] void KTitleWidget::setLevel(int *level*) {#setLevel}

Sets the level of this title, similar to HTML's h1 h2 h3...

Follows the [KDE HIG](https://develop.kde.org/hig/text_and_labels/).

`level` the level of the title, 1 is the biggest font and most important, descending

*See also* [level](ktitlewidget.md#level)()

### \[slot\] void KTitleWidget::setText(const QString &*text*, KTitleWidget::MessageType *type*) {#setText}

`text` Text displayed on the label. It can either be plain text or rich text.

`type` The sort of message it is; will also set the icon accordingly

> **Note:** Setter function for property [text](ktitlewidget.md#text-prop).

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kTitleWidget, qOverload<const QString &, KTitleWidget::MessageType>(&KTitleWidget::setText));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kTitleWidget, [receiver = kTitleWidget](const QString &text, KTitleWidget::MessageType type) { receiver->setText(text, type); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

*See also* [text](ktitlewidget.md#text)()

### \[slot\] void KTitleWidget::setText(const QString &*text*, Qt::Alignment *alignment* = Qt::AlignLeft \| Qt::AlignVCenter) {#setText-1}

`text` Text displayed on the label. It can either be plain text or rich text.

`alignment` Alignment of the text. Default is left and vertical centered.

> **Note:** Setter function for property [text](ktitlewidget.md#text-prop).

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kTitleWidget, qOverload<const QString &, Qt::Alignment>(&KTitleWidget::setText));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kTitleWidget, [receiver = kTitleWidget](const QString &text, Qt::Alignment alignment) { receiver->setText(text, alignment); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

*See also* [text](ktitlewidget.md#text)()

### \[slot, since 6.26\] void KTitleWidget::setTextSelectable(bool *selectable*) {#setTextSelectable}

Sets whether the text is selectable or not.

`selectable` whether the text is selectable, defaults to true.

> **Note:** Setter function for property [textSelectable](ktitlewidget.md#textSelectable-prop).

This function was introduced in Qt 6.26.

*See also* [textSelectable](ktitlewidget.md#textSelectable)()

### void KTitleWidget::setWidget(QWidget \**widget*) {#setWidget}

`widget` Widget displayed on the title widget.

### QString KTitleWidget::text() const {#text}

Returns the text displayed in the title

> **Note:** Getter function for property [text](ktitlewidget.md#text-prop).

*See also* [setText](ktitlewidget.md#setText)()

### \[since 6.26\] bool KTitleWidget::textSelectable() const {#textSelectable}

Returns if the text is selectable

> **Note:** Getter function for property [textSelectable](ktitlewidget.md#textSelectable-prop).

This function was introduced in Qt 6.26.

*See also* [setTextSelectable](ktitlewidget.md#setTextSelectable)()
