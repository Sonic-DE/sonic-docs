---
title: "KUrlLabel Class"
description: "A drop-in replacement for QLabel that displays hyperlinks."
---

# KUrlLabel Class

A drop-in replacement for [QLabel](https://doc.qt.io/qt-6/qlabel.html) that displays hyperlinks. [More...](#details)

- **Header:** `#include <KUrlLabel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QLabel](https://doc.qt.io/qt-6/qlabel.html)

[List of all members, including inherited members](kurllabel-members.md)

## Properties

- [alternatePixmap : QPixmap](#alternatePixmap-prop)
- [floatEnabled : bool](#floatEnabled-prop)
- [glowEnabled : bool](#glowEnabled-prop)
- [tipText : QString](#tipText-prop)
- [url : QString](#url-prop)
- [useCursor : bool](#useCursor-prop)
- [useTips : bool](#useTips-prop)

## Public Functions

- [KUrlLabel(QWidget \*parent = nullptr)](#KUrlLabel)
- [KUrlLabel(const QString &url, const QString &text = QString(), QWidget \*parent = nullptr)](#KUrlLabel-1)
- [const QPixmap \*alternatePixmap() const](#alternatePixmap)
- [bool isFloatEnabled() const](#isFloatEnabled)
- [bool isGlowEnabled() const](#isGlowEnabled)
- [QString tipText() const](#tipText)
- [QString url() const](#url)
- [bool useCursor() const](#useCursor)
- [bool useTips() const](#useTips)

## Public Slots

- [void setAlternatePixmap(const QPixmap &pixmap)](#setAlternatePixmap)
- [void setFloatEnabled(bool do\_float = true)](#setFloatEnabled)
- [void setGlowEnabled(bool glow = true)](#setGlowEnabled)
- [void setHighlightedColor(const QColor &highcolor)](#setHighlightedColor)
- [void setHighlightedColor(const QString &highcolor)](#setHighlightedColor-1)
- [void setSelectedColor(const QColor &color)](#setSelectedColor)
- [void setSelectedColor(const QString &color)](#setSelectedColor-1)
- [void setTipText(const QString &tip)](#setTipText)
- [void setUnderline(bool on = true)](#setUnderline)
- [void setUrl(const QString &url)](#setUrl)
- [void setUseCursor(bool on, QCursor \*cursor = nullptr)](#setUseCursor)
- [void setUseTips(bool on = true)](#setUseTips)

## Signals

- [void enteredUrl()](#enteredUrl)
- [void leftClickedUrl()](#leftClickedUrl)
- [void leftUrl()](#leftUrl)
- [void middleClickedUrl()](#middleClickedUrl)
- [void rightClickedUrl()](#rightClickedUrl)

## Detailed Description {#details}

[KUrlLabel](kurllabel.md) is a drop-in replacement for [QLabel](https://doc.qt.io/qt-6/qlabel.html) that handles text in a fashion similar to how an HTML widget handles hyperlinks. The text can be underlined (or not) and set to different colors. It can also "glow" (cycle colors) when the mouse passes over it.

[KUrlLabel](kurllabel.md) also provides signals for several events, including the mouse leaving and entering the text area and all forms of mouse clicking.

By default [KUrlLabel](kurllabel.md) accepts focus. When focused, standard focus rectangle is displayed as in HTML widget. Pressing Enter key accepts the focused label.

A typical usage would be something like so:

```cpp
KUrlLabel *address = new KUrlLabel(this);
address->setText("My homepage");
address->setUrl("http://www.home.com/~me");
connect(address, &KUrlLabel::leftClickedUrl, this, [this](cont QString &url) { processMyUrl(url); };
```

In this example, the text "My homepage" would be displayed as blue, underlined text. When the mouse passed over it, it would "glow" red. When the user clicks on the text, the signal [leftClickedUrl](kurllabel.md#leftClickedUrl)() would be emitted with "http://www.home.com/~me" as its argument.

## Property Documentation {#property-documentation}

### alternatePixmap : QPixmap {#alternatePixmap-prop}

**Access functions:**

- const `QPixmap` \***[alternatePixmap](kurllabel.md#alternatePixmap)**() const
- `void` **[setAlternatePixmap](kurllabel.md#setAlternatePixmap)**(const `QPixmap` &*pixmap*)

### floatEnabled : bool {#floatEnabled-prop}

**Access functions:**

- `bool` **[isFloatEnabled](kurllabel.md#isFloatEnabled)**() const
- `void` **[setFloatEnabled](kurllabel.md#setFloatEnabled)**(`bool` *do\_float* = true)

### glowEnabled : bool {#glowEnabled-prop}

**Access functions:**

- `bool` **[isGlowEnabled](kurllabel.md#isGlowEnabled)**() const
- `void` **[setGlowEnabled](kurllabel.md#setGlowEnabled)**(`bool` *glow* = true)

### tipText : QString {#tipText-prop}

**Access functions:**

- `QString` **[tipText](kurllabel.md#tipText)**() const
- `void` **[setTipText](kurllabel.md#setTipText)**(const `QString` &*tip*)

### url : QString {#url-prop}

**Access functions:**

- `QString` **[url](kurllabel.md#url)**() const
- `void` **[setUrl](kurllabel.md#setUrl)**(const `QString` &*url*)

### useCursor : bool {#useCursor-prop}

**Access functions:**

- `bool` **[useCursor](kurllabel.md#useCursor)**() const
- `void` **[setUseCursor](kurllabel.md#setUseCursor)**(`bool` *on*, `QCursor` \**cursor* = nullptr)

### useTips : bool {#useTips-prop}

**Access functions:**

- `bool` **[useTips](kurllabel.md#useTips)**() const
- `void` **[setUseTips](kurllabel.md#setUseTips)**(`bool` *on* = true)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KUrlLabel::KUrlLabel(QWidget \**parent* = nullptr) {#KUrlLabel}

Default constructor.

Use [setUrl](kurllabel.md#setUrl)() and [setText](https://doc.qt.io/qt-6/qlabel.html#text-prop)() or QListView::setPixmap() to set the resp. properties.

### \[explicit\] KUrlLabel::KUrlLabel(const QString &*url*, const QString &*text* = QString(), QWidget \**parent* = nullptr) {#KUrlLabel-1}

Convenience constructor.

`url` is the URL emitted when the label is clicked.

`text` is the displayed string. If it's equal to QString() the `url` will be used instead.

`parent` Passed to lower level constructor

@p parent and @p name are passed to [QLabel](https://doc.qt.io/qt-6/qlabel.html), which in turn passes them further down

### const QPixmap \*KUrlLabel::alternatePixmap() const {#alternatePixmap}

Returns the alternate pixmap (may be a null pointer if none was set)

> **Note:** Getter function for property [alternatePixmap](kurllabel.md#alternatePixmap-prop).

*See also* [setAlternatePixmap](kurllabel.md#setAlternatePixmap)()

### \[signal\] void KUrlLabel::enteredUrl() {#enteredUrl}

Emitted when the mouse has passed over the label.

### bool KUrlLabel::isFloatEnabled() const {#isFloatEnabled}

This feature is very similar to the "glow" feature in that the color of the label switches to the selected color when the cursor passes over it. In addition, underlining is turned on for as long as the mouse is overhead. Note that if "glow" and underlining are both already turned on, this feature will have no visible effect.

> **Note:** Getter function for property [floatEnabled](kurllabel.md#floatEnabled-prop).

### bool KUrlLabel::isGlowEnabled() const {#isGlowEnabled}

When this is on, the text will switch to the selected color whenever the mouse passes over it.

> **Note:** Getter function for property [glowEnabled](kurllabel.md#glowEnabled-prop).

### \[signal\] void KUrlLabel::leftClickedUrl() {#leftClickedUrl}

Emitted when the user clicked the left mouse button on this label.

### \[signal\] void KUrlLabel::leftUrl() {#leftUrl}

Emitted when the mouse is no longer over the label.

### \[signal\] void KUrlLabel::middleClickedUrl() {#middleClickedUrl}

Emitted when the user clicked the left mouse button on this label.

### \[signal\] void KUrlLabel::rightClickedUrl() {#rightClickedUrl}

Emitted when the user clicked the right mouse button on this label.

### \[slot\] void KUrlLabel::setAlternatePixmap(const QPixmap &*pixmap*) {#setAlternatePixmap}

Sets the "alt" pixmap.

This pixmap will be displayed when the cursor passes over the label. The effect is similar to the trick done with 'onMouseOver' in javascript.

> **Note:** Setter function for property [alternatePixmap](kurllabel.md#alternatePixmap-prop).

*See also* [alternatePixmap](kurllabel.md#alternatePixmap)()

### \[slot\] void KUrlLabel::setFloatEnabled(bool *do\_float* = true) {#setFloatEnabled}

Turns on or off the "float" feature.

This feature is very similar to the "glow" feature in that the color of the label switches to the selected color when the cursor passes over it. In addition, underlining is turned on for as long as the mouse is overhead. Note that if "glow" and underlining are both already turned on, this feature will have no visible effect. By default, it is `false`.

> **Note:** Setter function for property [floatEnabled](kurllabel.md#floatEnabled-prop).

*See also* [isFloatEnabled](kurllabel.md#isFloatEnabled)()

### \[slot\] void KUrlLabel::setGlowEnabled(bool *glow* = true) {#setGlowEnabled}

Turns on or off the "glow" feature.

When this is on, the text will switch to the selected color whenever the mouse passes over it. By default, it is `true`.

> **Note:** Setter function for property [glowEnabled](kurllabel.md#glowEnabled-prop).

*See also* [isGlowEnabled](kurllabel.md#isGlowEnabled)()

### \[slot\] void KUrlLabel::setHighlightedColor(const QColor &*highcolor*) {#setHighlightedColor}

Sets the highlight color.

This is the default foreground color (non-selected). By default, it is `blue`.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kUrlLabel, qOverload<const QColor &>(&KUrlLabel::setHighlightedColor));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kUrlLabel, [receiver = kUrlLabel](const QColor &highcolor) { receiver->setHighlightedColor(highcolor); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[slot\] void KUrlLabel::setHighlightedColor(const QString &*highcolor*) {#setHighlightedColor-1}

This is an overloaded version for convenience.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kUrlLabel, qOverload<const QString &>(&KUrlLabel::setHighlightedColor));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kUrlLabel, [receiver = kUrlLabel](const QString &highcolor) { receiver->setHighlightedColor(highcolor); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

*See also* [setHighlightedColor](kurllabel.md#setHighlightedColor)()

### \[slot\] void KUrlLabel::setSelectedColor(const QColor &*color*) {#setSelectedColor}

Sets the selected color.

This is the color the text will change to when either a mouse passes over it and "glow" mode is on or when it is selected (clicked). By default, it is `red`.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kUrlLabel, qOverload<const QColor &>(&KUrlLabel::setSelectedColor));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kUrlLabel, [receiver = kUrlLabel](const QColor &color) { receiver->setSelectedColor(color); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[slot\] void KUrlLabel::setSelectedColor(const QString &*color*) {#setSelectedColor-1}

This is an overloaded version for convenience.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kUrlLabel, qOverload<const QString &>(&KUrlLabel::setSelectedColor));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kUrlLabel, [receiver = kUrlLabel](const QString &color) { receiver->setSelectedColor(color); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

*See also* [setSelectedColor](kurllabel.md#setSelectedColor)()

### \[slot\] void KUrlLabel::setTipText(const QString &*tip*) {#setTipText}

Specifies what text to display when tooltips are turned on.

If this is not used, the tip will default to the URL.

> **Note:** Setter function for property [tipText](kurllabel.md#tipText-prop).

*See also* [tipText](kurllabel.md#tipText)(), [setUseTips](kurllabel.md#setUseTips)()

### \[slot\] void KUrlLabel::setUnderline(bool *on* = true) {#setUnderline}

Turns on or off the underlining.

When this is on, the text will be underlined. By default, it is `true`.

### \[slot\] void KUrlLabel::setUrl(const QString &*url*) {#setUrl}

Sets the URL for this label to `url`.

> **Note:** Setter function for property [url](kurllabel.md#url-prop).

*See also* [url](kurllabel.md#url)

### \[slot\] void KUrlLabel::setUseCursor(bool *on*, QCursor \**cursor* = nullptr) {#setUseCursor}

Turns the custom cursor feature on or off.

When this is on, the cursor will change to a custom cursor (default is a "pointing hand") whenever the cursor passes over the label. By default, it is on.

`on` whether a custom cursor should be displayed.

`cursor` the custom cursor. A null pointer indicates the default "hand cursor".

> **Note:** Setter function for property [useCursor](kurllabel.md#useCursor-prop).

*See also* [useCursor](kurllabel.md#useCursor)()

### \[slot\] void KUrlLabel::setUseTips(bool *on* = true) {#setUseTips}

Turns on or off the tool tip feature.

When this is on, the URL will be displayed as a tooltip whenever the mouse passes passes over it. By default, it is `false`.

> **Note:** Setter function for property [useTips](kurllabel.md#useTips-prop).

*See also* [useTips](kurllabel.md#useTips)()

### QString KUrlLabel::tipText() const {#tipText}

Returns the current tooltip text.

> **Note:** Getter function for property [tipText](kurllabel.md#tipText-prop).

*See also* [setTipText](kurllabel.md#setTipText)()

### QString KUrlLabel::url() const {#url}

Returns the URL.

> **Note:** Getter function for property [url](kurllabel.md#url-prop).

*See also* [setUrl](kurllabel.md#setUrl)()

### bool KUrlLabel::useCursor() const {#useCursor}

Returns `true` if the cursor will change while over the URL.

> **Note:** Getter function for property [useCursor](kurllabel.md#useCursor-prop).

*See also* [setUseCursor](kurllabel.md#setUseCursor)()

### bool KUrlLabel::useTips() const {#useTips}

Returns `true` if a tooltip will be displayed.

> **Note:** Getter function for property [useTips](kurllabel.md#useTips-prop).

*See also* [setUseTips](kurllabel.md#setUseTips)(), [setTipText](kurllabel.md#setTipText)()
