---
title: "KXMLGUIFactory Class"
description: "Collection of convenience classes and widgets to manage your own main QtWidgets window."
---

# KXMLGUIFactory Class

Collection of convenience classes and widgets to manage your own main QtWidgets window. [More...](#details)

- **Header:** `#include <KXMLGUIFactory>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kxmlguifactory-members.md)

## Public Functions

- [KXMLGUIFactory(KXMLGUIBuilder \*builder, QObject \*parent = nullptr)](#KXMLGUIFactory)
- [~KXMLGUIFactory()](#dtor.KXMLGUIFactory)
- [void addClient(KXMLGUIClient \*client)](#addClient)
- [QList\<KXMLGUIClient \*\> clients() const](#clients)
- [QWidget \*container(const QString &containerName, KXMLGUIClient \*client, bool useTagName = false)](#container)
- [void refreshActionProperties()](#refreshActionProperties)
- [void removeClient(KXMLGUIClient \*client)](#removeClient)
- [void reset()](#reset)
- [void resetContainer(const QString &containerName, bool useTagName = false)](#resetContainer)

## Public Slots

- [void showConfigureShortcutsDialog()](#showConfigureShortcutsDialog)

## Signals

- [void makingChanges(bool)](#makingChanges)
- [void shortcutsSaved()](#shortcutsSaved)

## Detailed Description {#details}

[KXMLGUIFactory](kxmlguifactory.md), together with [KXMLGUIClient](kxmlguiclient.md) objects, can be used to create a GUI of container widgets (like menus, toolbars, etc.) and container items (menu items, toolbar buttons, etc.) from an XML document and action objects.

Each [KXMLGUIClient](kxmlguiclient.md) represents a part of the GUI, composed from containers and actions. [KXMLGUIFactory](kxmlguifactory.md) takes care of building (with the help of a [KXMLGUIBuilder](kxmlguibuilder.md)) and merging the GUI from an unlimited number of clients.

Each client provides XML through a [QDomDocument](https://doc.qt.io/qt-6/qdomdocument.html) and actions through a [KActionCollection](kactioncollection.md) . The XML document contains the rules for how to merge the GUI.

[KXMLGUIFactory](kxmlguifactory.md) processes the DOM tree provided by a client and plugs in the client's actions, according to the XML and the merging rules of previously inserted clients. Container widgets are built via a [KXMLGUIBuilder](kxmlguibuilder.md) , which has to be provided with the [KXMLGUIFactory](kxmlguifactory.md) constructor.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KXMLGUIFactory::KXMLGUIFactory(KXMLGUIBuilder \**builder*, QObject \**parent* = nullptr) {#KXMLGUIFactory}

Constructs a [KXMLGUIFactory](kxmlguifactory.md).

The provided `builder` [KXMLGUIBuilder](kxmlguibuilder.md) with the given `parent` will be called for creating and removing container widgets when clients are added/removed from the GUI.

Note that the ownership of the given [KXMLGUIBuilder](kxmlguibuilder.md) object won't be transferred to this [KXMLGUIFactory](kxmlguifactory.md), so you have to take care of deleting it properly.

### \[override virtual noexcept\] KXMLGUIFactory::~KXMLGUIFactory() {#dtor.KXMLGUIFactory}

Destructor.

### void KXMLGUIFactory::addClient(KXMLGUIClient \**client*) {#addClient}

Creates the GUI described by the [QDomDocument](https://doc.qt.io/qt-6/qdomdocument.html) of the `client`, using the client's actions, and merges it with the previously created GUI.

This also means that the order in which clients are added to the factory is relevant; assuming that your application supports plugins, you should first add your application to the factory and then the plugin, so that the plugin's UI is merged into the UI of your application, and not the other way round.

### QList\<KXMLGUIClient \*\> KXMLGUIFactory::clients() const {#clients}

Returns a list of all clients currently added to this factory.

### QWidget \*KXMLGUIFactory::container(const QString &*containerName*, KXMLGUIClient \**client*, bool *useTagName* = false) {#container}

Use this method to get access to a container widget with the name specified with `containerName` that is owned by the `client`.

The container name is specified with a "name" attribute in the XML document.

This function is particularly useful for getting hold of a popupmenu defined in an XMLUI file.

For instance:

```cpp
QMenu *popup = static_cast<QMenu*>(guiFactory()->container("my_popup",this));
```

Where "my\_popup" is the name of the menu in the XMLUI file, and "this" is XMLGUIClient which owns the popupmenu (e.g. the mainwindow, or the part, or the plugin...).

`containerName` The name of the container widget.

`client` Owner of the container widget.

`useTagName` Whether to compare the specified name with the name attribute or the tag name.

This method may return nullptr if no container with the given name exists or if the container is not owned by the client.

### \[signal\] void KXMLGUIFactory::makingChanges(*bool*) {#makingChanges}

Emitted when the factory is currently making changes to the GUI, i.e. adding or removing clients.

makingChanges(true) is emitted before any change happens, and makingChanges(false) is emitted after the change is done.

This allows e.g. [KMainWindow](kmainwindow.md) to know that the GUI is being changed programmatically and not by the user (so there is no reason to save toolbar settings afterwards).

### void KXMLGUIFactory::refreshActionProperties() {#refreshActionProperties}

Use this method to reset and reread action properties (shortcuts, etc.) for all actions.

This is needed, for example, when you change shortcuts scheme at runtime.

### void KXMLGUIFactory::removeClient(KXMLGUIClient \**client*) {#removeClient}

Removes the GUI described by the `client` by unplugging all provided actions and removing all owned containers (and storing container state information in the given client).

### void KXMLGUIFactory::reset() {#reset}

Use this method to free all memory allocated by the [KXMLGUIFactory](kxmlguifactory.md).

This deletes the internal node tree and therefore resets the internal state of the class. Please note that the actual GUI is NOT touched at all, meaning no containers are deleted nor any actions unplugged. That is something you have to do on your own. So use this method only if you know what you are doing :-)

> **Note:** This will call [KXMLGUIClient::setFactory](kxmlguiclient.md#setFactory)(nullptr) for all inserted clients).

### void KXMLGUIFactory::resetContainer(const QString &*containerName*, bool *useTagName* = false) {#resetContainer}

Free all memory allocated by the [KXMLGUIFactory](kxmlguifactory.md) for a container named `containerName`, including all child containers and actions.

Additionally, you may set whether to compare the specified `containerName` with the name attribute or the tag name.

This deletes the internal node subtree for the specified container. The actual GUI is not touched, no containers are deleted or any actions unplugged.

Use this method only if you know what you are doing :-)

`useTagName` Whether to compare the specified name with the name attribute.

> **Note:** This will call [KXMLGUIClient::setFactory](kxmlguiclient.md#setFactory)(nullptr) for all clients of the container).

### \[signal\] void KXMLGUIFactory::shortcutsSaved() {#shortcutsSaved}

Emitted when the shortcuts have been saved (i.e. the user accepted the dialog).

If you're using multiple instances of the same [KXMLGUIClient](kxmlguiclient.md), you probably want to connect to this signal and call `KXMLGUIClient::reloadXML()` for each of your KXMLGUIClients, so that the other instances update their shortcuts settings.

### \[slot\] void KXMLGUIFactory::showConfigureShortcutsDialog() {#showConfigureShortcutsDialog}

Shows a dialog ([KShortcutsDialog](kshortcutsdialog.md)) that lists every action in this factory, and that can be used to change the shortcuts associated with each action.

This slot can be connected directly to the configure shortcuts action, for example:

```cpp
KStandardAction::keyBindings(guiFactory(), &KXMLGUIFactory::showConfigureShortcutsDialog, actionCollection());
```

This method constructs a [KShortcutsDialog](kshortcutsdialog.md) with the default arguments ([KShortcutsEditor::AllActions](kshortcutseditor.md#ActionType-enum) and [KShortcutsEditor::LetterShortcutsAllowed](kshortcutseditor.md#LetterShortcuts-enum)).

By default the changes will be saved back to the `*ui.rc` file they were initially read from.

If you need to run some extra code if the dialog is accepted and the settings are saved, you can simply connect to the [KXMLGUIFactory::shortcutsSaved](kxmlguifactory.md#shortcutsSaved)() signal before calling this method, for example:

```cpp
connect(guiFactory(), &KXMLGUIFactory::shortcutsSaved, this, &MyClass::slotShortcutSaved);
guiFactory()->showConfigureShortcutsDialog();
```

*See also* [KShortcutsDialog](kshortcutsdialog.md), [KShortcutsEditor::ActionTypes](kshortcutseditor.md#ActionType-enum), [KShortcutsEditor::LetterShortcuts](kshortcutseditor.md#LetterShortcuts-enum)
