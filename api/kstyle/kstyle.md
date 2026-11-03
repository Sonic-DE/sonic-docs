---
title: "KStyle Class"
description: "Provides integration with KDE Plasma Workspace settings for Qt styles."
---

# KStyle Class

Provides integration with KDE Plasma Workspace settings for Qt styles. [More...](#details)

- **Header:** `#include <KStyle>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FrameworkIntegration)`  
  `target_link_libraries(mytarget PRIVATE KF6::Style)`
- **Inherits:** [QCommonStyle](https://doc.qt.io/qt-6/qcommonstyle.html)

[List of all members, including inherited members](kstyle-members.md)

## Static Public Members

- [QStyle::ControlElement customControlElement(const QString &element, const QWidget \*widget)](#customControlElement)
- [QStyle::StyleHint customStyleHint(const QString &element, const QWidget \*widget)](#customStyleHint)
- [QStyle::SubElement customSubElement(const QString &element, const QWidget \*widget)](#customSubElement)

## Protected Functions

- [QStyle::ControlElement newControlElement(const QString &element)](#newControlElement)
- [QStyle::StyleHint newStyleHint(const QString &element)](#newStyleHint)
- [QStyle::SubElement newSubElement(const QString &element)](#newSubElement)

## Detailed Description {#details}

Derive your Qt style from [KStyle](kstyle.md) to automatically inherit various settings from the KDE Plasma Workspace, providing a consistent user experience. For example, this will ensure a consistent single-click or double-click activation setting, and the use of standard themed icons.

## Member Function Documentation {#member-function-documentation}

### \[static\] QStyle::ControlElement KStyle::customControlElement(const QString &*element*, const QWidget \**widget*) {#customControlElement}

### \[static\] QStyle::StyleHint KStyle::customStyleHint(const QString &*element*, const QWidget \**widget*) {#customStyleHint}

Runtime element extension This is just convenience and does /not/ require the using widgets style to inherit [KStyle](kstyle.md) (i.e. calling this while using cleanlooks won't segfault or so but just return 0) Returns a unique id for an element string (e.g. "CE\_CapacityBar")

For simplicity, only StyleHints, ControlElements and their SubElements are supported If you don't need extended SubElement functionality, just drop it

`element` The style element, represented as string. Naming convention: "appname.(2-char-element-type)\_element" where the 2-char-element-type is of {SH, CE, SE} (widgets in kdelibs don't have to pass the appname) examples: "CE\_CapacityBar", "amarok.CE\_Analyzer"

`widget` Your widget ("this") passing this is mandatory, passing NULL will just return 0

Returns a unique id for the `element` string or 0, if the element is not supported by the widgets current style

Important notes:

1) If your string lacks the matching "SH\_", "CE\_" or "SE\_" token the element request will be ignored (return is 0)

2) Try to avoid custom elements and use default ones (if possible) to get better style support and keep UI coherency

3) If you cache this value (good idea, this requires a map lookup) don't (!) forget to catch style changes in [QWidget::changeEvent](https://doc.qt.io/qt-6/qwidget.html#changeEvent)()

### \[static\] QStyle::SubElement KStyle::customSubElement(const QString &*element*, const QWidget \**widget*) {#customSubElement}

### \[protected\] QStyle::ControlElement KStyle::newControlElement(const QString &*element*) {#newControlElement}

### \[protected\] QStyle::StyleHint KStyle::newStyleHint(const QString &*element*) {#newStyleHint}

Runtime element extension, allows inheriting styles to add support custom elements merges supporting inherit chains Supposed to be called e.g. in your constructor.

NOTICE: in order to have this work, your style must provide an "X-KDE-CustomElements" classinfo, i.e.

```cpp
class MyStyle : public KStyle
{
      Q_OBJECT
      Q_CLASSINFO ("X-KDE-CustomElements", "true")

  public:
      .....
}
```

`element` The style element, represented as string. Suggested naming convention: appname.(2-char-element-type)\_element where the 2-char-element-type is of {SH, CE, SE} widgets in kdelibs don't have to pass the appname examples: "CE\_CapacityBar", "amarok.CE\_Analyzer"

Important notes: 1) If your string lacks the matching "SH\_", "CE\_" or "SE\_" token the element request will be ignored (return is 0) 2) To keep UI coherency, don't support any nonsense in your style, but convince app developers to use standard elements - if available

### \[protected\] QStyle::SubElement KStyle::newSubElement(const QString &*element*) {#newSubElement}
