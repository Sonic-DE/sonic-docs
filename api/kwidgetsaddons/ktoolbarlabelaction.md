---
title: "KToolBarLabelAction Class"
description: "Class to display a label in a toolbar."
---

# KToolBarLabelAction Class

Class to display a label in a toolbar. [More...](#details)

- **Header:** `#include <KToolBarLabelAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidgetAction](https://doc.qt.io/qt-6/qwidgetaction.html)

[List of all members, including inherited members](ktoolbarlabelaction-members.md)

## Public Functions

- [KToolBarLabelAction(const QString &text, QObject \*parent)](#KToolBarLabelAction)
- [KToolBarLabelAction(QAction \*buddy, const QString &text, QObject \*parent)](#KToolBarLabelAction-1)
- [QAction \*buddy() const](#buddy)
- [void setBuddy(QAction \*buddy)](#setBuddy)

## Signals

- [void textChanged(const QString &newText)](#textChanged)

## Detailed Description {#details}

[KToolBarLabelAction](ktoolbarlabelaction.md) is a convenience class for displaying a label in a toolbar.

It provides easy access to the label's \#[setBuddy](ktoolbarlabelaction.md#setBuddy)([QAction](https://doc.qt.io/qt-6/qaction.html)\*) and \#[buddy](ktoolbarlabelaction.md#buddy)() methods and can be used as follows:

```cpp
KHistoryComboBox *findCombo = new KHistoryComboBox(true, this);

KWidgetAction *action = new KWidgetAction(findCombo, i18n("Find Combo"),
                                           Qt::Key_F6, this, SLOT( slotFocus()),
                                           actionCollection(), "find_combo");

QAction *action = new KToolBarLabelAction(action, i18n("Find "), "find_label");
action->setShortcut(Qt::Key_F6);
connect(action, &QAction::triggered, this, [this]() { slotFocus(); });
```

## Member Function Documentation {#member-function-documentation}

### KToolBarLabelAction::KToolBarLabelAction(const QString &*text*, QObject \**parent*) {#KToolBarLabelAction}

Creates a toolbar label.

`text` The label's and the action's text.

`parent` This action's parent.

### KToolBarLabelAction::KToolBarLabelAction(QAction \**buddy*, const QString &*text*, QObject \**parent*) {#KToolBarLabelAction-1}

Creates a toolbar label setting a buddy for the label.

`buddy` The action whose widget which is focused when the label's accelerator is typed.

`text` The label's and the action's text.

`parent` This action's parent.

### QAction \*KToolBarLabelAction::buddy() const {#buddy}

Returns the label's buddy or a null pointer if no buddy is currently set.

See [QLabel::buddy](https://doc.qt.io/qt-6/qlabel.html#buddy)() and [QLabel::setBuddy](https://doc.qt.io/qt-6/qlabel.html#setBuddy)() for more information.

*See also* [setBuddy](ktoolbarlabelaction.md#setBuddy)()

### void KToolBarLabelAction::setBuddy(QAction \**buddy*) {#setBuddy}

Sets the label's buddy to buddy.

See [QLabel::setBuddy](https://doc.qt.io/qt-6/qlabel.html#setBuddy)() for details.

*See also* [buddy](ktoolbarlabelaction.md#buddy)()

### \[signal\] void KToolBarLabelAction::textChanged(const QString &*newText*) {#textChanged}

This signal is emitted whenever the text of this action is changed.
