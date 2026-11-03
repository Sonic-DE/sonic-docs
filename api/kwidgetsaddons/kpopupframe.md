---
title: "KPopupFrame Class"
description: "Frame with popup menu behavior."
---

# KPopupFrame Class

Frame with popup menu behavior. [More...](#details)

- **Header:** `#include <KPopupFrame>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QFrame](https://doc.qt.io/qt-6/qframe.html)

[List of all members, including inherited members](kpopupframe-members.md)

## Public Functions

- [KPopupFrame(QWidget \*parent = nullptr)](#KPopupFrame)
- [int exec(const QPoint &p)](#exec)
- [int exec(int x, int y)](#exec-1)
- [void popup(const QPoint &pos)](#popup)
- [void resizeEvent(QResizeEvent \*resize)](#resizeEvent)
- [void setMainWidget(QWidget \*m)](#setMainWidget)

## Public Slots

- [void close(int r)](#close)

## Signals

- [void leaveModality()](#leaveModality)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### KPopupFrame::KPopupFrame(QWidget \**parent* = nullptr) {#KPopupFrame}

The constructor. Creates a dialog without buttons.

### \[slot\] void KPopupFrame::close(int *r*) {#close}

Close the popup window. This is called from the main widget, usually.

`r` is the result returned from [exec](kpopupframe.md#exec)()

### int KPopupFrame::exec(const QPoint &*p*) {#exec}

Execute the popup window.

### int KPopupFrame::exec(int *x*, int *y*) {#exec-1}

Execute the popup window.

### \[signal\] void KPopupFrame::leaveModality() {#leaveModality}

### void KPopupFrame::popup(const QPoint &*pos*) {#popup}

Open the popup window at position pos.

### \[override virtual\] void KPopupFrame::resizeEvent(QResizeEvent \**resize*) {#resizeEvent}

Reimplements: [QWidget::resizeEvent(QResizeEvent \*event)](https://doc.qt.io/qt-6/qwidget.html#resizeEvent).

The resize event. Simply resizes the main widget to the whole widgets client size.

### void KPopupFrame::setMainWidget(QWidget \**m*) {#setMainWidget}

Set the main widget. You cannot set the main widget from the constructor, since it must be a child of the frame itself. Be careful: the size is set to the main widgets size. It is up to you to set the main widgets correct size before setting it as the main widget.
