---
title: "KParts::Part Class"
description: "Base class for parts."
---

# KParts::Part Class

Base class for parts. [More...](#details)

- **Header:** `#include <KParts/Part>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html) and [KParts::PartBase](kparts-partbase.md)
- **Inherited By:** [KParts::ReadOnlyPart](kparts-readonlypart.md)

[List of all members, including inherited members](kparts-part-members.md)

## Public Functions

- [Part(QObject \*parent = nullptr, const KPluginMetaData &data = {})](#Part)
- [KParts::Part \*hitTest(QWidget \*widget, const QPoint &globalPos)](#hitTest)
- [KParts::PartManager \*manager() const](#manager)
- [KPluginMetaData metaData() const](#metaData)
- [void setAutoDeletePart(bool autoDeletePart)](#setAutoDeletePart)
- [void setAutoDeleteWidget(bool autoDeleteWidget)](#setAutoDeleteWidget)
- [QWidget \*widget()](#widget)

## Signals

- [void setStatusBarText(const QString &text)](#setStatusBarText)
- [void setWindowCaption(const QString &caption)](#setWindowCaption)

## Protected Functions

- [void guiActivateEvent(KParts::GUIActivateEvent \*event)](#guiActivateEvent)
- [QWidget \*hostContainer(const QString &containerName)](#hostContainer)
- [void partActivateEvent(KParts::PartActivateEvent \*event)](#partActivateEvent)
- [void setWidget(QWidget \*widget)](#setWidget)

## Detailed Description {#details}

A "part" is a GUI component, featuring:

- A widget embeddedable in any application.
- GUI elements that will be merged in the "host" user interface (menubars, toolbars... ).

### About the widget: {#about-the-widget}

Note that [KParts::Part](kparts-part.md) does not inherit [QWidget](https://doc.qt.io/qt-6/qwidget.html). This is due to the fact that the "visual representation" will probably not be a mere [QWidget](https://doc.qt.io/qt-6/qwidget.html), but an elaborate one. That's why when implementing your [KParts::Part](kparts-part.md) (or derived) you should call KParts::Part::setWidget() in your constructor.

### About the GUI elements: {#about-the-gui-elements}

Those elements trigger actions, defined by the part ( [action](../kxmlgui/kxmlguiclient.md#action)()). The layout of the actions in the GUI is defined by an XML file ( [setXMLFile](../kxmlgui/kxmlguiclient.md#setXMLFile)()).

See also [ReadOnlyPart](kparts-readonlypart.md) and [ReadWritePart](kparts-readwritepart.md), which define the framework for a "viewer" part and for an "editor"-like part. Use Part directly only if your part doesn't fit into those.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Part::Part(QObject \**parent* = nullptr, const KPluginMetaData &*data* = {}) {#Part}

Constructor.

`parent` Parent object of the part.

`data` [KPluginMetaData](../kcoreaddons/kpluginmetadata.md) associated with this part, see [Part::metaData](kparts-part.md#metaData)()

### \[virtual protected\] void Part::guiActivateEvent(KParts::GUIActivateEvent \**event*) {#guiActivateEvent}

Convenience method which is called when the Part received a [GUIActivateEvent](kparts-guiactivateevent.md) . Reimplement this if you don't want to reimplement event and test for the event yourself or even install an event filter.

### \[virtual\] KParts::Part \*Part::hitTest(QWidget \**widget*, const QPoint &*globalPos*) {#hitTest}

Returns the part (this, or a child part) at the given global position. This is called by the part manager to ask whether a part should be activated when clicking somewhere. In most cases the default implementation is enough. Reimplement this if your part has child parts in some areas (like in khtml or koffice)

`widget` the part widget being clicked - usually the same as [widget](kparts-part.md#widget)(), except in koffice.

`globalPos` the mouse coordinates in global coordinates

### \[protected\] QWidget \*Part::hostContainer(const QString &*containerName*) {#hostContainer}

Convenience method for [KXMLGUIFactory::container](../kxmlgui/kxmlguifactory.md#container).

Returns a container widget owned by the Part's GUI.

### KParts::PartManager \*Part::manager() const {#manager}

Returns the part manager handling this part, if any (0L otherwise).

### KPluginMetaData Part::metaData() const {#metaData}

### \[virtual protected\] void Part::partActivateEvent(KParts::PartActivateEvent \**event*) {#partActivateEvent}

Convenience method which is called when the Part received a [PartActivateEvent](kparts-partactivateevent.md) . Reimplement this if you don't want to reimplement event and test for the event yourself or even install an event filter.

### void Part::setAutoDeletePart(bool *autoDeletePart*) {#setAutoDeletePart}

By default, the part deletes itself when its widget is deleted. The hosting application can call setAutoDeletePart(false) to disable this behavior, to be able to delete the widget and then the part, independently. This is a method for the hosting application only, Part subclasses should never call this.

### void Part::setAutoDeleteWidget(bool *autoDeleteWidget*) {#setAutoDeleteWidget}

By default, the widget is deleted by the part when the part is deleted. The hosting application can call setAutoDeleteWidget(false) to disable this behavior, given that the widget is usually deleted by its parent widget anyway. This is a method for the hosting application only, Part subclasses should never call this.

### \[signal\] void Part::setStatusBarText(const QString &*text*) {#setStatusBarText}

Emitted by the part, to set a text in the statusbar of the window(s) hosting this part

### \[virtual protected\] void Part::setWidget(QWidget \**widget*) {#setWidget}

Set the main widget.

Call this in the Part-inherited class constructor.

*See also* [widget](kparts-part.md#widget)()

### \[signal\] void Part::setWindowCaption(const QString &*caption*) {#setWindowCaption}

Emitted by the part, to set the caption of the window(s) hosting this part

> **Note:** this signal has only an effect on the window title if window title handling is enabled, see [KParts::MainWindow::setWindowTitleHandling](kparts-mainwindow.md#setWindowTitleHandling)

### \[virtual\] QWidget \*Part::widget() {#widget}

Returns the widget defined by this part, set by [setWidget](kparts-part.md#setWidget)().

*See also* [setWidget](kparts-part.md#setWidget)()
