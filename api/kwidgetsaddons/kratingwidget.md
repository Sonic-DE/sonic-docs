---
title: "KRatingWidget Class"
description: "Displays a rating value as a row of pixmaps."
---

# KRatingWidget Class

Displays a rating value as a row of pixmaps. [More...](#details)

- **Header:** `#include <KRatingWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QFrame](https://doc.qt.io/qt-6/qframe.html)

[List of all members, including inherited members](kratingwidget-members.md)

## Properties

- [alignment : Qt::Alignment](#alignment-prop)
- [halfStepsEnabled : bool](#halfStepsEnabled-prop)
- [icon : QIcon](#icon-prop)
- [maxRating : int](#maxRating-prop)
- [rating : int](#rating-prop)
- [spacing : int](#spacing-prop)

## Public Functions

- [KRatingWidget(QWidget \*parent = nullptr)](#KRatingWidget)
- [Qt::Alignment alignment() const](#alignment)
- [bool halfStepsEnabled() const](#halfStepsEnabled)
- [QIcon icon() const](#icon)
- [Qt::LayoutDirection layoutDirection() const](#layoutDirection)
- [int maxRating() const](#maxRating)
- [int rating() const](#rating)
- [int spacing() const](#spacing)

## Public Slots

- [void setAlignment(Qt::Alignment align)](#setAlignment)
- [void setCustomPixmap(const QPixmap &pixmap)](#setCustomPixmap)
- [void setHalfStepsEnabled(bool enabled)](#setHalfStepsEnabled)
- [void setIcon(const QIcon &icon)](#setIcon)
- [void setLayoutDirection(Qt::LayoutDirection direction)](#setLayoutDirection)
- [void setMaxRating(int max)](#setMaxRating)
- [void setPixmapSize(int size)](#setPixmapSize)
- [void setRating(int rating)](#setRating)
- [void setSpacing(int)](#setSpacing)

## Signals

- [void ratingChanged(int rating)](#ratingChanged)

## Detailed Description {#details}

The [KRatingWidget](kratingwidget.md) displays a range of stars or other arbitrary pixmaps and allows the user to select a certain number by mouse.

*See also* [KRatingPainter](kratingpainter.md)

## Property Documentation {#property-documentation}

### alignment : Qt::Alignment {#alignment-prop}

**Access functions:**

- `Qt::Alignment` **[alignment](kratingwidget.md#alignment)**() const
- `void` **[setAlignment](kratingwidget.md#setAlignment)**(`Qt::Alignment` *align*)

### halfStepsEnabled : bool {#halfStepsEnabled-prop}

**Access functions:**

- `bool` **[halfStepsEnabled](kratingwidget.md#halfStepsEnabled)**() const
- `void` **[setHalfStepsEnabled](kratingwidget.md#setHalfStepsEnabled)**(`bool` *enabled*)

### icon : QIcon {#icon-prop}

**Access functions:**

- `QIcon` **[icon](kratingwidget.md#icon)**() const
- `void` **[setIcon](kratingwidget.md#setIcon)**(const `QIcon` &*icon*)

### maxRating : int {#maxRating-prop}

**Access functions:**

- `int` **[maxRating](kratingwidget.md#maxRating)**() const
- `void` **[setMaxRating](kratingwidget.md#setMaxRating)**(`int` *max*)

### rating : int {#rating-prop}

**Access functions:**

- `int` **[rating](kratingwidget.md#rating)**() const
- `void` **[setRating](kratingwidget.md#setRating)**(`int` *rating*)

### spacing : int {#spacing-prop}

**Access functions:**

- `int` **[spacing](kratingwidget.md#spacing)**() const
- `void` **[setSpacing](kratingwidget.md#setSpacing)**(*int*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KRatingWidget::KRatingWidget(QWidget \**parent* = nullptr) {#KRatingWidget}

Creates a new rating widget.

### Qt::Alignment KRatingWidget::alignment() const {#alignment}

The alignment of the stars.

> **Note:** Getter function for property [alignment](kratingwidget.md#alignment-prop).

*See also* [setAlignment](kratingwidget.md#setAlignment)

### bool KRatingWidget::halfStepsEnabled() const {#halfStepsEnabled}

If half steps are enabled one star equals to 2 rating points and uneven rating values result in half-stars being drawn.

> **Note:** Getter function for property [halfStepsEnabled](kratingwidget.md#halfStepsEnabled-prop).

*See also* [setHalfStepsEnabled](kratingwidget.md#setHalfStepsEnabled)

### QIcon KRatingWidget::icon() const {#icon}

The icon used to draw a star. In case a custom pixmap has been set this value is ignored.

> **Note:** Getter function for property [icon](kratingwidget.md#icon-prop).

*See also* [setIcon](kratingwidget.md#setIcon), [setCustomPixmap](kratingwidget.md#setCustomPixmap)

### Qt::LayoutDirection KRatingWidget::layoutDirection() const {#layoutDirection}

The layout direction.

If RTL the stars representing the rating value will be drawn from the right.

*See also* [setLayoutDirection](kratingwidget.md#setLayoutDirection)

### int KRatingWidget::maxRating() const {#maxRating}

Returns the maximum possible rating.

> **Note:** Getter function for property [maxRating](kratingwidget.md#maxRating-prop).

*See also* [setMaxRating](kratingwidget.md#setMaxRating)()

### int KRatingWidget::rating() const {#rating}

Returns the current rating.

> **Note:** Getter function for property [rating](kratingwidget.md#rating-prop).

*See also* [setRating](kratingwidget.md#setRating)()

### \[signal\] void KRatingWidget::ratingChanged(int *rating*) {#ratingChanged}

This signal is emitted when the rating is changed.

### \[slot\] void KRatingWidget::setAlignment(Qt::Alignment *align*) {#setAlignment}

The alignment of the stars in the drawing rect. All alignment flags are supported.

> **Note:** Setter function for property [alignment](kratingwidget.md#alignment-prop).

*See also* [alignment](kratingwidget.md#alignment)()

### \[slot\] void KRatingWidget::setCustomPixmap(const QPixmap &*pixmap*) {#setCustomPixmap}

Set a custom pixmap.

### \[slot\] void KRatingWidget::setHalfStepsEnabled(bool *enabled*) {#setHalfStepsEnabled}

If half steps are enabled (the default) then one rating step corresponds to half a star.

> **Note:** Setter function for property [halfStepsEnabled](kratingwidget.md#halfStepsEnabled-prop).

*See also* [halfStepsEnabled](kratingwidget.md#halfStepsEnabled)()

### \[slot\] void KRatingWidget::setIcon(const QIcon &*icon*) {#setIcon}

Set a custom icon. Defaults to "rating".

> **Note:** Setter function for property [icon](kratingwidget.md#icon-prop).

*See also* [icon](kratingwidget.md#icon)()

### \[slot\] void KRatingWidget::setLayoutDirection(Qt::LayoutDirection *direction*) {#setLayoutDirection}

LTR or RTL

*See also* [layoutDirection](kratingwidget.md#layoutDirection)()

### \[slot\] void KRatingWidget::setMaxRating(int *max*) {#setMaxRating}

Set the maximum allowed rating value. The default is 10 which means that a rating from 1 to 10 is selectable. If `max` is uneven steps are automatically only allowed full.

> **Note:** Setter function for property [maxRating](kratingwidget.md#maxRating-prop).

*See also* [maxRating](kratingwidget.md#maxRating)()

### \[slot\] void KRatingWidget::setPixmapSize(int *size*) {#setPixmapSize}

Set the recommended size of the pixmaps. This is only used for the sizeHint. The actual size is always dependent on the size of the widget itself.

### \[slot\] void KRatingWidget::setRating(int *rating*) {#setRating}

Set the current rating. Calling this method will trigger the [ratingChanged](kratingwidget.md#ratingChanged) signal if `rating` is different from the previous rating.

> **Note:** Setter function for property [rating](kratingwidget.md#rating-prop).

*See also* [rating](kratingwidget.md#rating)()

### \[slot\] void KRatingWidget::setSpacing(*int*) {#setSpacing}

Set the spacing between the pixmaps. The default is 0.

> **Note:** Setter function for property [spacing](kratingwidget.md#spacing-prop).

*See also* [spacing](kratingwidget.md#spacing)()

### int KRatingWidget::spacing() const {#spacing}

The spacing between the rating stars.

> **Note:** Getter function for property [spacing](kratingwidget.md#spacing-prop).

*See also* [setSpacing](kratingwidget.md#setSpacing)
