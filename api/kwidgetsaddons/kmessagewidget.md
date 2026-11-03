---
title: "KMessageWidget Class"
description: "A widget to provide feedback or propose opportunistic interactions."
---

# KMessageWidget Class

A widget to provide feedback or propose opportunistic interactions. [More...](#details)

- **Header:** `#include <KMessageWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QFrame](https://doc.qt.io/qt-6/qframe.html)

[List of all members, including inherited members](kmessagewidget-members.md)

## Public Types

- [enum KMessageWidget::MessageType](#MessageType-enum)
- [\[since 6.0\] enum KMessageWidget::Position](#Position-enum)

## Properties

- [closeButtonVisible : bool](#closeButtonVisible-prop)
- [icon : QIcon](#icon-prop)
- [messageType : MessageType](#messageType-prop)
- [position : Position](#position-prop)
- [text : QString](#text-prop)
- [textFormat : Qt::TextFormat](#textFormat-prop)
- [wordWrap : bool](#wordWrap-prop)

## Public Functions

- [KMessageWidget(QWidget \*parent = nullptr)](#KMessageWidget)
- [KMessageWidget(const QString &text, QWidget \*parent = nullptr)](#KMessageWidget-1)
- [~KMessageWidget()](#dtor.KMessageWidget)
- [void addAction(QAction \*action)](#addAction)
- [void clearActions()](#clearActions)
- [QIcon icon() const](#icon)
- [bool isCloseButtonVisible() const](#isCloseButtonVisible)
- [bool isHideAnimationRunning() const](#isHideAnimationRunning)
- [bool isShowAnimationRunning() const](#isShowAnimationRunning)
- [KMessageWidget::MessageType messageType() const](#messageType)
- [KMessageWidget::Position position() const](#position) (since 6.0)
- [void removeAction(QAction \*action)](#removeAction)
- [void setTextFormat(Qt::TextFormat textFormat)](#setTextFormat) (since 6.0)
- [QString text() const](#text)
- [Qt::TextFormat textFormat() const](#textFormat) (since 6.0)
- [bool wordWrap() const](#wordWrap)

## Public Slots

- [void animatedHide()](#animatedHide)
- [void animatedShow()](#animatedShow)
- [void setCloseButtonVisible(bool visible)](#setCloseButtonVisible)
- [void setIcon(const QIcon &icon)](#setIcon)
- [void setMessageType(KMessageWidget::MessageType type)](#setMessageType)
- [void setPosition(KMessageWidget::Position position)](#setPosition) (since 6.0)
- [void setText(const QString &text)](#setText)
- [void setWordWrap(bool wordWrap)](#setWordWrap)

## Signals

- [void hideAnimationFinished()](#hideAnimationFinished)
- [void linkActivated(const QString &contents)](#linkActivated)
- [void linkHovered(const QString &contents)](#linkHovered)
- [void showAnimationFinished()](#showAnimationFinished)

## Detailed Description {#details}

[KMessageWidget](kmessagewidget.md) can be used to provide inline positive or negative feedback, or to implement opportunistic interactions.

As a feedback widget, [KMessageWidget](kmessagewidget.md) provides a less intrusive alternative to "OK Only" message boxes. If you want to avoid a modal [KMessageBox](kmessagebox.md), consider using [KMessageWidget](kmessagewidget.md) instead.

Examples of [KMessageWidget](kmessagewidget.md) look as follows, all of them having an icon set with [setIcon](kmessagewidget.md#setIcon)(), and the first three show a close button:

### Negative feedback {#negative-feedback}

The [KMessageWidget](kmessagewidget.md) can be used as a secondary indicator of failure: the first indicator is usually the fact the action the user expected to happen did not happen.

Example: User fills a form, clicks "Submit".

- Expected feedback: form closes
- First indicator of failure: form stays there
- Second indicator of failure: a [KMessageWidget](kmessagewidget.md) appears on top of the form, explaining the error condition

When used to provide negative feedback, [KMessageWidget](kmessagewidget.md) should be placed close to its context. In the case of a form, it should appear on top of the form entries.

[KMessageWidget](kmessagewidget.md) should get inserted in the existing layout. Space should not be reserved for it, otherwise it becomes "dead space", ignored by the user. [KMessageWidget](kmessagewidget.md) should also not appear as an overlay to prevent blocking access to elements the user needs to interact with to fix the failure.

### Positive feedback {#positive-feedback}

[KMessageWidget](kmessagewidget.md) can be used for positive feedback but it shouldn't be overused. It is often enough to provide feedback by simply showing the results of an action.

Examples of acceptable uses:

- Confirm success of "critical" transactions
- Indicate completion of background tasks

Example of unadapted uses:

- Indicate successful saving of a file
- Indicate a file has been successfully removed

### Opportunistic interaction {#opportunistic-interaction}

Opportunistic interaction is the situation where the application suggests to the user an action he could be interested in perform, either based on an action the user just triggered or an event which the application noticed.

Example of acceptable uses:

- A browser can propose remembering a recently entered password
- A music collection can propose ripping a CD which just got inserted
- A chat application may notify the user a "special friend" just connected

## Member Type Documentation {#member-type-documentation}

### enum KMessageWidget::MessageType {#MessageType-enum}

Available message types. The background colors are chosen depending on the message type.

| Constant | Value | Description |
| --- | --- | --- |
| `KMessageWidget::Positive` | `0` | Positive message type |
| `KMessageWidget::Information` | `1` | Information message type |
| `KMessageWidget::Warning` | `2` | Warning message type |
| `KMessageWidget::Error` | `3` | Error message type |

### \[since 6.0\] enum KMessageWidget::Position {#Position-enum}

Position of the [KMessageWidget](kmessagewidget.md)

This will update the look of the [KMessageWidget](kmessagewidget.md) to be appropriate to the position.

| Constant | Value | Description |
| --- | --- | --- |
| `KMessageWidget::Inline` | `0` | The message widget is display inside the content. |
| `KMessageWidget::Header` | `1` | The message widget is displayed as header. |
| `KMessageWidget::Footer` | `2` | The message widget is displayed as footer. |

This enum was introduced in Qt 6.0.

## Property Documentation {#property-documentation}

### closeButtonVisible : bool {#closeButtonVisible-prop}

**Access functions:**

- `bool` **[isCloseButtonVisible](kmessagewidget.md#isCloseButtonVisible)**() const
- `void` **[setCloseButtonVisible](kmessagewidget.md#setCloseButtonVisible)**(`bool` *visible*)

### icon : QIcon {#icon-prop}

**Access functions:**

- `QIcon` **[icon](kmessagewidget.md#icon)**() const
- `void` **[setIcon](kmessagewidget.md#setIcon)**(const `QIcon` &*icon*)

### messageType : MessageType {#messageType-prop}

**Access functions:**

- `KMessageWidget::MessageType` **[messageType](kmessagewidget.md#messageType)**() const
- `void` **[setMessageType](kmessagewidget.md#setMessageType)**(`KMessageWidget::MessageType` *type*)

### position : Position {#position-prop}

**Access functions:**

- `KMessageWidget::Position` **[position](kmessagewidget.md#position)**() const
- `void` **[setPosition](kmessagewidget.md#setPosition)**(`KMessageWidget::Position` *position*)

### text : QString {#text-prop}

**Access functions:**

- `QString` **[text](kmessagewidget.md#text)**() const
- `void` **[setText](kmessagewidget.md#setText)**(const `QString` &*text*)

### textFormat : Qt::TextFormat {#textFormat-prop}

**Access functions:**

- `Qt::TextFormat` **[textFormat](kmessagewidget.md#textFormat)**() const
- `void` **[setTextFormat](kmessagewidget.md#setTextFormat)**(`Qt::TextFormat` *textFormat*)

### wordWrap : bool {#wordWrap-prop}

**Access functions:**

- `bool` **[wordWrap](kmessagewidget.md#wordWrap)**() const
- `void` **[setWordWrap](kmessagewidget.md#setWordWrap)**(`bool` *wordWrap*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KMessageWidget::KMessageWidget(QWidget \**parent* = nullptr) {#KMessageWidget}

Constructs a [KMessageWidget](kmessagewidget.md) with the specified `parent`.

### \[explicit\] KMessageWidget::KMessageWidget(const QString &*text*, QWidget \**parent* = nullptr) {#KMessageWidget-1}

Constructs a [KMessageWidget](kmessagewidget.md) with the specified `parent` and contents `text`.

### \[override virtual noexcept\] KMessageWidget::~KMessageWidget() {#dtor.KMessageWidget}

Destructor.

### void KMessageWidget::addAction(QAction \**action*) {#addAction}

Add `action` to the message widget.

For each action a button is added to the message widget in the order the actions were added.

`action` the action to add

*See also* [removeAction](kmessagewidget.md#removeAction)(), [QWidget::actions](https://doc.qt.io/qt-6/qwidget.html#actions)()

### \[slot\] void KMessageWidget::animatedHide() {#animatedHide}

Hide the widget using an animation.

### \[slot\] void KMessageWidget::animatedShow() {#animatedShow}

Show the widget using an animation.

### void KMessageWidget::clearActions() {#clearActions}

Clears all actions from the message widget.

*See also* [KMessageWidget::MessageType](kmessagewidget.md#MessageType-enum), [addAction](kmessagewidget.md#addAction)(), [removeAction](kmessagewidget.md#removeAction)()

### \[signal\] void KMessageWidget::hideAnimationFinished() {#hideAnimationFinished}

This signal is emitted when the hide animation is finished, started by calling [animatedHide](kmessagewidget.md#animatedHide)(). If animations are disabled, this signal is emitted immediately after the message widget got hidden.

> **Note:** This signal is not emitted if the widget was hidden by calling [hide](https://doc.qt.io/qt-6/qwidget.html#hide)(), so this signal is only useful in conjunction with [animatedHide](kmessagewidget.md#animatedHide)().

*See also* [animatedHide](kmessagewidget.md#animatedHide)()

### QIcon KMessageWidget::icon() const {#icon}

The icon shown on the left of the text. By default, no icon is shown.

> **Note:** Getter function for property [icon](kmessagewidget.md#icon-prop).

*See also* [setIcon](kmessagewidget.md#setIcon)()

### bool KMessageWidget::isCloseButtonVisible() const {#isCloseButtonVisible}

Check whether the close button is visible.

> **Note:** Getter function for property [closeButtonVisible](kmessagewidget.md#closeButtonVisible-prop).

*See also* [setCloseButtonVisible](kmessagewidget.md#setCloseButtonVisible)()

### bool KMessageWidget::isHideAnimationRunning() const {#isHideAnimationRunning}

Check whether the hide animation started by calling [animatedHide](kmessagewidget.md#animatedHide)() is still running. If animations are disabled, this function always returns `false`.

*See also* [animatedHide](kmessagewidget.md#animatedHide)(), [hideAnimationFinished](kmessagewidget.md#hideAnimationFinished)()

### bool KMessageWidget::isShowAnimationRunning() const {#isShowAnimationRunning}

Check whether the show animation started by calling [animatedShow](kmessagewidget.md#animatedShow)() is still running. If animations are disabled, this function always returns `false`.

*See also* [animatedShow](kmessagewidget.md#animatedShow)(), [showAnimationFinished](kmessagewidget.md#showAnimationFinished)()

### \[signal\] void KMessageWidget::linkActivated(const QString &*contents*) {#linkActivated}

This signal is emitted when the user clicks a link in the text label.

The URL referred to by the href anchor is passed in contents.

`contents` text of the href anchor

*See also* [QLabel::linkActivated](https://doc.qt.io/qt-6/qlabel.html#linkActivated)()

### \[signal\] void KMessageWidget::linkHovered(const QString &*contents*) {#linkHovered}

This signal is emitted when the user hovers over a link in the text label.

The URL referred to by the href anchor is passed in contents.

`contents` text of the href anchor

*See also* [QLabel::linkHovered](https://doc.qt.io/qt-6/qlabel.html#linkHovered)()

### KMessageWidget::MessageType KMessageWidget::messageType() const {#messageType}

Get the type of this message. By default, the type is set to [KMessageWidget::Information](kmessagewidget.md#MessageType-enum).

> **Note:** Getter function for property [messageType](kmessagewidget.md#messageType-prop).

*See also* [KMessageWidget::MessageType](kmessagewidget.md#MessageType-enum), [setMessageType](kmessagewidget.md#setMessageType)()

### \[since 6.0\] KMessageWidget::Position KMessageWidget::position() const {#position}

Get the position of this message. By default this is [KMessageWidget::Inline](kmessagewidget.md#Position-enum).

> **Note:** Getter function for property [position](kmessagewidget.md#position-prop).

This function was introduced in Qt 6.0.

*See also* [setPosition](kmessagewidget.md#setPosition)()

### void KMessageWidget::removeAction(QAction \**action*) {#removeAction}

Remove `action` from the message widget.

`action` the action to remove

*See also* [KMessageWidget::MessageType](kmessagewidget.md#MessageType-enum), [addAction](kmessagewidget.md#addAction)(), [setMessageType](kmessagewidget.md#setMessageType)()

### \[slot\] void KMessageWidget::setCloseButtonVisible(bool *visible*) {#setCloseButtonVisible}

Set the visibility of the close button. If `visible` is `true`, a close button is shown that calls [animatedHide](kmessagewidget.md#animatedHide)() if clicked.

By default the close button is set to be visible.

> **Note:** Setter function for property [closeButtonVisible](kmessagewidget.md#closeButtonVisible-prop).

*See also* [isCloseButtonVisible](kmessagewidget.md#isCloseButtonVisible)(), closeButtonVisible(), [animatedHide](kmessagewidget.md#animatedHide)()

### \[slot\] void KMessageWidget::setIcon(const QIcon &*icon*) {#setIcon}

Define an icon to be shown on the left of the text

> **Note:** Setter function for property [icon](kmessagewidget.md#icon-prop).

*See also* [icon](kmessagewidget.md#icon)()

### \[slot\] void KMessageWidget::setMessageType(KMessageWidget::MessageType *type*) {#setMessageType}

Set the message type to `type`. By default, the message type is set to [KMessageWidget::Information](kmessagewidget.md#MessageType-enum). Appropriate colors are chosen to mimic the appearance of Kirigami's InlineMessage.

> **Note:** Setter function for property [messageType](kmessagewidget.md#messageType-prop).

*See also* [messageType](kmessagewidget.md#messageType)(), [KMessageWidget::MessageType](kmessagewidget.md#MessageType-enum)

### \[slot, since 6.0\] void KMessageWidget::setPosition(KMessageWidget::Position *position*) {#setPosition}

Set the position of this message

> **Note:** Setter function for property [position](kmessagewidget.md#position-prop).

This function was introduced in Qt 6.0.

*See also* [position](kmessagewidget.md#position)()

### \[slot\] void KMessageWidget::setText(const QString &*text*) {#setText}

Set the text of the message widget to `text`. If the message widget is already visible, the text changes on the fly.

`text` the text to display, rich text is allowed

> **Note:** Setter function for property [text](kmessagewidget.md#text-prop).

*See also* [text](kmessagewidget.md#text)()

### \[since 6.0\] void KMessageWidget::setTextFormat(Qt::TextFormat *textFormat*) {#setTextFormat}

Set the text format of the message widget's label.

> **Note:** Setter function for property [textFormat](kmessagewidget.md#textFormat-prop).

This function was introduced in Qt 6.0.

*See also* [textFormat](kmessagewidget.md#textFormat)(), [QLabel::setTextFormat](https://doc.qt.io/qt-6/qlabel.html#textFormat-prop)()

### \[slot\] void KMessageWidget::setWordWrap(bool *wordWrap*) {#setWordWrap}

Set word wrap to `wordWrap`. If word wrap is enabled, the [text](kmessagewidget.md#text)() of the message widget is wrapped to fit the available width. If word wrap is disabled, the message widget's minimum size is such that the entire text fits.

By default word wrap is disabled.

`wordWrap` disable/enable word wrap

> **Note:** Setter function for property [wordWrap](kmessagewidget.md#wordWrap-prop).

*See also* [wordWrap](kmessagewidget.md#wordWrap)()

### \[signal\] void KMessageWidget::showAnimationFinished() {#showAnimationFinished}

This signal is emitted when the show animation is finished, started by calling [animatedShow](kmessagewidget.md#animatedShow)(). If animations are disabled, this signal is emitted immediately after the message widget got shown.

> **Note:** This signal is not emitted if the widget was shown by calling [show](https://doc.qt.io/qt-6/qwidget.html#show)(), so this signal is only useful in conjunction with [animatedShow](kmessagewidget.md#animatedShow)().

*See also* [animatedShow](kmessagewidget.md#animatedShow)()

### QString KMessageWidget::text() const {#text}

Get the text of this message widget.

> **Note:** Getter function for property [text](kmessagewidget.md#text-prop).

*See also* [setText](kmessagewidget.md#setText)()

### \[since 6.0\] Qt::TextFormat KMessageWidget::textFormat() const {#textFormat}

Get the text format of the message widget's label.

> **Note:** Getter function for property [textFormat](kmessagewidget.md#textFormat-prop).

This function was introduced in Qt 6.0.

*See also* [setTextFormat](kmessagewidget.md#setTextFormat)(), [QLabel::textFormat](https://doc.qt.io/qt-6/qlabel.html#textFormat-prop)()

### bool KMessageWidget::wordWrap() const {#wordWrap}

Check whether word wrap is enabled.

If word wrap is enabled, the message widget wraps the displayed text as required to the available width of the widget. This is useful to avoid breaking widget layouts.

> **Note:** Getter function for property [wordWrap](kmessagewidget.md#wordWrap-prop).

*See also* [setWordWrap](kmessagewidget.md#setWordWrap)()
