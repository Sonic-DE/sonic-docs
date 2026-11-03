---
title: "KUserFeedback::NotificationPopup Class"
description: "Notification popup that overlays a small part of the application for encouraging contributions or inform about surveys."
---

# KUserFeedback::NotificationPopup Class

Notification popup that overlays a small part of the application for encouraging contributions or inform about surveys. [More...](#details)

- **Header:** `#include <KUserFeedback/NotificationPopup>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS UserFeedbackWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::UserFeedbackWidgets)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kuserfeedback-notificationpopup-members.md)

## Public Functions

- [NotificationPopup(QWidget \*parent)](#NotificationPopup)
- [void setFeedbackProvider(KUserFeedback::Provider \*provider)](#setFeedbackProvider)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] NotificationPopup::NotificationPopup(QWidget \**parent*) {#NotificationPopup}

Create a new notification popup.

Do not put this widget into a layout.

`parent` The parent widget. This must not be `nullptr`.

### void NotificationPopup::setFeedbackProvider(KUserFeedback::Provider \**provider*) {#setFeedbackProvider}

Set the feedback provider that is going to drive this notification popup.
