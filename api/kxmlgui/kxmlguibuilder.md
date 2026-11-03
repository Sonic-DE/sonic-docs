---
title: "KXMLGUIBuilder Class"
description: "Collection of convenience classes and widgets to manage your own main QtWidgets window."
---

# KXMLGUIBuilder Class

Collection of convenience classes and widgets to manage your own main QtWidgets window. [More...](#details)

- **Header:** `#include <KXMLGUIBuilder>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherited By:** [KXmlGuiWindow](kxmlguiwindow.md)

[List of all members, including inherited members](kxmlguibuilder-members.md)

## Public Functions

- [KXMLGUIBuilder(QWidget \*widget)](#KXMLGUIBuilder)
- [~KXMLGUIBuilder()](#dtor.KXMLGUIBuilder)
- [QWidget \*createContainer(QWidget \*parent, int index, const QDomElement &element, QAction \*&containerAction)](#createContainer)
- [void removeContainer(QWidget \*container, QWidget \*parent, QDomElement &element, QAction \*containerAction)](#removeContainer)

## Detailed Description {#details}

Implements the creation of the GUI (menubar, menus and toolbars) as requested by the GUI factory.

The virtual methods are mostly for historical reasons, there isn't really a need to derive from [KXMLGUIBuilder](kxmlguibuilder.md) anymore.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KXMLGUIBuilder::KXMLGUIBuilder(QWidget \**widget*) {#KXMLGUIBuilder}

Constructs a new [KXMLGUIBuilder](kxmlguibuilder.md) object from `widget`.

### \[virtual noexcept\] KXMLGUIBuilder::~KXMLGUIBuilder() {#dtor.KXMLGUIBuilder}

Destructor.

### \[virtual\] QWidget \*KXMLGUIBuilder::createContainer(QWidget \**parent*, int *index*, const QDomElement &*element*, QAction \*&*containerAction*) {#createContainer}

Creates a container (menubar/menu/toolbar/statusbar/separator/...) from an `element` at `index` in the XML file.

`parent` The parent for the container.

`index` The index where the container should be inserted into the parent container/widget.

`element` The element from the DOM tree describing the container (use it to access container specified attributes or child elements).

`containerAction` The action created for this container; used for e.g. passing to [removeContainer](kxmlguibuilder.md#removeContainer).

### \[virtual\] void KXMLGUIBuilder::removeContainer(QWidget \**container*, QWidget \**parent*, QDomElement &*element*, QAction \**containerAction*) {#removeContainer}

Removes the given `container`.

`parent` The parent for the container.

`element` The element from the DOM tree describing the container (use it to access container specified attributes or child elements).

`containerAction` The action created for this container.
