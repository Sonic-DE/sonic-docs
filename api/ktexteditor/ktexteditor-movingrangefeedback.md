---
title: "KTextEditor::MovingRangeFeedback Class"
description: "A class which provides notifications of state changes to a MovingRange."
---

# KTextEditor::MovingRangeFeedback Class

A class which provides notifications of state changes to a [MovingRange](ktexteditor-movingrange.md). [More...](#details)

- **Header:** `#include <KTextEditor/MovingRangeFeedback>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Group:** MovingRangeFeedback is part of kte\_group\_moving\_classes

[List of all members, including inherited members](ktexteditor-movingrangefeedback-members.md)

## Public Functions

- [MovingRangeFeedback()](#MovingRangeFeedback)
- [~MovingRangeFeedback()](#dtor.MovingRangeFeedback)
- [void caretEnteredRange(KTextEditor::MovingRange \*range, KTextEditor::View \*view)](#caretEnteredRange)
- [void caretExitedRange(KTextEditor::MovingRange \*range, KTextEditor::View \*view)](#caretExitedRange)
- [void mouseEnteredRange(KTextEditor::MovingRange \*range, KTextEditor::View \*view)](#mouseEnteredRange)
- [void mouseExitedRange(KTextEditor::MovingRange \*range, KTextEditor::View \*view)](#mouseExitedRange)
- [void rangeEmpty(KTextEditor::MovingRange \*range)](#rangeEmpty)
- [void rangeInvalid(KTextEditor::MovingRange \*range)](#rangeInvalid)

## Detailed Description {#details}

This class provides notifications of changes to the position or contents of a [MovingRange](ktexteditor-movingrange.md).

Before destruction, you must unregister the feedback class from any range using it.

## Member Function Documentation {#member-function-documentation}

### MovingRangeFeedback::MovingRangeFeedback() {#MovingRangeFeedback}

Default constructor

### \[virtual noexcept\] MovingRangeFeedback::~MovingRangeFeedback() {#dtor.MovingRangeFeedback}

Virtual destructor

### \[virtual\] void MovingRangeFeedback::caretEnteredRange(KTextEditor::MovingRange \**range*, KTextEditor::View \**view*) {#caretEnteredRange}

The caret on `view` entered `range`.

`range` is the pointer to the range which generated the notification.

`view` is the view over which the mouse moved to generate the notification

### \[virtual\] void MovingRangeFeedback::caretExitedRange(KTextEditor::MovingRange \**range*, KTextEditor::View \**view*) {#caretExitedRange}

The caret on `view` exited `range`.

`range` is the pointer to the range which generated the notification.

`view` is the view over which the mouse moved to generate the notification

### \[virtual\] void MovingRangeFeedback::mouseEnteredRange(KTextEditor::MovingRange \**range*, KTextEditor::View \**view*) {#mouseEnteredRange}

The mouse cursor on `view` entered `range`.

`range` is a pointer to the range which generated the notification.

`view` is the view over which the mouse moved to generate the notification

### \[virtual\] void MovingRangeFeedback::mouseExitedRange(KTextEditor::MovingRange \**range*, KTextEditor::View \**view*) {#mouseExitedRange}

The mouse cursor on `view` exited `range`.

`range` is the pointer to the range which generated the notification.

`view` is the view over which the mouse moved to generate the notification

### \[virtual\] void MovingRangeFeedback::rangeEmpty(KTextEditor::MovingRange \**range*) {#rangeEmpty}

The range is now empty (ie. the start and end cursors are the same). If the range has invalidateIfEmpty set, this will never be emitted, but instead [rangeInvalid](ktexteditor-movingrangefeedback.md#rangeInvalid) is triggered. You may delete the range inside this method, but don't alter the range here (for example by using setRange).

`range` is a pointer to the range which generated the notification.

### \[virtual\] void MovingRangeFeedback::rangeInvalid(KTextEditor::MovingRange \**range*) {#rangeInvalid}

The range is now invalid (ie. the start and end cursors are invalid). You may delete the range inside this method, but don't alter the range here (for example by using setRange).

`range` is a pointer to the range which generated the notification.
