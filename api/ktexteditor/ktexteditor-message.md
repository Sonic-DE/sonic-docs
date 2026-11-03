---
title: "KTextEditor::Message Class"
description: "This class holds a Message to display in Views."
---

# KTextEditor::Message Class

This class holds a Message to display in Views. [More...](#details)

- **Header:** `#include <KTextEditor/Message>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ktexteditor-message-members.md)

## Public Types

- [enum Message::AutoHideMode](#AutoHideMode-enum)
- [enum Message::MessagePosition](#MessagePosition-enum)
- [enum Message::MessageType](#MessageType-enum)

## Public Functions

- [Message(const QString &richtext, KTextEditor::Message::MessageType type = Message::Information)](#Message)
- [~Message()](#dtor.Message)
- [QList\<QAction \*\> actions() const](#actions)
- [void addAction(QAction \*action, bool closeOnTrigger = true)](#addAction)
- [int autoHide() const](#autoHide)
- [KTextEditor::Message::AutoHideMode autoHideMode() const](#autoHideMode)
- [KTextEditor::Document \*document() const](#document)
- [QIcon icon() const](#icon)
- [KTextEditor::Message::MessageType messageType() const](#messageType)
- [KTextEditor::Message::MessagePosition position() const](#position)
- [int priority() const](#priority)
- [void setAutoHide(int delay = 0)](#setAutoHide)
- [void setAutoHideMode(KTextEditor::Message::AutoHideMode mode)](#setAutoHideMode)
- [void setDocument(KTextEditor::Document \*document)](#setDocument)
- [void setPosition(KTextEditor::Message::MessagePosition position)](#setPosition)
- [void setPriority(int priority)](#setPriority)
- [void setView(KTextEditor::View \*view)](#setView)
- [void setWordWrap(bool wordWrap)](#setWordWrap)
- [QString text() const](#text)
- [KTextEditor::View \*view() const](#view)
- [bool wordWrap() const](#wordWrap)

## Public Slots

- [void setIcon(const QIcon &icon)](#setIcon)
- [void setText(const QString &richtext)](#setText)

## Signals

- [void closed(KTextEditor::Message \*message)](#closed)
- [void iconChanged(const QIcon &icon)](#iconChanged)
- [void textChanged(const QString &text)](#textChanged)

## Detailed Description {#details}

### Introduction {#introduction}

The Message class holds the data used to display interactive message widgets in the editor. Use the [Document::postMessage](ktexteditor-document.md#postMessage)() to post a message as follows:

```cpp
// always use a QPointer to guard your Message, if you keep a pointer
// after calling postMessage()
QPointer<KTextEditor::Message> message =
    new KTextEditor::Message("text", KTextEditor::Message::Information);
message->setWordWrap(true);
message->addAction(...); // add your actions...
document->postMessage(message);
```

A Message is deleted automatically if the Message gets closed, meaning that you usually can forget the pointer. If you really need to delete a message before the user processed it, always guard it with a [QPointer](https://doc.qt.io/qt-6/qpointer.html)!

### Message Creation and Deletion {#message-creation-and-deletion}

To create a new Message, use code like this:

```cpp
QPointer<KTextEditor::Message> message =
    new KTextEditor::Message("My information text", KTextEditor::Message::Information);
message->setWordWrap(true);
// ...
```

Although discouraged in general, the text of the Message can be changed on the fly when it is already visible with [setText](ktexteditor-message.md#setText)().

Once you posted the Message through [Document::postMessage](ktexteditor-document.md#postMessage)(), the lifetime depends on the user interaction. The Message gets automatically deleted either if the user clicks a closing action in the message, or for instance if the document is reloaded.

If you posted a message but want to remove it yourself again, just delete the message. But beware of the following warning!

> **Warning:** Always use [QPointer](https://doc.qt.io/qt-6/qpointer.html)\<Message\> to guard the message pointer from getting invalid, if you need to access the Message after you posted it.

### Positioning {#positioning}

By default, the Message appears right above of the View. However, if desired, the position can be changed through [setPosition](ktexteditor-message.md#setPosition)(). For instance, the search-and-replace code in Kate Part shows the number of performed replacements in a message floating in the view. For further information, have a look at the enum [MessagePosition](ktexteditor-message.md#MessagePosition-enum).

### Autohiding Messages {#autohiding-messages}

Message%s can be shown for only a short amount of time by using the autohide feature. With [setAutoHide](ktexteditor-message.md#setAutoHide)() a timeout in milliseconds can be set after which the Message is automatically hidden. Further, use [setAutoHideMode](ktexteditor-message.md#setAutoHideMode)() to either trigger the autohide timer as soon as the widget is shown ([AutoHideMode::Immediate](ktexteditor-message.md#AutoHideMode-enum)), or only after user interaction with the view ([AutoHideMode::AfterUserInteraction](ktexteditor-message.md#AutoHideMode-enum)).

The default autohide mode is set to [AutoHideMode::AfterUserInteraction](ktexteditor-message.md#AutoHideMode-enum). This way, it is unlikely the user misses a notification.

## Member Type Documentation {#member-type-documentation}

### enum Message::AutoHideMode {#AutoHideMode-enum}

The AutoHideMode determines when to trigger the [autoHide](ktexteditor-message.md#autoHide) timer.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::Message::Immediate` | `0` | Auto-hide is triggered as soon as the message is shown |
| `KTextEditor::Message::AfterUserInteraction` | `1` | Auto-hide is triggered only after the user interacted with the view |

*See also* [setAutoHide](ktexteditor-message.md#setAutoHide)(), [autoHide](ktexteditor-message.md#autoHide)()

### enum Message::MessagePosition {#MessagePosition-enum}

Message position used to place the message either above or below of the [KTextEditor::View](ktexteditor-view.md).

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::Message::AboveView` | `0` | Show message above view. |
| `KTextEditor::Message::BelowView` | `1` | Show message below view. |
| `KTextEditor::Message::TopInView` | `2` | Show message as view overlay in the top right corner. |
| `KTextEditor::Message::BottomInView` | `3` | Show message as view overlay in the bottom right corner. |
| `KTextEditor::Message::CenterInView` | `4` | Show message as view overlay in the center of the view. |

### enum Message::MessageType {#MessageType-enum}

Message types used as visual indicator.

The message types match exactly the behavior of KMessageWidget::MessageType. For simple notifications either use Positive or Information.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::Message::Positive` | `0` | Positive information message |
| `KTextEditor::Message::Information` | `1` | Information message type |
| `KTextEditor::Message::Warning` | `2` | Warning message type |
| `KTextEditor::Message::Error` | `3` | Error message type |

## Member Function Documentation {#member-function-documentation}

### Message::Message(const QString &*richtext*, KTextEditor::Message::MessageType *type* = Message::Information) {#Message}

Constructor for new messages.

`type` is the message type, e.g. [MessageType::Information](ktexteditor-message.md#MessageType-enum)

`richtext` is the text to be displayed

### \[override virtual noexcept\] Message::~Message() {#dtor.Message}

Destructor.

### QList\<QAction \*\> Message::actions() const {#actions}

Accessor to all actions, mainly used in the internal implementation to add the actions into the gui.

*See also* [addAction](ktexteditor-message.md#addAction)()

### void Message::addAction(QAction \**action*, bool *closeOnTrigger* = true) {#addAction}

Adds an action to the message.

By default (`closeOnTrigger` = true), the action closes the message displayed in all Views. If `closeOnTrigger` is false, the message is stays open.

The actions will be displayed in the order you added the actions.

To connect to an action, use the following code:

```cpp
connect(action, &QAction::triggered, receiver, &ReceiverType::slotActionTriggered);
```

`action` is the action to be added

`closeOnTrigger` when triggered, the message widget is closed

> **Warning:** The added actions are deleted automatically. So do **not** delete the added actions yourself.

### int Message::autoHide() const {#autoHide}

Returns the auto hide time in milliseconds. Please refer to [setAutoHide](ktexteditor-message.md#setAutoHide)() for an explanation of the return value.

*See also* [setAutoHide](ktexteditor-message.md#setAutoHide)(), [autoHideMode](ktexteditor-message.md#autoHideMode)()

### KTextEditor::Message::AutoHideMode Message::autoHideMode() const {#autoHideMode}

Get the Message's auto hide mode. The default mode is set to [AutoHideMode::AfterUserInteraction](ktexteditor-message.md#AutoHideMode-enum).

*See also* [setAutoHideMode](ktexteditor-message.md#setAutoHideMode)(), [autoHide](ktexteditor-message.md#autoHide)()

### \[signal\] void Message::closed(KTextEditor::Message \**message*) {#closed}

This signal is emitted before the `message` is deleted. Afterwards, this pointer is invalid.

Use the function [document](ktexteditor-message.md#document)() to access the associated Document.

`message` the closed/processed message

### KTextEditor::Document \*Message::document() const {#document}

Returns the document pointer this message was posted in. This pointer is 0 as long as the message was not posted.

*See also* [setDocument](ktexteditor-message.md#setDocument)()

### QIcon Message::icon() const {#icon}

Returns the icon of this message. If the message has no icon set, a null icon is returned.

*See also* [setIcon](ktexteditor-message.md#setIcon)()

### \[signal\] void Message::iconChanged(const QIcon &*icon*) {#iconChanged}

This signal is emitted whenever [setIcon](ktexteditor-message.md#setIcon)() was called.

`icon` is the new notification icon

*See also* [setIcon](ktexteditor-message.md#setIcon)()

### KTextEditor::Message::MessageType Message::messageType() const {#messageType}

Returns the message type set in the constructor.

### KTextEditor::Message::MessagePosition Message::position() const {#position}

Returns the message position of this message.

*See also* [setPosition](ktexteditor-message.md#setPosition)(), [MessagePosition](ktexteditor-message.md#MessagePosition-enum)

### int Message::priority() const {#priority}

Returns the priority of the message.

*See also* [setPriority](ktexteditor-message.md#setPriority)()

### void Message::setAutoHide(int *delay* = 0) {#setAutoHide}

Set the auto hide time to `delay` milliseconds. If `delay` \< 0, auto hide is disabled. If `delay` = 0, auto hide is enabled and set to a sane default value of several seconds.

By default, auto hide is disabled.

*See also* [autoHide](ktexteditor-message.md#autoHide)(), [setAutoHideMode](ktexteditor-message.md#setAutoHideMode)()

### void Message::setAutoHideMode(KTextEditor::Message::AutoHideMode *mode*) {#setAutoHideMode}

Sets the auto hide mode to `mode`. The default mode is set to [AutoHideMode::AfterUserInteraction](ktexteditor-message.md#AutoHideMode-enum).

`mode` is the auto hide mode

*See also* [autoHideMode](ktexteditor-message.md#autoHideMode)(), [setAutoHide](ktexteditor-message.md#setAutoHide)()

### void Message::setDocument(KTextEditor::Document \**document*) {#setDocument}

Set the document pointer to `document`. This is called by the implementation, as soon as you post a message through [Document::postMessage](ktexteditor-document.md#postMessage)(), so that you do not have to call this yourself.

*See also* [document](ktexteditor-message.md#document)()

### \[slot\] void Message::setIcon(const QIcon &*icon*) {#setIcon}

Add an optional `icon` for this notification which will be shown next to the message text. If the message was already sent through [Document::postMessage](ktexteditor-document.md#postMessage)(), the displayed icon changes on the fly.

> **Note:** Change the icon on the fly with care, since changing the text may resize the notification widget, which may result in a distracting user experience.

`icon` is the icon to be displayed

*See also* [iconChanged](ktexteditor-message.md#iconChanged)()

### void Message::setPosition(KTextEditor::Message::MessagePosition *position*) {#setPosition}

Sets the position of the message to `position`. By default, the position is set to [MessagePosition::AboveView](ktexteditor-message.md#MessagePosition-enum).

*See also* [position](ktexteditor-message.md#position)(), [MessagePosition](ktexteditor-message.md#MessagePosition-enum)

### void Message::setPriority(int *priority*) {#setPriority}

Set the priority of this message to `priority`. Messages with higher priority are shown first. The default priority is 0.

*See also* [priority](ktexteditor-message.md#priority)()

### \[slot\] void Message::setText(const QString &*richtext*) {#setText}

Sets the notification contents to `richtext`. If the message was already sent through [Document::postMessage](ktexteditor-document.md#postMessage)(), the displayed text changes on the fly.

> **Note:** Change text on the fly with care, since changing the text may resize the notification widget, which may result in a distracting user experience.

`richtext` is the new notification text (rich text supported)

*See also* [textChanged](ktexteditor-message.md#textChanged)()

### void Message::setView(KTextEditor::View \**view*) {#setView}

Set the associated view of the message. If `view` is 0, the message is shown in all View%s of the Document. If `view` is given, i.e. non-zero, the message is shown only in this view. `view` the associated view the message should be displayed in

*See also* [view](ktexteditor-message.md#view)()

### void Message::setWordWrap(bool *wordWrap*) {#setWordWrap}

Enabled word wrap according to `wordWrap`. By default, auto wrap is disabled.

Word wrap is enabled automatically, if the Message's width is larger than the parent widget's width to avoid breaking the gui layout.

*See also* [wordWrap](ktexteditor-message.md#wordWrap)()

### QString Message::text() const {#text}

Returns the text set in the constructor.

*See also* [setText](ktexteditor-message.md#setText)()

### \[signal\] void Message::textChanged(const QString &*text*) {#textChanged}

This signal is emitted whenever [setText](ktexteditor-message.md#setText)() was called.

`text` the new notification text (rich text supported)

*See also* [setText](ktexteditor-message.md#setText)()

### KTextEditor::View \*Message::view() const {#view}

This function returns the view you set by [setView](ktexteditor-message.md#setView)(). If [setView](ktexteditor-message.md#setView)() was not called, the return value is 0.

*See also* [setView](ktexteditor-message.md#setView)()

### bool Message::wordWrap() const {#wordWrap}

Returns true if word wrap is enabled.

*See also* [setWordWrap](ktexteditor-message.md#setWordWrap)()
