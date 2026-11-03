---
title: "KTextEditor::Range Class"
description: "An object representing a section of text, from one Cursor to another."
---

# KTextEditor::Range Class

An object representing a section of text, from one Cursor to another. [More...](#details)

- **Header:** `#include <KTextEditor/Range>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`

[List of all members, including inherited members](ktexteditor-range-members.md)

## Public Functions

- [Range()](#Range)
- [Range(KTextEditor::Cursor start, KTextEditor::Cursor end)](#Range-1)
- [Range(KTextEditor::Cursor start, int width)](#Range-2)
- [Range(KTextEditor::Cursor start, int endLine, int endColumn)](#Range-3)
- [Range(int startLine, int startColumn, int endLine, int endColumn)](#Range-4)
- [bool boundaryAtCursor(KTextEditor::Cursor cursor) const](#boundaryAtCursor)
- [int columnWidth() const](#columnWidth)
- [bool confineToRange(KTextEditor::Range range)](#confineToRange)
- [bool contains(KTextEditor::Cursor cursor) const](#contains)
- [bool contains(KTextEditor::Range range) const](#contains-1)
- [bool containsColumn(int column) const](#containsColumn)
- [bool containsLine(int line) const](#containsLine)
- [KTextEditor::Range encompass(KTextEditor::Range range) const](#encompass)
- [KTextEditor::Cursor end() const](#end)
- [bool expandToRange(KTextEditor::Range range)](#expandToRange)
- [KTextEditor::Range intersect(KTextEditor::Range range) const](#intersect)
- [bool isEmpty() const](#isEmpty)
- [bool isValid() const](#isValid)
- [int numberOfLines() const](#numberOfLines)
- [bool onSingleLine() const](#onSingleLine)
- [bool overlaps(KTextEditor::Range range) const](#overlaps)
- [bool overlapsColumn(int column) const](#overlapsColumn)
- [bool overlapsLine(int line) const](#overlapsLine)
- [void setBothColumns(int column)](#setBothColumns)
- [void setBothLines(int line)](#setBothLines)
- [void setEnd(KTextEditor::Cursor end)](#setEnd)
- [void setRange(KTextEditor::Range range)](#setRange)
- [void setRange(KTextEditor::Cursor start, KTextEditor::Cursor end)](#setRange-1)
- [void setStart(KTextEditor::Cursor start)](#setStart)
- [KTextEditor::Cursor start() const](#start)
- [KTextEditor::LineRange toLineRange() const](#toLineRange)
- [QString toString() const](#toString)

## Static Public Members

- [KTextEditor::Range fromString(QStringView str)](#fromString)
- [KTextEditor::Range invalid()](#invalid)

## Detailed Description {#details}

A Range is a basic class which represents a range of text with two Cursors, from a [start](ktexteditor-range.md#start)() position to an [end](ktexteditor-range.md#end)() position.

For simplicity and convenience, ranges always maintain their start position to be before or equal to their end position. Attempting to set either the start or end of the range beyond the respective end or start will result in both values being set to the specified position. In the constructor, the start and end will be swapped if necessary.

If you want additional functionality such as the ability to maintain position in a document, see [MovingRange](ktexteditor-movingrange.md).

*See also* [MovingRange](ktexteditor-movingrange.md)

## Member Function Documentation {#member-function-documentation}

### \[constexpr noexcept\] Range::Range() {#Range}

Default constructor. Creates a valid range from position (0, 0) to position (0, 0).

*See also* [setRange](ktexteditor-range.md#setRange)()

### \[constexpr noexcept\] Range::Range(KTextEditor::Cursor *start*, KTextEditor::Cursor *end*) {#Range-1}

Constructor which creates a range from *start* to *end*. If start is after end, they will be swapped.

`start` is the start position

`end` is the end position

### \[constexpr noexcept\] Range::Range(KTextEditor::Cursor *start*, int *width*) {#Range-2}

Constructor which creates a single-line range from `start`, extending `width` characters along the same line.

`start` is the start position

`width` is the width of this range in columns along the same line

### \[constexpr noexcept\] Range::Range(KTextEditor::Cursor *start*, int *endLine*, int *endColumn*) {#Range-3}

Constructor which creates a range from `start`, to `endLine`, `endColumn`.

`start` is the start position

`endLine` is the end line

`endColumn` is the end column

### \[constexpr noexcept\] Range::Range(int *startLine*, int *startColumn*, int *endLine*, int *endColumn*) {#Range-4}

Constructor which creates a range from *startLine*, *startColumn* to *endLine*, *endColumn*.

`startLine` is the start line

`startColumn` is the start column

`endLine` is the end line

`endColumn` is the end column

### \[constexpr noexcept\] bool Range::boundaryAtCursor(KTextEditor::Cursor *cursor*) const {#boundaryAtCursor}

Check whether `cursor` is located at either of the [start](ktexteditor-range.md#start)() or [end](ktexteditor-range.md#end)() boundaries.

`cursor` is the cursor to check

Returns *true* if the cursor is equal to [start](ktexteditor-range.md#start)() or [end](ktexteditor-range.md#end)(), otherwise *false*.

### \[constexpr noexcept\] int Range::columnWidth() const {#columnWidth}

Returns the number of columns separating the [start](ktexteditor-range.md#start)() and [end](ktexteditor-range.md#end)() positions.

Returns the number of columns separating the [start](ktexteditor-range.md#start)() and [end](ktexteditor-range.md#end)() positions; 0 if the start and end columns are the same.

### \[noexcept\] bool Range::confineToRange(KTextEditor::Range *range*) {#confineToRange}

Confine this range if necessary to fit within `range`.

`range` is the range which should contain this range

Returns *true* if confinement occurred, *false* otherwise

### \[constexpr noexcept\] bool Range::contains(KTextEditor::Cursor *cursor*) const {#contains}

Check to see if `cursor` is contained within this range, ie \>= [start](ktexteditor-range.md#start)() and \< [end](ktexteditor-range.md#end)().

`cursor` is the position to test for containment

Returns *true* if the cursor is contained within this range, otherwise *false*.

### \[constexpr noexcept\] bool Range::contains(KTextEditor::Range *range*) const {#contains-1}

Check whether the this range wholly encompasses *range*.

`range` is the range to check

Returns *true*, if this range contains *range*, otherwise *false*

### \[constexpr noexcept\] bool Range::containsColumn(int *column*) const {#containsColumn}

Check whether the range contains *column*.

`column` is the column to check

Returns *true* if the range contains *column*, otherwise *false*

### \[constexpr noexcept\] bool Range::containsLine(int *line*) const {#containsLine}

Returns true if this range wholly encompasses `line`.

`line` is the line to check

Returns *true* if the line is wholly encompassed by this range, otherwise *false*.

### \[constexpr noexcept\] KTextEditor::Range Range::encompass(KTextEditor::Range *range*) const {#encompass}

Returns the smallest range which encompasses this range and the supplied `range`.

`range` is the other range to encompass

Returns the smallest range which contains this range and the supplied `range`.

### \[constexpr noexcept\] KTextEditor::Cursor Range::end() const {#end}

Get the end position of this range. This will always be \>= [start](ktexteditor-range.md#start)().

Returns const reference to the end position of this range.

*See also* [setEnd](ktexteditor-range.md#setEnd)()

### \[noexcept\] bool Range::expandToRange(KTextEditor::Range *range*) {#expandToRange}

Expand this range if necessary to contain `range`.

`range` is the range which this range should contain

Returns *true* if expansion occurred, *false* otherwise

### \[static noexcept\] KTextEditor::Range Range::fromString(QStringView *str*) {#fromString}

Returns a Range created from the string `str` containing the format "\[(start-line, start-column), (endl-line:end-column)\]". In case the string cannot be parsed, an [Range::invalid](ktexteditor-range.md#invalid)() is returned.

*See also* [toString](ktexteditor-range.md#toString)()

### \[constexpr noexcept\] KTextEditor::Range Range::intersect(KTextEditor::Range *range*) const {#intersect}

Intersects this range with another, returning the shared area of the two ranges.

`range` is the other range to intersect with this

Returns the intersection of this range and the supplied `range`.

### \[static constexpr noexcept\] KTextEditor::Range Range::invalid() {#invalid}

Returns an invalid range.

### \[constexpr noexcept\] bool Range::isEmpty() const {#isEmpty}

Returns true if this range contains no characters, ie. the [start](ktexteditor-range.md#start)() and [end](ktexteditor-range.md#end)() positions are the same.

Returns *true* if the range contains no characters, otherwise *false*

### \[constexpr noexcept\] bool Range::isValid() const {#isValid}

Validity check. In the base class, returns true unless the range starts before (0,0).

### \[constexpr noexcept\] int Range::numberOfLines() const {#numberOfLines}

Returns the number of lines separating the [start](ktexteditor-range.md#start)() and [end](ktexteditor-range.md#end)() positions.

Returns the number of lines separating the [start](ktexteditor-range.md#start)() and [end](ktexteditor-range.md#end)() positions; 0 if the start and end lines are the same.

### \[constexpr noexcept\] bool Range::onSingleLine() const {#onSingleLine}

Check whether this range is wholly contained within one line, ie. if the [start](ktexteditor-range.md#start)() and [end](ktexteditor-range.md#end)() positions are on the same line.

Returns *true* if both the start and end positions are on the same line, otherwise *false*

### \[constexpr noexcept\] bool Range::overlaps(KTextEditor::Range *range*) const {#overlaps}

Check whether the this range overlaps with *range*.

`range` is the range to check against

Returns *true*, if this range overlaps with *range*, otherwise *false*

### \[constexpr noexcept\] bool Range::overlapsColumn(int *column*) const {#overlapsColumn}

Check to see if this range overlaps `column`; that is, if `column` is between [start](ktexteditor-range.md#start)().column() and [end](ktexteditor-range.md#end)().column(). This function is most likely to be useful in relation to block text editing.

`column` is the column to test

Returns *true* if the column is between the range's starting and ending columns, otherwise *false*.

### \[constexpr noexcept\] bool Range::overlapsLine(int *line*) const {#overlapsLine}

Check whether the range overlaps at least part of *line*.

`line` is the line to check

Returns *true*, if the range overlaps at least part of *line*, otherwise *false*

### \[noexcept\] void Range::setBothColumns(int *column*) {#setBothColumns}

Convenience function. Set the start and end columns to `column`.

`column` is the column number to assign to [start](ktexteditor-range.md#start)() and [end](ktexteditor-range.md#end)()

### \[noexcept\] void Range::setBothLines(int *line*) {#setBothLines}

Convenience function. Set the start and end lines to `line`.

`line` is the line number to assign to [start](ktexteditor-range.md#start)() and [end](ktexteditor-range.md#end)()

### \[noexcept\] void Range::setEnd(KTextEditor::Cursor *end*) {#setEnd}

Set the end cursor to *end*.

> **Note:** If *end* is in front of current start, start and end will be set to new end value.

`end` is the new end cursor

*See also* [end](ktexteditor-range.md#end)()

### \[noexcept\] void Range::setRange(KTextEditor::Range *range*) {#setRange}

Set the start and end cursors to *range.start()* and *range.end()* respectively.

`range` is the range to assign to this range

### \[noexcept\] void Range::setRange(KTextEditor::Cursor *start*, KTextEditor::Cursor *end*) {#setRange-1}

\\n\\n Set the start and end cursors to *start* and *end* respectively.

> **Note:** If *start* is after *end*, they will be reversed.

`start` is the start cursor

`end` is the end cursor

This is an overloaded function.

### \[noexcept\] void Range::setStart(KTextEditor::Cursor *start*) {#setStart}

Set the start cursor to *start*.

> **Note:** If *start* is after current end, start and end will be set to new start value.

`start` is the new start cursor

*See also* [start](ktexteditor-range.md#start)()

### \[constexpr noexcept\] KTextEditor::Cursor Range::start() const {#start}

Get the start position of this range. This will always be \<= [end](ktexteditor-range.md#end)().

Returns const reference to the start position of this range.

*See also* [setStart](ktexteditor-range.md#setStart)()

### \[constexpr noexcept\] KTextEditor::LineRange Range::toLineRange() const {#toLineRange}

Convert this Range to a [LineRange](ktexteditor-linerange.md)

Returns [LineRange](ktexteditor-linerange.md) from the start line to the end line of this range.

### QString Range::toString() const {#toString}

Returns the cursor position as string in the format "start-line:start-column,endl-line:end-column".

*See also* [fromString](ktexteditor-range.md#fromString)()

## Related Non-Members {#related-non-members}

### \[constexpr noexcept\] bool operator!=(KTextEditor::Range *r1*, KTextEditor::Range *r2*) {#operator-not-eq}

Inequality operator.

`r1` is the first range to compare

`r2` is the second range to compare

Returns *true* if *r1* and *r2* do *not* equal, otherwise *false*

### \[noexcept\] KTextEditor::Range &operator&=(KTextEditor::Range &*r1*, KTextEditor::Range *r2*) {#operator-and-eq}

Intersects `r1` with `r2` and assigns the result to `r1`.

`r1` is the range to assign the intersection to

`r2` is the range to intersect `r1` with

Returns a reference to this range, after the intersection has taken place

### \[noexcept\] KTextEditor::Range &operator+=(KTextEditor::Range &*r1*, KTextEditor::Range *r2*) {#operator-2b-eq}

Addition assignment operator. Adds `r2` to this range.

`r1` is the first range

`r2` is the second range

Returns a reference to the cursor which has just been added to

### \[noexcept\] KTextEditor::Range &operator-=(KTextEditor::Range &*r1*, KTextEditor::Range *r2*) {#operator--eq}

Subtraction assignment operator. Subtracts `r2` from `r1`.

`r1` is the first range

`r2` is the second range

Returns a reference to the range which has just been subtracted from

### \[constexpr noexcept\] bool operator\<(KTextEditor::Range *r1*, KTextEditor::Range *r2*) {#operator-lt}

Less than operator. Looks only at the position of the two ranges, does not consider their size.

`r1` is the first range to compare

`r2` is the second range to compare

Returns *true* if *r1* ends before *r2* begins, otherwise *false*

### QDebug operator\<\<(QDebug *s*, KTextEditor::Range *range*) {#operator-lt-lt}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this range to the debug output in a nicely formatted way.

### \[constexpr noexcept\] bool operator==(KTextEditor::Range *r1*, KTextEditor::Range *r2*) {#operator-eq-eq}

Equality operator.

`r1` is the first range to compare

`r2` is the second range to compare

Returns *true* if *r1* and *r2* equal, otherwise *false*

### \[constexpr noexcept\] bool operator\>(KTextEditor::Range *r1*, KTextEditor::Range *r2*) {#operator-gt}

Greater than operator. Looks only at the position of the two ranges, does not consider their size.

`r1` is the first range to compare

`r2` is the second range to compare

Returns *true* if *r1* starts after where *r2* ends, otherwise *false*
