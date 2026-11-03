---
title: "KTextEditor::MovingRange Class"
description: "A range that is bound to a specific Document, and maintains its position."
---

# KTextEditor::MovingRange Class

A range that is bound to a specific Document, and maintains its position. [More...](#details)

- **Header:** `#include <KTextEditor/MovingRange>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Group:** MovingRange is part of kte\_group\_moving\_classes

[List of all members, including inherited members](ktexteditor-movingrange-members.md)

## Public Types

- [enum MovingRange::EmptyBehavior](#EmptyBehavior-enum)
- [enum MovingRange::InsertBehavior](#InsertBehavior-enum)

## Public Functions

- [MovingRange(const KTextEditor::MovingRange &)](#MovingRange-1)
- [~MovingRange()](#dtor.MovingRange)
- [const Attribute::Ptr &attribute() const](#attribute)
- [bool attributeOnlyForViews() const](#attributeOnlyForViews)
- [bool contains(KTextEditor::Cursor cursor) const](#contains)
- [bool contains(const KTextEditor::Range &range) const](#contains-1)
- [bool containsColumn(int column) const](#containsColumn)
- [bool containsLine(int line) const](#containsLine)
- [KTextEditor::Document \*document() const](#document)
- [KTextEditor::MovingRange::EmptyBehavior emptyBehavior() const](#emptyBehavior)
- [const KTextEditor::MovingCursor &end() const](#end)
- [KTextEditor::MovingRangeFeedback \*feedback() const](#feedback)
- [KTextEditor::MovingRange::InsertBehaviors insertBehaviors() const](#insertBehaviors)
- [bool isEmpty() const](#isEmpty)
- [int numberOfLines() const](#numberOfLines)
- [bool onSingleLine() const](#onSingleLine)
- [bool overlaps(const KTextEditor::Range &range) const](#overlaps)
- [bool overlapsColumn(int column) const](#overlapsColumn)
- [bool overlapsLine(int line) const](#overlapsLine)
- [void setAttribute(Attribute::Ptr attribute)](#setAttribute)
- [void setAttributeOnlyForViews(bool onlyForViews)](#setAttributeOnlyForViews)
- [void setEmptyBehavior(KTextEditor::MovingRange::EmptyBehavior emptyBehavior)](#setEmptyBehavior)
- [void setFeedback(KTextEditor::MovingRangeFeedback \*feedback)](#setFeedback)
- [void setInsertBehaviors(KTextEditor::MovingRange::InsertBehaviors insertBehaviors)](#setInsertBehaviors)
- [void setRange(KTextEditor::Range range)](#setRange)
- [void setRange(KTextEditor::Range range, Attribute::Ptr attribute)](#setRange-1) (since 6.0)
- [void setRange(KTextEditor::Range range, Attribute::Ptr attribute, qreal zDepth)](#setRange-2) (since 6.0)
- [void setRange(KTextEditor::Cursor start, KTextEditor::Cursor end)](#setRange-3)
- [void setView(KTextEditor::View \*view)](#setView)
- [void setZDepth(qreal zDepth)](#setZDepth)
- [const KTextEditor::MovingCursor &start() const](#start)
- [KTextEditor::LineRange toLineRange() const](#toLineRange)
- [const KTextEditor::Range toRange() const](#toRange)
- [KTextEditor::View \*view() const](#view)
- [qreal zDepth() const](#zDepth)
- [MovingRange::operator Range() const](#operator-KTextEditor-3a-3aRange)
- [KTextEditor::MovingRange &MovingRange::operator=(const KTextEditor::MovingRange &)](#operator-eq)

## Protected Functions

- [MovingRange()](#MovingRange)

## Detailed Description {#details}

### Introduction {#introduction}

A [MovingRange](ktexteditor-movingrange.md) is an extension of the basic Range class. It maintains its position in the document. As a result of this, [MovingRange](ktexteditor-movingrange.md)%s may not be copied, as they need to maintain a connection to the associated Document.

Create a new [MovingRange](ktexteditor-movingrange.md) like this:

```cpp
auto* movingRange = aDocument->newMovingRange(range);
```

The ownership of the range is passed to the user. When finished with a [MovingRange](ktexteditor-movingrange.md), simply delete it.

### Editing Behavior {#editing-behavior}

The insert behavior controls how the range reacts to characters inserted at the range boundaries, i.e. at the start of the range or the end of the range. Either the range boundary moves with text insertion, or it stays. Use [setInsertBehaviors](ktexteditor-movingrange.md#setInsertBehaviors)() and [insertBehaviors](ktexteditor-movingrange.md#insertBehaviors)() to set and query the current insert behavior.

When the [start](ktexteditor-movingrange.md#start)() and [end](ktexteditor-movingrange.md#end)() Cursor of a range equal, [isEmpty](ktexteditor-movingrange.md#isEmpty)() returns true. Further, the empty-behavior can be changed such that the [start](ktexteditor-movingrange.md#start)() and [end](ktexteditor-movingrange.md#end)() Cursor%s of [MovingRange](ktexteditor-movingrange.md)%s that get empty are automatically set to (-1, -1). Use [setEmptyBehavior](ktexteditor-movingrange.md#setEmptyBehavior)() and [emptyBehavior](ktexteditor-movingrange.md#emptyBehavior)() to control the empty behavior.

> **Warning:** MovingRanges may be set to (-1, -1, -1, -1) at any time, if the user reloads a document (F5)! Use a [MovingRangeFeedback](ktexteditor-movingrangefeedback.md) to get notified if you need to catch this case, and/or listen to the signal [Document::aboutToInvalidateMovingInterfaceContent](ktexteditor-document.md#aboutToInvalidateMovingInterfaceContent)().

### MovingRange Feedback {#movingrange-feedback}

With [setFeedback](ktexteditor-movingrange.md#setFeedback)() a feedback instance can be associated with the moving range. The [MovingRangeFeedback](ktexteditor-movingrangefeedback.md) notifies about the following events:

- the text cursor (caret) entered the range,
- the text cursor (caret) left the range,
- the mouse cursor entered the range,
- the mouse cursor left the range,
- the range became empty, i.e. [start](ktexteditor-movingrange.md#start)() == [end](ktexteditor-movingrange.md#end)(),
- the range became invalid, i.e. [start](ktexteditor-movingrange.md#start)() == [end](ktexteditor-movingrange.md#end)() == (-1, -1).

If a feedback is not needed anymore, call [setFeedback](ktexteditor-movingrange.md#setFeedback)(0).

### Working with Ranges {#working-with-ranges}

There are several convenience methods that make working with MovingRanges very simple. For instance, use [isEmpty](ktexteditor-movingrange.md#isEmpty)() to check if the [start](ktexteditor-movingrange.md#start)() Cursor equals the [end](ktexteditor-movingrange.md#end)() Cursor. Use [contains](ktexteditor-movingrange.md#contains)(), [containsLine](ktexteditor-movingrange.md#containsLine)() or [containsColumn](ktexteditor-movingrange.md#containsColumn)() to check whether the [MovingRange](ktexteditor-movingrange.md) contains a Range, a Cursor, a line or column. The same holds for [overlaps](ktexteditor-movingrange.md#overlaps)(), [overlapsLine](ktexteditor-movingrange.md#overlapsLine)() and [overlapsColumn](ktexteditor-movingrange.md#overlapsColumn)(). Besides [onSingleLine](ktexteditor-movingrange.md#onSingleLine)() returns whether a [MovingRange](ktexteditor-movingrange.md) spans only one line.

For compatibility, a [MovingRange](ktexteditor-movingrange.md) can be explicitly converted to a simple Range by calling [toRange](ktexteditor-movingrange.md#toRange)(), or implicitly by the Range operator.

### Arbitrary Highlighting {#arbitrary-highlighting}

With [setAttribute](ktexteditor-movingrange.md#setAttribute)() highlighting Attribute%s can be assigned to a [MovingRange](ktexteditor-movingrange.md). By default, this highlighting is used in all views of a document. Use [setView](ktexteditor-movingrange.md#setView)(), if the highlighting should only appear in a specific view. Further, if the additional highlighting should not be printed call [setAttributeOnlyForViews](ktexteditor-movingrange.md#setAttributeOnlyForViews)() with the parameter true.

### MovingRange Example {#movingrange-example}

In the following example, we assume the [KTextEditor::Document](ktexteditor-document.md) has the contents:

```cpp
void printText(const std::string & text); // this is line 3
```

In order to highlight the function name *printText* with a yellow background color, the following code is needed:

```cpp
KTextEditor::View * view = ...;
KTextEditor::Document * doc = view->document();

// range is of type KTextEditor::MovingRange*
auto range = doc->newMovingRange(KTextEditor::Range(3, 5, 3, 14));

KTextEditor::Attribute::Ptr attrib = new KTextEditor::Attribute();
attrib->setBackground(Qt::yellow);

range->setAttribute(attrib);
```

[MovingRange](ktexteditor-movingrange.md)%s are invalidated automatically when a document is cleared or closed.

*See also* [Cursor](ktexteditor-cursor.md), [MovingCursor](ktexteditor-movingcursor.md), [Range](ktexteditor-range.md), [MovingRangeFeedback](ktexteditor-movingrangefeedback.md), [Document](ktexteditor-document.md)

## Member Type Documentation {#member-type-documentation}

### enum MovingRange::EmptyBehavior {#EmptyBehavior-enum}

Behavior of range if it becomes empty.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::MovingRange::AllowEmpty` | `0x0` | Allow range to be empty |
| `KTextEditor::MovingRange::InvalidateIfEmpty` | `0x1` | Invalidate range if it becomes empty |

### enum MovingRange::InsertBehavior {#InsertBehavior-enum}

**flags MovingRange::InsertBehaviors**

Determines how the range reacts to characters inserted immediately outside the range.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::MovingRange::DoNotExpand` | `0x0` | Don't expand to encapsulate new characters in either direction. This is the default. |
| `KTextEditor::MovingRange::ExpandLeft` | `0x1` | Expand to encapsulate new characters to the left of the range. |
| `KTextEditor::MovingRange::ExpandRight` | `0x2` | Expand to encapsulate new characters to the right of the range. |

The `InsertBehaviors` type is a typedef for `QFlags<InsertBehavior>. `It stores an OR combination of `InsertBehavior` values.

*See also* InsertBehaviors

## Member Function Documentation {#member-function-documentation}

### \[protected\] MovingRange::MovingRange() {#MovingRange}

For inherited class only.

### MovingRange::MovingRange(*const KTextEditor::MovingRange &*) {#MovingRange-1}

no copy constructor, don't allow this to be copied.

### \[virtual noexcept\] MovingRange::~MovingRange() {#dtor.MovingRange}

Destruct the moving range.

### \[pure virtual\] const Attribute::Ptr &MovingRange::attribute() const {#attribute}

Gets the active Attribute for this range.

Returns a pointer to the active attribute

*See also* [setAttribute](ktexteditor-movingrange.md#setAttribute)()

### \[pure virtual\] bool MovingRange::attributeOnlyForViews() const {#attributeOnlyForViews}

Is this range's attribute only visible in views, not for example prints? Default is false. Returns range visible only for views

*See also* [setAttributeOnlyForViews](ktexteditor-movingrange.md#setAttributeOnlyForViews)()

### bool MovingRange::contains(KTextEditor::Cursor *cursor*) const {#contains}

Check to see if `cursor` is contained within this range, ie \>= [start](ktexteditor-movingrange.md#start)() and \< [end](ktexteditor-movingrange.md#end)().

`cursor` is the position to test for containment

Returns *true* if the cursor is contained within this range, otherwise *false*.

### bool MovingRange::contains(const KTextEditor::Range &*range*) const {#contains-1}

Check whether the this range wholly encompasses *range*.

`range` is the range to check

Returns *true*, if this range contains *range*, otherwise *false*

### bool MovingRange::containsColumn(int *column*) const {#containsColumn}

Check whether the range contains *column*.

`column` is the column to check

Returns *true* if the range contains *column*, otherwise *false*

### bool MovingRange::containsLine(int *line*) const {#containsLine}

Returns true if this range wholly encompasses `line`.

`line` is the line to check

Returns *true* if the line is wholly encompassed by this range, otherwise *false*.

### \[pure virtual\] KTextEditor::Document \*MovingRange::document() const {#document}

Gets the document to which this range is bound.

Returns a pointer to the document

### \[pure virtual\] KTextEditor::MovingRange::EmptyBehavior MovingRange::emptyBehavior() const {#emptyBehavior}

Will this range invalidate itself if it becomes empty? Returns behavior on becoming empty

*See also* [setEmptyBehavior](ktexteditor-movingrange.md#setEmptyBehavior)()

### \[pure virtual\] const KTextEditor::MovingCursor &MovingRange::end() const {#end}

Retrieve end cursor of this range, read-only. Returns end cursor

### \[pure virtual\] KTextEditor::MovingRangeFeedback \*MovingRange::feedback() const {#feedback}

Gets the active [MovingRangeFeedback](ktexteditor-movingrangefeedback.md) for this range.

Returns a pointer to the active [MovingRangeFeedback](ktexteditor-movingrangefeedback.md)

*See also* [setFeedback](ktexteditor-movingrange.md#setFeedback)()

### \[pure virtual\] KTextEditor::MovingRange::InsertBehaviors MovingRange::insertBehaviors() const {#insertBehaviors}

Get current insert behaviors. Returns current insert behaviors

*See also* [setInsertBehaviors](ktexteditor-movingrange.md#setInsertBehaviors)()

### bool MovingRange::isEmpty() const {#isEmpty}

Returns true if this range contains no characters, ie. the [start](ktexteditor-movingrange.md#start)() and [end](ktexteditor-movingrange.md#end)() positions are the same.

Returns *true* if the range contains no characters, otherwise *false*

### \[noexcept\] int MovingRange::numberOfLines() const {#numberOfLines}

Returns the number of lines separating the [start](ktexteditor-movingrange.md#start)() and [end](ktexteditor-movingrange.md#end)() positions.

Returns the number of lines separating the [start](ktexteditor-movingrange.md#start)() and [end](ktexteditor-movingrange.md#end)() positions; 0 if the start and end lines are the same.

### bool MovingRange::onSingleLine() const {#onSingleLine}

Check whether the [start](ktexteditor-movingrange.md#start)() and [end](ktexteditor-movingrange.md#end)() cursors of this range are on the same line.

Returns *true* if both the start and end positions are on the same line, otherwise *false*

### bool MovingRange::overlaps(const KTextEditor::Range &*range*) const {#overlaps}

Check whether the this range overlaps with *range*.

`range` is the range to check against

Returns *true*, if this range overlaps with *range*, otherwise *false*

### bool MovingRange::overlapsColumn(int *column*) const {#overlapsColumn}

Check to see if this range overlaps `column`; that is, if `column` is between [start](ktexteditor-movingrange.md#start)().column() and [end](ktexteditor-movingrange.md#end)().column(). This function is most likely to be useful in relation to block text editing.

`column` is the column to test

Returns *true* if the column is between the range's starting and ending columns, otherwise *false*.

### bool MovingRange::overlapsLine(int *line*) const {#overlapsLine}

Check whether the range overlaps at least part of *line*.

`line` is the line to check

Returns *true*, if the range overlaps at least part of *line*, otherwise *false*

### \[pure virtual\] void MovingRange::setAttribute(Attribute::Ptr *attribute*) {#setAttribute}

Sets the currently active attribute for this range. This will trigger update of the relevant view parts, if the attribute changed.

`attribute` is the attribute to assign to this range. If null, simply removes the previous Attribute.

*See also* [attribute](ktexteditor-movingrange.md#attribute)()

### \[pure virtual\] void MovingRange::setAttributeOnlyForViews(bool *onlyForViews*) {#setAttributeOnlyForViews}

Set if this range's attribute is only visible in views, not for example prints.

`onlyForViews` if true, the attribute is only valid for views

*See also* [attributeOnlyForViews](ktexteditor-movingrange.md#attributeOnlyForViews)()

### \[pure virtual\] void MovingRange::setEmptyBehavior(KTextEditor::MovingRange::EmptyBehavior *emptyBehavior*) {#setEmptyBehavior}

Set if this range will invalidate itself if it becomes empty.

`emptyBehavior` is the behavior on becoming empty

*See also* [emptyBehavior](ktexteditor-movingrange.md#emptyBehavior)()

### \[pure virtual\] void MovingRange::setFeedback(KTextEditor::MovingRangeFeedback \**feedback*) {#setFeedback}

Sets the currently active [MovingRangeFeedback](ktexteditor-movingrangefeedback.md) for this range. This will trigger evaluation if feedback must be send again (for example if mouse is already inside range).

`feedback` is the [MovingRangeFeedback](ktexteditor-movingrangefeedback.md) to assign to this range. If null, simply removes the previous [MovingRangeFeedback](ktexteditor-movingrangefeedback.md).

*See also* [feedback](ktexteditor-movingrange.md#feedback)()

### \[pure virtual\] void MovingRange::setInsertBehaviors(KTextEditor::MovingRange::InsertBehaviors *insertBehaviors*) {#setInsertBehaviors}

Set insert behaviors.

`insertBehaviors` are the new insert behaviors

*See also* [insertBehaviors](ktexteditor-movingrange.md#insertBehaviors)()

### \[pure virtual\] void MovingRange::setRange(KTextEditor::Range *range*) {#setRange}

Set the range of this range.

A TextRange is not allowed to be empty, as soon as start == end position, it will become automatically invalid!

`range` new range for this clever range

### \[pure virtual, since 6.0\] void MovingRange::setRange(KTextEditor::Range *range*, Attribute::Ptr *attribute*) {#setRange-1}

Set the range of this range and the connected attribute. Avoids internal overhead of separate setting that.

A TextRange is not allowed to be empty, as soon as start == end position, it will become automatically invalid!

`range` is the new range for this clever range

`attribute` is the attribute to assign to this range. If null, simply removes the previous Attribute.

This function was introduced in Qt 6.0.

### \[pure virtual, since 6.0\] void MovingRange::setRange(KTextEditor::Range *range*, Attribute::Ptr *attribute*, qreal *zDepth*) {#setRange-2}

Set the range of this range and the connected attribute and Z-depth. Avoids internal overhead of separate setting that.

A TextRange is not allowed to be empty, as soon as start == end position, it will become automatically invalid!

`range` is the new range for this clever range

`attribute` is the attribute to assign to this range. If null, simply removes the previous Attribute.

`zDepth` is the new Z-depth of this range

This function was introduced in Qt 6.0.

### void MovingRange::setRange(KTextEditor::Cursor *start*, KTextEditor::Cursor *end*) {#setRange-3}

Set the range of this range A TextRange is not allowed to be empty, as soon as start == end position, it will become automatically invalid!

`start` is the new start for this clever range

`end` is the new end for this clever range

This is an overloaded function.

### \[pure virtual\] void MovingRange::setView(KTextEditor::View \**view*) {#setView}

Sets the currently active view for this range. This will trigger update of the relevant view parts, if the view changed. Set view before the attribute, that will avoid not needed redraws.

`view` is the View to assign to this range. If null, simply removes the previous view.

*See also* [view](ktexteditor-movingrange.md#view)()

### \[pure virtual\] void MovingRange::setZDepth(qreal *zDepth*) {#setZDepth}

Set the current Z-depth of this range. Ranges with smaller Z-depth than others will win during rendering. This will trigger update of the relevant view parts, if the depth changed. Set depth before the attribute, that will avoid not needed redraws. Default is 0.0.

`zDepth` is new Z-depth of this range

*See also* [zDepth](ktexteditor-movingrange.md#zDepth)()

### \[pure virtual\] const KTextEditor::MovingCursor &MovingRange::start() const {#start}

Retrieve start cursor of this range, read-only. Returns start cursor

### \[noexcept\] KTextEditor::LineRange MovingRange::toLineRange() const {#toLineRange}

Convert this [MovingRange](ktexteditor-movingrange.md) to a simple [LineRange](ktexteditor-linerange.md). Returns [LineRange](ktexteditor-linerange.md) from the start line to the end line of this range.

### const KTextEditor::Range MovingRange::toRange() const {#toRange}

Convert this clever range into a dumb one. Returns normal range

### \[pure virtual\] KTextEditor::View \*MovingRange::view() const {#view}

Gets the active view for this range. Might be already invalid, internally only used for pointer comparisons.

Returns a pointer to the active view

*See also* [setView](ktexteditor-movingrange.md#setView)()

### \[pure virtual\] qreal MovingRange::zDepth() const {#zDepth}

Gets the current Z-depth of this range. Ranges with smaller Z-depth than others will win during rendering. Default is 0.0.

Defined depths for common kind of ranges use in editor components implementing this interface, smaller depths are more more in the foreground and will win during rendering:

- Selection == -100000.0
- Search == -10000.0
- Bracket Highlighting == -1000.0
- Folding Hover == -100.0

Returns current Z-depth of this range

*See also* [setZDepth](ktexteditor-movingrange.md#setZDepth)()

### MovingRange::operator KTextEditor::Range() const {#operator-KTextEditor-3a-3aRange}

Convert this clever range into a dumb one. Equal to [toRange](ktexteditor-movingrange.md#toRange), allowing to use implicit conversion. Returns normal range

### KTextEditor::MovingRange &MovingRange::operator=(*const KTextEditor::MovingRange &*) {#operator-eq}

no assignment operator, no copying around clever ranges.

## Related Non-Members {#related-non-members}

### QDebug operator\<\<(QDebug *s*, const KTextEditor::MovingRange &*range*) {#operator-lt-lt}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this range to the debug output in a nicely formatted way.

`s` is the debug stream

`range` is the range to print

Returns debug stream

### QDebug operator\<\<(QDebug *s*, const KTextEditor::MovingRange \**range*) {#operator-lt-lt-1}

[qDebug](https://doc.qt.io/qt-6/qdebug.html#qDebug)() stream operator. Writes this range to the debug output in a nicely formatted way.

`s` is the debug stream

`range` is the range to print

Returns debug stream
