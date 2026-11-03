---
title: "KTextEditor::DocumentCursor Class"
description: "A Cursor which is bound to a specific Document."
---

# KTextEditor::DocumentCursor Class

A Cursor which is bound to a specific Document. [More...](#details)

- **Header:** `#include <KTextEditor/DocumentCursor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`

[List of all members, including inherited members](ktexteditor-documentcursor-members.md)

## Public Types

- [enum DocumentCursor::WrapBehavior](#WrapBehavior-enum)

## Public Functions

- [DocumentCursor()](#DocumentCursor)
- [DocumentCursor(KTextEditor::Document \*document)](#DocumentCursor-1)
- [DocumentCursor(KTextEditor::Document \*document, KTextEditor::Cursor position)](#DocumentCursor-3)
- [DocumentCursor(KTextEditor::Document \*document, int line, int column)](#DocumentCursor-4)
- [DocumentCursor(const KTextEditor::DocumentCursor &other)](#DocumentCursor-2)
- [~DocumentCursor()](#dtor.DocumentCursor)
- [bool atEndOfDocument() const](#atEndOfDocument)
- [bool atEndOfLine() const](#atEndOfLine)
- [bool atStartOfDocument() const](#atStartOfDocument)
- [bool atStartOfLine() const](#atStartOfLine)
- [int column() const](#column)
- [KTextEditor::Document \*document() const](#document)
- [bool gotoNextLine()](#gotoNextLine)
- [bool gotoPreviousLine()](#gotoPreviousLine)
- [bool isValid() const](#isValid)
- [bool isValidTextPosition() const](#isValidTextPosition)
- [int line() const](#line)
- [void makeValid()](#makeValid)
- [bool move(int chars, KTextEditor::DocumentCursor::WrapBehavior wrapBehavior = Wrap)](#move)
- [void setColumn(int column)](#setColumn)
- [void setLine(int line)](#setLine)
- [void setPosition(KTextEditor::Cursor position)](#setPosition)
- [void setPosition(int line, int column)](#setPosition-1)
- [KTextEditor::Cursor toCursor() const](#toCursor)
- [DocumentCursor::operator Cursor() const](#operator-KTextEditor-3a-3aCursor)
- [KTextEditor::DocumentCursor &DocumentCursor::operator=(const KTextEditor::DocumentCursor &other)](#operator-eq)

## Detailed Description {#details}

### Introduction {#introduction}

A [DocumentCursor](ktexteditor-documentcursor.md) is an extension of the basic Cursor class. The [DocumentCursor](ktexteditor-documentcursor.md) is bound to a specific Document instance. This way, the cursor provides additional functions like [gotoNextLine](ktexteditor-documentcursor.md#gotoNextLine)(), [gotoPreviousLine](ktexteditor-documentcursor.md#gotoPreviousLine)() and [move](ktexteditor-documentcursor.md#move)() according to the [WrapBehavior](ktexteditor-documentcursor.md#WrapBehavior-enum).

The only difference to a [MovingCursor](ktexteditor-movingcursor.md) is that the [DocumentCursor](ktexteditor-documentcursor.md)'s position does not automatically move on text manipulation.

### Validity {#validity}

When constructing a [DocumentCursor](ktexteditor-documentcursor.md), a valid document pointer is required in the constructor. A null pointer will assert in debug builds. Further, a [DocumentCursor](ktexteditor-documentcursor.md) should only be used as long as the Document exists, otherwise the [DocumentCursor](ktexteditor-documentcursor.md) contains a dangling pointer to the previously assigned Document.

### Example {#example}

A [DocumentCursor](ktexteditor-documentcursor.md) is created and used like this:

```cpp
KTextEditor::DocumentCursor docCursor(document);
docCursor.setPosition(0, 0);
docCursor.gotoNextLine();
docCursor.move(5); // move 5 characters to the right
```

*See also* [KTextEditor::Cursor](ktexteditor-index.md), [KTextEditor::MovingCursor](ktexteditor-index.md)

## Member Type Documentation {#member-type-documentation}

### enum DocumentCursor::WrapBehavior {#WrapBehavior-enum}

Wrap behavior for end of line treatment used in [move](ktexteditor-documentcursor.md#move)().

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::DocumentCursor::Wrap` | `0x0` | Wrap at end of line. |
| `KTextEditor::DocumentCursor::NoWrap` | `0x1` | Do not wrap at end of line. |

## Member Function Documentation {#member-function-documentation}

### DocumentCursor::DocumentCursor() {#DocumentCursor}

no default constructor, as we need a document.

### DocumentCursor::DocumentCursor(KTextEditor::Document \**document*) {#DocumentCursor-1}

Constructor that creates a [DocumentCursor](ktexteditor-documentcursor.md) at the `invalid` position (-1, -1).

*See also* [isValid](ktexteditor-documentcursor.md#isValid)()

### DocumentCursor::DocumentCursor(KTextEditor::Document \**document*, KTextEditor::Cursor *position*) {#DocumentCursor-3}

Constructor that creates a [DocumentCursor](ktexteditor-documentcursor.md) located at `position`.

### DocumentCursor::DocumentCursor(KTextEditor::Document \**document*, int *line*, int *column*) {#DocumentCursor-4}

Constructor that creates a [DocumentCursor](ktexteditor-documentcursor.md) located at `line` and `column`.

### DocumentCursor::DocumentCursor(const KTextEditor::DocumentCursor &*other*) {#DocumentCursor-2}

Copy constructor. Make sure the Document of the [DocumentCursor](ktexteditor-documentcursor.md) is valid.

### \[noexcept\] DocumentCursor::~DocumentCursor() {#dtor.DocumentCursor}

Destruct the moving cursor.

### bool DocumentCursor::atEndOfDocument() const {#atEndOfDocument}

Determine if this cursor is located at the end of the last line in the document.

Returns `true` if the cursor is at the end of the document, otherwise `false`.

### bool DocumentCursor::atEndOfLine() const {#atEndOfLine}

Determine if this cursor is located at the end of the current line.

Returns `true` if the cursor is situated at the end of the line, otherwise `false`.

### bool DocumentCursor::atStartOfDocument() const {#atStartOfDocument}

Determine if this cursor is located at line 0 and column 0.

Returns `true` if the cursor is at start of the document, otherwise `false`.

### bool DocumentCursor::atStartOfLine() const {#atStartOfLine}

Determine if this cursor is located at column 0 of a valid text line.

Returns `true` if cursor is a valid text position and [column](ktexteditor-documentcursor.md#column)()=0, otherwise `false`.

### int DocumentCursor::column() const {#column}

Retrieve the column on which this cursor is situated. Returns column number, where 0 is the first column.

*See also* [setColumn](ktexteditor-documentcursor.md#setColumn)()

### KTextEditor::Document \*DocumentCursor::document() const {#document}

Gets the document to which this cursor is bound. Returns a pointer to the document

### bool DocumentCursor::gotoNextLine() {#gotoNextLine}

Moves the cursor to the next line and sets the column to 0. If the cursor position is already in the last line of the document, the cursor position remains unchanged and the return value is `false`.

Returns `true` on success, otherwise `false`

### bool DocumentCursor::gotoPreviousLine() {#gotoPreviousLine}

Moves the cursor to the previous line and sets the column to 0. If the cursor position is already in line 0, the cursor position remains unchanged and the return value is `false`.

Returns `true` on success, otherwise `false`

### bool DocumentCursor::isValid() const {#isValid}

Check if the current position of this cursor is a valid position, i.e. whether [line](ktexteditor-documentcursor.md#line)() \>= 0 and [column](ktexteditor-documentcursor.md#column)() \>= 0. Returns `true`, if the cursor position is valid, otherwise `false`

*See also* [KTextEditor::Cursor::isValid()](ktexteditor-index.md), [isValidTextPosition](ktexteditor-documentcursor.md#isValidTextPosition)()

### bool DocumentCursor::isValidTextPosition() const {#isValidTextPosition}

Returns true if this cursor is currently at a valid text position. A cursor position at (line, column) is valid, if

- line \>= 0 and line \< lines() holds, and
- column \>= 0 and column \<= lineLength(column).

The text position is also invalid if it is inside a Unicode surrogate. Therefore, use this function when iterating over the characters of a line.

*See also* [KTextEditor::Document::isValidTextPosition()](ktexteditor-index.md), [isValid](ktexteditor-documentcursor.md#isValid)()

### int DocumentCursor::line() const {#line}

Retrieve the line on which this cursor is situated. Returns line number, where 0 is the first line.

*See also* [setLine](ktexteditor-documentcursor.md#setLine)()

### void DocumentCursor::makeValid() {#makeValid}

Make sure the cursor position is at a valid text position according to the following rules.

- If the cursor is invalid(), i.e. either line \< 0 or column \< 0, it is set to (0, 0).
- If the cursor's line is past the number of lines in the document, the cursor is set to [Document::documentEnd](ktexteditor-document.md#documentEnd)().
- If the cursor's column is past the line length, the cursor column is set to the line length.
- If the cursor is inside a Unicode surrogate, the cursor is moved to the beginning of the Unicode surrogate.

After calling makeValid(), the cursor is guaranteed to be located at a valid text position.

*See also* [isValidTextPosition](ktexteditor-documentcursor.md#isValidTextPosition)(), [isValid](ktexteditor-documentcursor.md#isValid)()

### bool DocumentCursor::move(int *chars*, KTextEditor::DocumentCursor::WrapBehavior *wrapBehavior* = Wrap) {#move}

Moves the cursor `chars` character forward or backwards. If `wrapBehavior` equals [WrapBehavior::Wrap](ktexteditor-documentcursor.md#WrapBehavior-enum), the cursor is automatically wrapped to the next line at the end of a line.

When moving backwards, the [WrapBehavior](ktexteditor-documentcursor.md#WrapBehavior-enum) does not have any effect.

> **Note:** If the cursor could not be moved the amount of chars requested, the cursor is not moved at all!

Returns `true` on success, otherwise `false`

### void DocumentCursor::setColumn(int *column*) {#setColumn}

Set the cursor column to `column`. The cursor's line number is not changed.

`column` is the new cursor column

*See also* [column](ktexteditor-documentcursor.md#column)()

### void DocumentCursor::setLine(int *line*) {#setLine}

Set the cursor line to `line`. The cursor's column is not changed.

`line` is the new cursor line

*See also* [line](ktexteditor-documentcursor.md#line)()

### void DocumentCursor::setPosition(KTextEditor::Cursor *position*) {#setPosition}

Set the current cursor position to `position`. If `position` is not valid, meaning that either its line \< 0 or its column \< 0, then the document cursor will also be invalid

`position` is new cursor position

### void DocumentCursor::setPosition(int *line*, int *column*) {#setPosition-1}

Set the cursor position to `line` and `column`.

`line` is the new cursor line

`column` is the new cursor column

This is an overloaded function.

### KTextEditor::Cursor DocumentCursor::toCursor() const {#toCursor}

Convert this clever cursor into a dumb one. Returns normal cursor

### DocumentCursor::operator KTextEditor::Cursor() const {#operator-KTextEditor-3a-3aCursor}

Convert this clever cursor into a dumb one. Equal to [toCursor](ktexteditor-documentcursor.md#toCursor), allowing to use implicit conversion. Returns normal cursor

### KTextEditor::DocumentCursor &DocumentCursor::operator=(const KTextEditor::DocumentCursor &*other*) {#operator-eq}

Assignment operator. Same as the copy constructor. Make sure that the assigned Document is a valid document pointer.

`other` is the [DocumentCursor](ktexteditor-documentcursor.md) to assign to this

## Related Non-Members {#related-non-members}

### bool operator!=(KTextEditor::DocumentCursor *c1*, KTextEditor::DocumentCursor *c2*) {#operator-not-eq}

Inequality operator.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns `true`, if c1's and c2's assigned document, line and column are `not` equal.

### bool operator\<(KTextEditor::DocumentCursor *c1*, KTextEditor::DocumentCursor *c2*) {#operator-lt}

Less than operator.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns `true`, if c1's position is greater than or equal to c2's position, otherwise `false`.

### bool operator\<=(KTextEditor::DocumentCursor *c1*, KTextEditor::DocumentCursor *c2*) {#operator-lt-eq}

Less than or equal to operator.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns `true`, if c1's position is lesser than or equal to c2's position, otherwise `false`.

### bool operator==(KTextEditor::DocumentCursor *c1*, KTextEditor::DocumentCursor *c2*) {#operator-eq-eq}

Equality operator.

> **Note:** comparison between two invalid cursors is undefined. comparison between an invalid and a valid cursor will always be `false`.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns `true`, if c1's and c2's assigned document, line and column are `equal`.

### bool operator\>(KTextEditor::DocumentCursor *c1*, KTextEditor::DocumentCursor *c2*) {#operator-gt}

Greater than operator.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns `true`, if c1's position is greater than c2's position, otherwise `false`.

### bool operator\>=(KTextEditor::DocumentCursor *c1*, KTextEditor::DocumentCursor *c2*) {#operator-gt-eq}

Greater than or equal to operator.

`c1` is the first cursor to compare

`c2` is the second cursor to compare

Returns `true`, if c1's position is greater than or equal to c2's position, otherwise `false`.
