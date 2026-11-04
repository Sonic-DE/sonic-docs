---
title: "KStyleExtensions Namespace"
description: "Runtime style extensions."
---

# KStyleExtensions Namespace

Runtime style extensions. [More...](#details)

- **Header:** `#include <KStyleExtensions>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

## Detailed Description {#details}

You can use this to have a supporting [QStyle](https://doc.qt.io/qt-6/qstyle.html) implementation paint your widget This is just convenience and does /not/ require the using widgets style to inherit KStyle (i.e. calling this while using cleanlooks won't segfault but just return "0")

For simplicity, only StyleHints, ControlElements and their SubElements are supported If you don't need extended SubElement functionality, just skip its usage

The element string has to be of the form: "appname.(2-char-element-type)\_element" The 2-char-element-type is the corresponding {SH, CE, SE} Widgets in [KWidgetsAddons](kwidgetsaddons-module.md) don't have to pass the appname

Examples: "CE\_CapacityBar", "amarok.CE\_Analyzer"

Important notes:

1) If your string lacks the matching "SH\_", "CE\_" or "SE\_" token the element request will be ignored (return is 0)

2) Try to avoid custom elements and use default ones (if possible) to get better style support and keep UI coherency

3) If you cache this value (good idea, this requires a map lookup) do not forget to catch style changes in [QWidget::changeEvent](https://doc.qt.io/qt-6/qwidget.html#changeEvent)()!

## Function Documentation {#function-documentation}

### QStyle::ControlElement KStyleExtensions::customControlElement(const QString &*element*, const QWidget \**widget*) {#customControlElement}

Resolve a dynamic [QStyle::ControlElement](https://doc.qt.io/qt-6/qstyle.html#ControlElement-enum) for eg. [QStyle::drawControl](https://doc.qt.io/qt-6/qstyle.html#drawControl)()

Returns a unique [QStyle::ControlElement](https://doc.qt.io/qt-6/qstyle.html#ControlElement-enum) or 0 in case the style doesn't support this element

`element` a valid element string appname.CE\_element, eg. "amarok.CE\_Analyzer"

`widget` the widget to paint this element for. This parameter is mandatory, nullptr will return 0!

### QStyle::StyleHint KStyleExtensions::customStyleHint(const QString &*element*, const QWidget \**widget*) {#customStyleHint}

Resolve a dynamic [QStyle::StyleHint](https://doc.qt.io/qt-6/qstyle.html#StyleHint-enum) to query [QStyle::styleHint](https://doc.qt.io/qt-6/qstyle.html#styleHint)()

Returns a unique [QStyle::StyleHint](https://doc.qt.io/qt-6/qstyle.html#StyleHint-enum) or 0 in case the style doesn't support this element

`element` a valid element string appname.SH\_element, eg. "amarok.SH\_Analyzer"

`widget` the widget to paint this element for. This parameter is mandatory, nullptr will return 0!

### QStyle::SubElement KStyleExtensions::customSubElement(const QString &*element*, const QWidget \**widget*) {#customSubElement}

Resolve a dynamic [QStyle::SubElement](https://doc.qt.io/qt-6/qstyle.html#SubElement-enum) for eg. [QStyle::subElementRect](https://doc.qt.io/qt-6/qstyle.html#subElementRect)()

Returns a unique [QStyle::SubElement](https://doc.qt.io/qt-6/qstyle.html#SubElement-enum) or 0 in case the style doesn't support this element

`element` a valid element string appname.SE\_element, eg. "amarok.SE\_AnalyzerCanvas"

`widget` the widget to paint this element for. This parameter is mandatory, nullptr will return 0!
