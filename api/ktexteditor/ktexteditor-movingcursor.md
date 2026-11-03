---
title: "KTextEditor::MovingCursor Class"
description: "A Cursor which is bound to a specific Document, and maintains its position."
---

# KTextEditor::MovingCursor Class

A Cursor which is bound to a specific Document, and maintains its position. [More...](#details)

- **Header:** `#include <KTextEditor/MovingCursor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Group:** MovingCursor is part of kte\_group\_moving\_classes

[List of all members, including inherited members](ktexteditor-movingcursor-members.md)

## Public Types

- [enum MovingCursor::InsertBehavior](#InsertBehavior-enum)
- [enum MovingCursor::WrapBehavior](#WrapBehavior-enum)

## Public Functions

- [MovingCursor(const KTextEditor::MovingCursor &)](#MovingCursor-1)
- [~MovingCursor()](#dtor.MovingCursor)
- [bool atEndOfDocument() const](#atEndOfDocument)
- [bool atEndOfLine() const](#atEndOfLine)
- [bool atStartOfDocument() const](#atStartOfDocument)
- [bool atStartOfLine() const](#atStartOfLine)
- [int column() const](#column)
- [KTextEditor::Document \*document() const](#document)
- [bool gotoNextLine()](#gotoNextLine)
- [bool gotoPreviousLine()](#gotoPreviousLine)
- [KTextEditor::MovingCursor::InsertBehavior insertBehavior() const](#insertBehavior)
- [bool isValid() const](#isValid)
- [bool isValidTextPosition() const](#isValidTextPosition)
- [int line() const](#line)
- [bool move(int chars, KTextEditor::MovingCursor::WrapBehavior wrapBehavior = Wrap)](#move)
- [KTextEditor::MovingRange \*range() const](#range)
- [void setColumn(int column)](#setColumn)
- [void setInsertBehavior(KTextEditor::MovingCursor::InsertBehavior insertBehavior)](#setInsertBehavior)
- [void setLine(int line)](#setLine)
- [void setPosition(KTextEditor::Cursor position)](#setPosition)
- [void setPosition(int line, int column)](#setPosition-1)
- [const KTextEditor::Cursor toCursor() const](#toCursor)
- [MovingCursor::operator Cursor() const](#operator-KTextEditor-3a-3aCursor)
- [KTextEditor::MovingCursor &MovingCursor::operator=(const KTextEditor::MovingCursor &)](#operator-eq)

## Protected Functions

- [MovingCursor()](#MovingCursor)

## Detailed Description {#details}

A [MovingCursor](ktexteditor-movingcursor.md) is an extension of the basic Cursor class. It maintains its position in the document. As a result of this, [MovingCursor](ktexteditor-movingcursor.md)%s may not be copied, as they need to maintain a connection to the associated Document.

Create a new [MovingCursor](ktexteditor-movingcursor.md) like this:

```cpp
auto* movingCursor = aDocument->newMovingCursor(position);
```

The ownership of the cursor is passed to the user. When finished with a [MovingCursor](ktexteditor-movingcursor.md), simply delete it.

*See also* [Cursor](ktexteditor-cursor.md), [Range](ktexteditor-range.md), [MovingRange](ktexteditor-movingrange.md), [Document](ktexteditor-document.md)

## Member Type Documentation {#member-type-documentation}

### enum MovingCursor::InsertBehavior {#InsertBehavior-enum}

Insert behavior of this cursor, should it stay if text is insert at its position or should it move.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::MovingCursor::StayOnInsert` | `0x0` | Stay on insert. |
| `KTextEditor::MovingCursor::MoveOnInsert` | `0x1` | Move on insert. |

### enum MovingCursor::WrapBehavior {#WrapBehavior-enum}

Wrap behavior for end of line treatment used in [move](ktexteditor-movingcursor.md#move)().

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::MovingCursor::Wrap` | `0x0` | Wrap at end of line |
| `KTextEditor::MovingCursor::NoWrap` | `0x1` | Do not wrap at end of line |

## Member Function Documentation {#member-function-documentation}

### \[protected\] MovingCursor::MovingCursor() {#MovingCursor}

For inherited class only.

### MovingCursor::MovingCursor(*const KTextEditor::MovingCursor &*) {#MovingCursor-1}

no copy constructor, don't allow this to be copied.

### \[virtual noexcept\] MovingCursor::~MovingCursor() {#dtor.MovingCursor}

Destruct the moving cursor.

### bool MovingCursor::atEndOfDocument() const {#atEndOfDocument}

Determine if this cursor is located at the end of the last line in the document.

Returns *true* if the cursor is at the end of the document, otherwise *false*.

### bool MovingCursor::atEndOfLine() const {#atEndOfLine}

Determine if this cursor is located at the end of the current line.

Returns *true* if the cursor is situated at the end of the line, otherwise *false*.

### bool MovingCursor::atStartOfDocument() const {#atStartOfDocument}

Determine if this cursor is located at line 0 and column 0.

Returns *true* if the cursor is at start of the document, otherwise *false*.

### bool MovingCursor::atStartOfLine() const {#atStartOfLine}

Determine if this cursor is located at column 0 of a valid text line.

Returns *true* if cursor is a valid text position and [column](ktexteditor-movingcursor.md#column)()=0, otherwise *false*.

### \[pure virtual\] int MovingCursor::column() const {#column}

Retrieve the column on which this cursor is situated.

Returns column number, where 0 is the first column.

*See also* [setColumn](ktexteditor-movingcursor.md#setColumn)()

### \[pure virtual\] KTextEditor::Document \*MovingCursor::document() const {#document}

Gets the document to which this cursor is bound.

Returns a pointer to the document

### bool MovingCursor::gotoNextLine() {#gotoNextLine}

Moves the cursor to the next line and sets the column to 0. If the cursor position is already in the last line of the document, the cursor position remains unchanged and the return value is *false*.

Returns *true* on success, otherwise *false*

### bool MovingCursor::gotoPreviousLine() {#gotoPreviousLine}

Moves the cursor to the previous line and sets the column to 0. If the cursor position is already in line 0, the cursor position remains unchanged and the return value is *false*.

Returns *true* on success, otherwise *false*

### \[pure virtual\] KTextEditor::MovingCursor::InsertBehavior MovingCursor::insertBehavior() const {#insertBehavior}

Get current insert behavior. Returns current insert behavior

*See also* [setInsertBehavior](ktexteditor-movingcursor.md#setInsertBehavior)()

### bool MovingCursor::isValid() const {#isValid}

Returns whether the current position of this cursor is a valid position, i.e. whether [line](ktexteditor-movingcursor.md#line)() \>= 0 and [column](ktexteditor-movingcursor.md#column)() \>= 0.

Returns *true* , if the cursor position is valid, otherwise *false*

### bool MovingCursor::isValidTextPosition() const {#isValidTextPosition}

Check whether this [MovingCursor](ktexteditor-movingcursor.md) is located at a valid text position.

A cursor position at (line, column) is valid, if:

- line \>= 0 and line \< [document](ktexteditor-movingcursor.md#document)()-\>lines() holds, and
- column \>= 0 and column \<= lineLength(column).

Further, the text position is also invalid if it is inside a Unicode surrogate (utf-32 character).

Returns *true*, if the cursor is a valid text position, otherwise *false*

*See also* [Document::isValidTextPosition](ktexteditor-document.md#isValidTextPosition)()

### \[pure virtual\] int MovingCursor::line() const {#line}

Retrieve the line on which this cursor is situated.

Returns line number, where 0 is the first line.

*See also* [setLine](ktexteditor-movingcursor.md#setLine)()

### bool MovingCursor::move(int *chars*, KTextEditor::MovingCursor::WrapBehavior *wrapBehavior* = Wrap) {#move}

Moves the cursor `chars` character forward or backwards. If `wrapBehavior` equals [WrapBehavior::Wrap](ktexteditor-movingcursor.md#WrapBehavior-enum), the cursor is automatically wrapped to the next line at the end of a line.

When moving backwards, the [WrapBehavior](ktexteditor-movingcursor.md#WrapBehavior-enum) does not have any effect.

> **Note:** If the cursor could not be moved the amount of chars requested, the cursor is not moved at all!

Returns *true* on success, otherwise *false*

### \[pure virtual\] KTextEditor::MovingRange \*MovingCursor::range() const {#range}

Get range this cursor belongs to, if any Returns range this pointer is part of, else 0

### void MovingCursor::setColumn(int *column*) {#setColumn}

Set the cursor column to *column*.

`column` is the new cursor column

*See also* [column](ktexteditor-movingcursor.md#column)()

### \[pure virtual\] void MovingCursor::setInsertBehavior(KTextEditor::MovingCursor::InsertBehavior *insertBehavior*) {#setInsertBehavior}

Set insert behavior.

`insertBehavior` is the new insert behavior

*See also* [insertBehavior](ktexteditor-movingcursor.md#insertBehavior)()

### void MovingCursor::setLine(int *line*) {#setLine}

Set the cursor line to *line*.

`line` is the new cursor line

*See also* [line](ktexteditor-movingcursor.md#line)()

### \[pure virtual\] void MovingCursor::setPosition(KTextEditor::Cursor *position*) {#setPosition}

Set the current cursor position to *position*.

`position` is the new cursor position

### void MovingCursor::setPosition(int *line*, int *column*) {#setPosition-1}

Set the cursor position to *line* and *column*.

`line` is the new cursor line

`column` is the new cursor column

This is an overloaded function.

### const KTextEditor::Cursor MovingCursor::toCursor() const {#toCursor}

Convert this clever cursor into a dumb one. Even if this cursor belongs to a range, the created one not. Returns normal cursor

### MovingCursor::operator KTextEditor::Cursor() const {#operator-KTextEditor-3a-3aCursor}

Convert this clever cursor into a dumb one. Equal to [toCursor](ktexteditor-movingcursor.md#toCursor), allowing to use implicit conversion. Even if this cursor belongs to a range, the created one not. Returns normal cursor

### KTextEditor::MovingCursor &MovingCursor::operator=(*const KTextEditor::MovingCursor &*) {#operator-eq}

no assignment operator, no copying around clever cursors.

## Related Non-Members {#related-non-members}

### bool operator!=(const KTextEditor::MovingCursor &*c1*, const KTextEditor::MovingCursor &*c2*) {#operator-not-eq}

Inequality operator.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns *true*, if c1's and c2's line and column are *not* equal.

### bool operator\<(const KTextEditor::MovingCursor &*c1*, const KTextEditor::MovingCursor &*c2*) {#operator-lt}

Less than operator.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns *true*, if c1's position is greater than or equal to c2's position, otherwise *false*.

### QDebug operator\<\<(QDebug *s*, const KTextEditor::MovingCursor &*cursor*) {#operator-lt-lt}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this cursor to the debug output in a nicely formatted way.

`s` is the debug stream

`cursor` is the cursor to print

Returns debug stream

### QDebug operator\<\<(QDebug *s*, const KTextEditor::MovingCursor \**cursor*) {#operator-lt-lt-1}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this cursor to the debug output in a nicely formatted way.

`s` is the debug stream

`cursor` is the cursor to print

Returns debug stream

### bool operator\<=(const KTextEditor::MovingCursor &*c1*, const KTextEditor::MovingCursor &*c2*) {#operator-lt-eq}

Less than or equal to operator.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns *true*, if c1's position is lesser than or equal to c2's position, otherwise *false*.

### bool operator==(const KTextEditor::MovingCursor &*c1*, const KTextEditor::MovingCursor &*c2*) {#operator-eq-eq}

Equality operator.

> **Note:** comparison between two invalid cursors is undefined. comparison between an invalid and a valid cursor will always be *false*.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns *true*, if c1's and c2's line and column are *equal*.

### bool operator\>(const KTextEditor::MovingCursor &*c1*, const KTextEditor::MovingCursor &*c2*) {#operator-gt}

Greater than operator.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns *true*, if c1's position is greater than c2's position, otherwise *false*.

### bool operator\>=(const KTextEditor::MovingCursor &*c1*, const KTextEditor::MovingCursor &*c2*) {#operator-gt-eq}

Greater than or equal to operator.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns *true*, if c1's position is greater than or equal to c2's position, otherwise *false*.
