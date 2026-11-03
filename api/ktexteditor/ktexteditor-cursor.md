---
title: "KTextEditor::Cursor Class"
description: "The Cursor represents a position in a Document."
---

# KTextEditor::Cursor Class

The Cursor represents a position in a Document. [More...](#details)

- **Header:** `#include <KTextEditor/Cursor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`

[List of all members, including inherited members](ktexteditor-cursor-members.md)

## Public Functions

- [Cursor()](#Cursor)
- [Cursor(int line, int column)](#Cursor-1)
- [bool atStartOfDocument() const](#atStartOfDocument)
- [bool atStartOfLine() const](#atStartOfLine)
- [int column() const](#column)
- [bool isValid() const](#isValid)
- [int line() const](#line)
- [void position(int &line, int &column) const](#position)
- [void setColumn(int column)](#setColumn)
- [void setLine(int line)](#setLine)
- [void setPosition(KTextEditor::Cursor position)](#setPosition)
- [void setPosition(int line, int column)](#setPosition-1)
- [QString toString() const](#toString)

## Static Public Members

- [KTextEditor::Cursor fromString(QStringView str)](#fromString)
- [KTextEditor::Cursor invalid()](#invalid)
- [KTextEditor::Cursor start()](#start)

## Detailed Description {#details}

Introduction

A Cursor represents a position in a Document through a tuple of two int%s, namely the [line](ktexteditor-cursor.md#line)() and [column](ktexteditor-cursor.md#column)(). A Cursor maintains no affiliation with a particular Document, meaning that it remains constant if not changed through the Cursor API.

Important Notes

Working with a cursor, one should be aware of the following notes:

- Lines and columns start a 0.
- The Cursor class is designed to be passed by value (only 8 Bytes).
- Think of cursors as having their position at the start of a character, not in the middle of one.
- [invalid](ktexteditor-cursor.md#invalid)() Cursor%s are located at (-1, -1). In addition, a Cursor is [invalid](ktexteditor-cursor.md#invalid)(), if either its [line](ktexteditor-cursor.md#line)() and/or its [column](ktexteditor-cursor.md#column)() is arbitrarily negative, i.e. \< 0.
- All Cursor%s with [line](ktexteditor-cursor.md#line)() \>= 0 and [column](ktexteditor-cursor.md#column)() \>= 0 are valid. In this case [isValid](ktexteditor-cursor.md#isValid)() returns *true*.
- A Cursor has a non-virtual destructor. Hence, you cannot derive from Cursor.

Cursor Efficiency

The Cursor consists of just two int%s, the [line](ktexteditor-cursor.md#line)() and the [column](ktexteditor-cursor.md#column)(). Therefore, a Cursor instance takes 8 Bytes of memory. Further, a Cursor is a non-virtual class, turning it into a primitive old data type (POD). Thus, it can be moved and copied very efficiently.

Additional Concepts

In addition to the Cursor, the [KTextEditor](ktexteditor-module.md) API provides advanced concepts:

- The [DocumentCursor](ktexteditor-documentcursor.md) is a Cursor bound to a specific Document. In addition to the Cursor API, it provides convenience functions like [DocumentCursor::isValidTextPosition](ktexteditor-documentcursor.md#isValidTextPosition)() or [DocumentCursor::move](ktexteditor-documentcursor.md#move)(). The [DocumentCursor](ktexteditor-documentcursor.md) does not maintain its position, though.
- The [MovingCursor](ktexteditor-movingcursor.md) is also bound to a specific Document. In addition to the [DocumentCursor](ktexteditor-documentcursor.md), the [MovingCursor](ktexteditor-movingcursor.md) maintains its position, meaning that whenever the Document changes, the [MovingCursor](ktexteditor-movingcursor.md) moves, too.
- The Cursor forms the basis for the Range.

*See also* [DocumentCursor](ktexteditor-documentcursor.md), [MovingCursor](ktexteditor-movingcursor.md), [Range](ktexteditor-range.md)

## Member Function Documentation {#member-function-documentation}

### \[constexpr noexcept\] Cursor::Cursor() {#Cursor}

The default constructor creates a cursor at position (0, 0).

### \[constexpr noexcept\] Cursor::Cursor(int *line*, int *column*) {#Cursor-1}

This constructor creates a cursor initialized to a line and column.

`line` is the line the cursor is to be positioned on

`column` is the column the cursor is to be positioned on

### \[constexpr noexcept\] bool Cursor::atStartOfDocument() const {#atStartOfDocument}

Determine if this cursor is located at the start of a document (= at position (0, 0)). Returns *true* if the cursor is situated at the start of the document, *false* if it isn't.

### \[constexpr noexcept\] bool Cursor::atStartOfLine() const {#atStartOfLine}

Determine if this cursor is located at the start of a line (= at column 0). Returns *true* if the cursor is situated at the start of the line, *false* if it isn't.

### \[constexpr noexcept\] int Cursor::column() const {#column}

Retrieve the column on which this cursor is situated. Returns column number, where 0 is the first column.

*See also* [setColumn](ktexteditor-cursor.md#setColumn)()

### \[static noexcept\] KTextEditor::Cursor Cursor::fromString(QStringView *str*) {#fromString}

Returns a Cursor created from the string `str` containing the format "(line, column)". In case the string cannot be parsed, [Cursor::invalid](ktexteditor-cursor.md#invalid)() is returned.

*See also* [toString](ktexteditor-cursor.md#toString)()

### \[static constexpr noexcept\] KTextEditor::Cursor Cursor::invalid() {#invalid}

Returns an invalid cursor. The returned cursor position is set to (-1, -1).

*See also* [isValid](ktexteditor-cursor.md#isValid)()

### \[constexpr noexcept\] bool Cursor::isValid() const {#isValid}

Returns whether the current position of this cursor is a valid position (line + column must both be \>= 0).

> **Note:** If you want to check, whether a cursor position is a valid *text-position*, use [DocumentCursor::isValidTextPosition](ktexteditor-documentcursor.md#isValidTextPosition)(), or [Document::isValidTextPosition](ktexteditor-document.md#isValidTextPosition)().

### \[constexpr noexcept\] int Cursor::line() const {#line}

Retrieve the line on which this cursor is situated. Returns line number, where 0 is the first line.

*See also* [setLine](ktexteditor-cursor.md#setLine)()

### \[noexcept\] void Cursor::position(int &*line*, int &*column*) const {#position}

Get both the line and column of the cursor position.

`line` will be filled with current cursor line

`column` will be filled with current cursor column

*See also* [setPosition](ktexteditor-cursor.md#setPosition)()

### \[noexcept\] void Cursor::setColumn(int *column*) {#setColumn}

Set the cursor column to *column*.

`column` is the new cursor column

*See also* [column](ktexteditor-cursor.md#column)()

### \[noexcept\] void Cursor::setLine(int *line*) {#setLine}

Set the cursor line to *line*.

`line` is the new cursor line

*See also* [line](ktexteditor-cursor.md#line)()

### \[noexcept\] void Cursor::setPosition(KTextEditor::Cursor *position*) {#setPosition}

Set the current cursor position to *position*.

`position` is the new cursor position

*See also* [position](ktexteditor-cursor.md#position)()

### \[noexcept\] void Cursor::setPosition(int *line*, int *column*) {#setPosition-1}

Set the cursor position to *line* and *column*.

`line` is the new cursor line

`column` is the new cursor column

This is an overloaded function.

### \[static constexpr noexcept\] KTextEditor::Cursor Cursor::start() {#start}

Returns a cursor representing the start of any document - i.e., line 0, column 0.

### QString Cursor::toString() const {#toString}

Returns the cursor position as string in the format "(line, column)".

*See also* [fromString](ktexteditor-cursor.md#fromString)()

## Related Non-Members {#related-non-members}

### \[constexpr noexcept\] bool operator!=(KTextEditor::Cursor *c1*, KTextEditor::Cursor *c2*) {#operator-not-eq}

Inequality operator.

`c1` is first cursor to compare

`c2` is second cursor to compare

Returns *true*, if c1's and c2's line and column are *not* equal.

### \[noexcept\] KTextEditor::Cursor &operator+=(KTextEditor::Cursor &*c1*, KTextEditor::Cursor *c2*) {#operator-2b-eq}

Addition assignment operator. Adds `c2` to this cursor.

`c1` is the cursor being added to

`c2` is the position to add

Returns a reference to the cursor which has just been added to

### \[noexcept\] KTextEditor::Cursor &operator-=(KTextEditor::Cursor &*c1*, KTextEditor::Cursor *c2*) {#operator--eq}

Subtraction assignment operator. Subtracts `c2` from `c1`.

`c1` is the cursor being subtracted from

`c2` is the position to subtract

Returns a reference to the cursor which has just been subtracted from

### \[constexpr noexcept\] bool operator\<(KTextEditor::Cursor *c1*, KTextEditor::Cursor *c2*) {#operator-lt}

Less than operator.

`c1` is first cursor to compare

`c2` is second cursor to compare

Returns *true*, if c1's position is greater than or equal to c2's position, otherwise *false*.

### QDebug operator\<\<(QDebug *s*, KTextEditor::Cursor *cursor*) {#operator-lt-lt}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this cursor to the debug output in a nicely formatted way.

`s` is the debug output stream

`cursor` is the cursor to write

### \[constexpr noexcept\] bool operator\<=(KTextEditor::Cursor *c1*, KTextEditor::Cursor *c2*) {#operator-lt-eq}

Less than or equal to operator.

`c1` is first cursor to compare

`c2` is second cursor to compare

Returns *true*, if c1's position is lesser than or equal to c2's position, otherwise *false*.

### \[constexpr noexcept\] bool operator==(KTextEditor::Cursor *c1*, KTextEditor::Cursor *c2*) {#operator-eq-eq}

Equality operator.

> **Note:** comparison between two invalid cursors is undefined. comparison between and invalid and a valid cursor will always be *false*.

`c1` is first cursor to compare

`c2` is second cursor to compare

Returns *true*, if c1's and c2's line and column are *equal*.

### \[constexpr noexcept\] bool operator\>(KTextEditor::Cursor *c1*, KTextEditor::Cursor *c2*) {#operator-gt}

Greater than operator.

`c1` is first cursor to compare

`c2` is second cursor to compare

Returns *true*, if c1's position is greater than c2's position, otherwise *false*.

### \[constexpr noexcept\] bool operator\>=(KTextEditor::Cursor *c1*, KTextEditor::Cursor *c2*) {#operator-gt-eq}

Greater than or equal to operator.

`c1` is first cursor to compare

`c2` is second cursor to compare

Returns *true*, if c1's position is greater than or equal to c2's position, otherwise *false*.
