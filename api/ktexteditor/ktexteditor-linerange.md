---
title: "KTextEditor::LineRange Class"
description: "An object representing lines from a start line to an end line."
---

# KTextEditor::LineRange Class

An object representing lines from a start line to an end line. [More...](#details)

- **Header:** `#include <KTextEditor/LineRange>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`

[List of all members, including inherited members](ktexteditor-linerange-members.md)

## Public Functions

- [LineRange()](#LineRange)
- [LineRange(int start, int end)](#LineRange-1)
- [bool confineToRange(KTextEditor::LineRange range)](#confineToRange)
- [bool contains(KTextEditor::LineRange range) const](#contains)
- [bool containsLine(int line) const](#containsLine)
- [KTextEditor::LineRange encompass(KTextEditor::LineRange range) const](#encompass)
- [int end() const](#end)
- [bool expandToRange(KTextEditor::LineRange range)](#expandToRange)
- [KTextEditor::LineRange intersect(KTextEditor::LineRange range) const](#intersect)
- [bool isValid() const](#isValid)
- [int numberOfLines() const](#numberOfLines)
- [bool onSingleLine() const](#onSingleLine)
- [bool overlaps(KTextEditor::LineRange range) const](#overlaps)
- [bool overlapsLine(int line) const](#overlapsLine)
- [void setBothLines(int line)](#setBothLines)
- [void setEnd(int end)](#setEnd)
- [void setRange(KTextEditor::LineRange range)](#setRange)
- [void setRange(int start, int end)](#setRange-1)
- [void setStart(int start)](#setStart)
- [int start() const](#start)
- [QString toString() const](#toString)

## Static Public Members

- [KTextEditor::LineRange fromString(QStringView str)](#fromString)
- [KTextEditor::LineRange invalid()](#invalid)

## Detailed Description {#details}

A [LineRange](ktexteditor-linerange.md) is a basic class which represents a range of lines, from a [start](ktexteditor-linerange.md#start)() line to an [end](ktexteditor-linerange.md#end)() line.

For simplicity and convenience, ranges always maintain their [start](ktexteditor-linerange.md#start)() line to be before or equal to their [end](ktexteditor-linerange.md#end)() line. Attempting to set either the start or end of the range beyond the respective end or start will result in both values being set to the specified line. In the constructor, the start and end will be swapped if necessary.

*See also* [Range](ktexteditor-range.md)

## Member Function Documentation {#member-function-documentation}

### \[constexpr noexcept\] LineRange::LineRange() {#LineRange}

Default constructor. Creates a valid line range with both start and end line set to 0.

### \[constexpr noexcept\] LineRange::LineRange(int *start*, int *end*) {#LineRange-1}

Constructor which creates a range from *start* to *end*. If start is after end, they will be swapped.

`start` is the start line

`end` is the end line

### \[noexcept\] bool LineRange::confineToRange(KTextEditor::LineRange *range*) {#confineToRange}

Confine this range if necessary to fit within `range`.

`range` range which should contain this range

Returns *true* if confinement occurred, *false* otherwise

### \[constexpr noexcept\] bool LineRange::contains(KTextEditor::LineRange *range*) const {#contains}

Check whether the this range wholly encompasses *range*.

`range` range to check

Returns *true*, if this range contains *range*, otherwise *false*

### \[constexpr noexcept\] bool LineRange::containsLine(int *line*) const {#containsLine}

Returns true if this range wholly encompasses `line`.

`line` line to check

Returns *true* if the line is wholly encompassed by this range, otherwise *false*.

### \[constexpr noexcept\] KTextEditor::LineRange LineRange::encompass(KTextEditor::LineRange *range*) const {#encompass}

Returns the smallest range which encompasses this line range and the supplied `range`.

`range` other range to encompass

Returns the smallest range which contains this range and the supplied `range`.

### \[constexpr noexcept\] int LineRange::end() const {#end}

Get the end line of this line range. This will always be \>= [start](ktexteditor-linerange.md#start)().

Returns the end line of this line range.

*See also* [setEnd](ktexteditor-linerange.md#setEnd)()

### \[noexcept\] bool LineRange::expandToRange(KTextEditor::LineRange *range*) {#expandToRange}

Expand this line range if necessary to contain `range`.

`range` range which this range should contain

Returns *true* if expansion occurred, *false* otherwise

### \[static noexcept\] KTextEditor::LineRange LineRange::fromString(QStringView *str*) {#fromString}

Returns a [LineRange](ktexteditor-linerange.md) created from the string `str` containing the format "\[start line, end line\]". In case the string cannot be parsed, an [LineRange::invalid](ktexteditor-linerange.md#invalid)() is returned.

*See also* [toString](ktexteditor-linerange.md#toString)()

### \[constexpr noexcept\] KTextEditor::LineRange LineRange::intersect(KTextEditor::LineRange *range*) const {#intersect}

Intersects this line range with another, returning the shared lines of the two line ranges.

`range` other line range to intersect with this

Returns the intersection of this range and the supplied `range`.

### \[static constexpr noexcept\] KTextEditor::LineRange LineRange::invalid() {#invalid}

Returns an invalid line range.

### \[constexpr noexcept\] bool LineRange::isValid() const {#isValid}

Validity check. In the base class, returns true unless the line range starts before (0,0).

### \[constexpr noexcept\] int LineRange::numberOfLines() const {#numberOfLines}

Returns the number of lines separating the [start](ktexteditor-linerange.md#start)() and [end](ktexteditor-linerange.md#end)() line.

Returns the number of lines separating the [start](ktexteditor-linerange.md#start)() and [end](ktexteditor-linerange.md#end)() line; 0 if the start and end lines are the same.

### \[constexpr noexcept\] bool LineRange::onSingleLine() const {#onSingleLine}

Check whether this line range is on one line.

Returns *true* if both the start and end line are equal, otherwise *false*

### \[constexpr noexcept\] bool LineRange::overlaps(KTextEditor::LineRange *range*) const {#overlaps}

Check whether the this range overlaps with *range*.

`range` range to check against

Returns *true*, if this range overlaps with *range*, otherwise *false*

### \[constexpr noexcept\] bool LineRange::overlapsLine(int *line*) const {#overlapsLine}

Check whether the range overlaps at least part of *line*.

`line` line to check

Returns *true*, if the range overlaps at least part of *line*, otherwise *false*

### \[noexcept\] void LineRange::setBothLines(int *line*) {#setBothLines}

Convenience function. Set the start and end lines to `line`.

`line` the line number to assign to [start](ktexteditor-linerange.md#start)() and [end](ktexteditor-linerange.md#end)()

### \[noexcept\] void LineRange::setEnd(int *end*) {#setEnd}

Set the end line to *end*.

> **Note:** If *end* is in front of current start, start and end will be set to new end value.

`end` new end line

*See also* [end](ktexteditor-linerange.md#end)()

### \[noexcept\] void LineRange::setRange(KTextEditor::LineRange *range*) {#setRange}

Set the start and end lines of the range.

> **Note:** If *start* is after *end*, they will be reversed.

`range` is the new range

### \[noexcept\] void LineRange::setRange(int *start*, int *end*) {#setRange-1}

Set the start and end lines of the range.

> **Note:** If *start* is after *end*, they will be reversed.

`start` is the start line of the range

`end` is the end line of the range

### \[noexcept\] void LineRange::setStart(int *start*) {#setStart}

Set the start line to *start*.

> **Note:** If *start* is after current end, start and end will be set to new start value.

`start` new start line

*See also* [start](ktexteditor-linerange.md#start)()

### \[constexpr noexcept\] int LineRange::start() const {#start}

Get the start line of this line range. This will always be \<= [end](ktexteditor-linerange.md#end)().

Returns the start line of this line range.

*See also* [setStart](ktexteditor-linerange.md#setStart)()

### QString LineRange::toString() const {#toString}

Returns the line range as string in the format "\[start line, end line\]".

*See also* [fromString](ktexteditor-linerange.md#fromString)()

## Related Non-Members {#related-non-members}

### \[constexpr noexcept\] bool operator!=(KTextEditor::LineRange *r1*, KTextEditor::LineRange *r2*) {#operator-not-eq}

Inequality operator.

`r1` is the first range to compare

`r2` is the second range to compare

Returns *true* if *r1* and *r2* do *not* equal, otherwise *false*

### \[noexcept\] KTextEditor::LineRange &operator&=(KTextEditor::LineRange &*r1*, KTextEditor::LineRange *r2*) {#operator-and-eq}

Intersects `r1` with `r2` and assigns the result to `r1`.

`r1` is the range to assign the intersection to

`r2` is the range to intersect `r1` with

Returns a reference to this range, after the intersection has taken place

### \[noexcept\] KTextEditor::LineRange &operator+=(KTextEditor::LineRange &*r1*, KTextEditor::LineRange *r2*) {#operator-2b-eq}

Addition assignment operator. Adds `r2` to this range.

`r1` is the first range

`r2` is the second range

Returns a reference to the line range which has just been added to

### \[noexcept\] KTextEditor::LineRange &operator-=(KTextEditor::LineRange &*r1*, KTextEditor::LineRange *r2*) {#operator--eq}

Subtraction assignment operator. Subtracts `r2` from `r1`.

`r1` is the first range

`r2` is the second range

Returns a reference to the range which has just been subtracted from

### \[constexpr noexcept\] bool operator\<(KTextEditor::LineRange *r1*, KTextEditor::LineRange *r2*) {#operator-lt}

Less than operator. Looks only at the lines of the two ranges, does not consider their size.

`r1` is the first range to compare

`r2` is the second range to compare

Returns *true* if *r1* ends before *r2* begins, otherwise *false*

### QDebug operator\<\<(QDebug *s*, KTextEditor::LineRange *range*) {#operator-lt-lt}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this range to the debug output in a nicely formatted way.

### \[constexpr noexcept\] bool operator==(KTextEditor::LineRange *r1*, KTextEditor::LineRange *r2*) {#operator-eq-eq}

Equality operator.

`r1` is the first range to compare

`r2` is the second range to compare

Returns *true* if *r1* and *r2* equal, otherwise *false*

### \[constexpr noexcept\] bool operator\>(KTextEditor::LineRange *r1*, KTextEditor::LineRange *r2*) {#operator-gt}

Greater than operator. Looks only at the lines of the two ranges, does not consider their size.

`r1` is the first range to compare

`r2` is the second range to compare

Returns *true* if *r1* starts after where *r2* ends, otherwise *false*
