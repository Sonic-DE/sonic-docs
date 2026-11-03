---
title: "KTextEditor Namespace"
description: "Full text editor component."
---

# KTextEditor Namespace

Full text editor component. [More...](#details)

- Header: KTextEditor/Editor
- CMake: find\_package(KF6 REQUIRED COMPONENTS TextEditor) target\_link\_libraries(mytarget PRIVATE KF6::TextEditor)

## Detailed Description {#details}

The [KTextEditor](ktexteditor-module.md) namespace contains all the public API that is required to use the [KTextEditor](ktexteditor-module.md) component. Using the [KTextEditor](ktexteditor-module.md) interfaces is described in the article index.

> **Warning:** All classes that are *not* part of the [KTextEditor](ktexteditor-module.md) namespace are internal and subject to change. We mean it!

## Classes {#classes}

### class [Application](ktexteditor-application.md)

This class allows the application that embeds the [KTextEditor](ktexteditor-module.md) component to allow it access to application wide information and interactions.

### class [Attribute](ktexteditor-attribute.md)

A class which provides customized text decorations.

### class [CodeCompletionModel](ktexteditor-codecompletionmodel.md)

An item model for providing code completion, and meta information for enhanced presentation.

### class [CodeCompletionModelControllerInterface](ktexteditor-codecompletionmodelcontrollerinterface.md)

Controller interface for a [CodeCompletionModel](ktexteditor-codecompletionmodel.md) instance.

### class [Command](ktexteditor-command.md)

An Editor command line command.

### class [ConfigPage](ktexteditor-configpage.md)

Config page interface for the Editor and Plugin%s.

### class [Cursor](ktexteditor-cursor.md)

The Cursor represents a position in a Document.

### class [Document](ktexteditor-document.md)

A [KParts](../kparts/kparts-module.md) derived class representing a text document.

### class [DocumentCursor](ktexteditor-documentcursor.md)

A Cursor which is bound to a specific Document.

### class [Editor](ktexteditor-editor.md)

Accessor interface for the [KTextEditor](ktexteditor-module.md) framework.

### class [LineRange](ktexteditor-linerange.md)

An object representing lines from a start line to an end line.

### class [MainWindow](ktexteditor-mainwindow.md)

This class allows the application that embeds the [KTextEditor](ktexteditor-module.md) component to allow it to access parts of its main window.

### class [Message](ktexteditor-message.md)

This class holds a Message to display in Views.

### class [MovingCursor](ktexteditor-movingcursor.md)

A Cursor which is bound to a specific Document, and maintains its position.

### class [MovingRange](ktexteditor-movingrange.md)

A range that is bound to a specific Document, and maintains its position.

### class [MovingRangeFeedback](ktexteditor-movingrangefeedback.md)

A class which provides notifications of state changes to a [MovingRange](ktexteditor-movingrange.md).

### class [Range](ktexteditor-range.md)

An object representing a section of text, from one Cursor to another.

### class [View](ktexteditor-view.md)

A text widget with [KXMLGUIClient](../kxmlgui/kxmlguiclient.md) that represents a Document.

## Type Documentation {#type-documentation}

### enum SearchOption {#SearchOption-enum}

**flags KTextEditor::SearchOptions**

Search flags for use with [Document::searchText](ktexteditor-document.md#searchText)().

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::Document::Default` | `0` | Search for a case-sensitive plaintext pattern, without processing of escape sequences, with "whole words" off, in forward direction, within a non-block-mode text range. |
| `KTextEditor::Document::Regex` | `1 << 1` | Treats the pattern as a regular expression |
| `KTextEditor::Document::CaseInsensitive` | `1 << 4` | Ignores case, e.g. "a" matches "A" |
| `KTextEditor::Document::Backwards` | `1 << 5` | Searches in backward direction |
| `KTextEditor::Document::EscapeSequences` | `1 << 10` | Plaintext mode: processes escape sequences |
| `KTextEditor::Document::WholeWords` | `1 << 11` | Plaintext mode: searches whole words only, e.g. **not** "amp" in "example" |

The `SearchOptions` type is a typedef for `QFlags<SearchOption>. `It stores an OR combination of `SearchOption` values.

## Function Documentation {#function-documentation}

### QDebug operator\<\<(QDebug *s*, const KTextEditor::MovingCursor &*cursor*) {#operator-lt-lt}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this cursor to the debug output in a nicely formatted way.

`s` is the debug stream

`cursor` is the cursor to print

Returns debug stream

### QDebug operator\<\<(QDebug *s*, const KTextEditor::MovingRange &*range*) {#operator-lt-lt}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this range to the debug output in a nicely formatted way.

`s` is the debug stream

`range` is the range to print

Returns debug stream

### QDebug operator\<\<(QDebug *s*, const KTextEditor::MovingCursor \**cursor*) {#operator-lt-lt-1}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this cursor to the debug output in a nicely formatted way.

`s` is the debug stream

`cursor` is the cursor to print

Returns debug stream

### QDebug operator\<\<(QDebug *s*, const KTextEditor::MovingRange \**range*) {#operator-lt-lt-1}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this range to the debug output in a nicely formatted way.

`s` is the debug stream

`range` is the range to print

Returns debug stream
