---
title: "KToolTipHelper Class"
description: "An event filter used to enhance tooltips."
---

# KToolTipHelper Class

An event filter used to enhance tooltips. [More...](#details)

- **Header:** `#include <KToolTipHelper>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ktooltiphelper-members.md)

## Public Functions

- [bool eventFilter(QObject \*watched, QEvent \*event)](#eventFilter)

## Static Public Members

- [const QString whatsThisHintOnly()](#whatsThisHintOnly)

## Detailed Description {#details}

Example: Without this class, a tooltip of a [QToolButton](https://doc.qt.io/qt-6/qtoolbutton.html) of a "New" action will read something like "New File". Using this class, the tooltip can be enhanced to read something like "New File (Ctrl+N)" and in the next line smaller "Press Shift for help.". Pressing Shift will open the "What's This" context help for that widget. If a hyperlink in that help is clicked, the corresponding event will also be filtered by this class and open the linked location.

The extra text added to tooltips is only shown when available and where it makes sense. If a [QToolButton](https://doc.qt.io/qt-6/qtoolbutton.html) has no associated shortcut and an empty [QWidget::whatsThis](https://doc.qt.io/qt-6/qwidget.html#whatsThis-prop)(), this class won't tamper with the requested tooltip at all.

This class also activates tooltips for actions in QMenus but only when it makes sense like when the tooltip isn't equal to the already displayed text.

If you want the "Press Shift for help." line to be displayed for a widget that has whatsThis() but no toolTip() take a look at [KToolTipHelper::whatsThisHintOnly](ktooltiphelper.md#whatsThisHintOnly)().

The enhanced tooltips can be enabled at any time after the [QApplication](https://doc.qt.io/qt-6/qapplication.html) was constructed with:

```cpp
qApp->installEventFilter(KToolTipHelper::instance());
```

Therefore, to de-activate them you can call the following any time later:

```cpp
qApp->removeEventFilter(KToolTipHelper::instance());
```

If you want [KToolTipHelper](ktooltiphelper.md) to not tamper with certain QEvents, e.g. you want to handle some tooltips differently or you want to change what happens when a [QWhatsThisClickedEvent](https://doc.qt.io/qt-6/qwhatsthisclickedevent.html) is processed, first remove [KToolTipHelper](ktooltiphelper.md) as an event filter just like in the line of code above. Then create your own custom EventFilter that handles those QEvents differently and, for all cases that you don't want to handle differently, call:

```cpp
return KToolTipHelper::instance()->eventFilter(watched, event);
```

Since 5.84, [KMainWindow](kmainwindow.md) installs this EventFilter by default. If you want to opt out of that, remove the EventFilter in the constructor of your MainWindow class inheriting from [KMainWindow](kmainwindow.md).

*See also* [QToolTip](https://doc.qt.io/qt-6/qtooltip.html)

## Member Function Documentation {#member-function-documentation}

### \[override virtual\] bool KToolTipHelper::eventFilter(QObject \**watched*, QEvent \**event*) {#eventFilter}

Reimplements: [QObject::eventFilter(QObject \*watched, QEvent \*event)](https://doc.qt.io/qt-6/qobject.html#eventFilter).

Filters the given `event` for a given `watched` object.

Filters [QEvent::ToolTip](https://doc.qt.io/qt-6/qevent.html#Type-enum) if an enhanced tooltip is available for the widget. Filters the [QEvent::KeyPress](https://doc.qt.io/qt-6/qevent.html#Type-enum) that is used to expand an expandable tooltip. Filters [QEvent::WhatsThisClicked](https://doc.qt.io/qt-6/qevent.html#Type-enum) so hyperlinks in whatsThis() texts work.

*See also* [QObject::eventFilter](https://doc.qt.io/qt-6/qobject.html#eventFilter)(), [QHelpEvent](https://doc.qt.io/qt-6/qhelpevent.html)

### \[static\] const QString KToolTipHelper::whatsThisHintOnly() {#whatsThisHintOnly}

Use this to have a widget show "Press Shift for help." as its tooltip.

Example usage:

```cpp
widget->setToolTip(KToolTipHelper::whatsThisHintOnly());
```

[KToolTipHelper](ktooltiphelper.md) won't show that tooltip if the widget's whatsThis() is empty.

Returns a [QString](https://doc.qt.io/qt-6/qstring.html) that is interpreted by this class to show the expected tooltip.
