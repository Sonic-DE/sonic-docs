---
title: "KXMLGUIClient Class"
description: "Collection of convenience classes and widgets to manage your own main QtWidgets window."
---

# KXMLGUIClient Class

Collection of convenience classes and widgets to manage your own main QtWidgets window. [More...](#details)

- **Header:** `#include <KXMLGUIClient>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherited By:** [KXmlGuiWindow](kxmlguiwindow.md)

[List of all members, including inherited members](kxmlguiclient-members.md)

## Public Functions

- [KXMLGUIClient()](#KXMLGUIClient)
- [KXMLGUIClient(KXMLGUIClient \*parent)](#KXMLGUIClient-1)
- [~KXMLGUIClient()](#dtor.KXMLGUIClient)
- [QAction \*action(const QDomElement &element) const](#action)
- [QAction \*action(const QString &name) const](#action-1) (since 6.0)
- [KActionCollection \*actionCollection() const](#actionCollection)
- [QList\<KXMLGUIClient \*\> childClients()](#childClients)
- [KXMLGUIBuilder \*clientBuilder() const](#clientBuilder)
- [QString componentName() const](#componentName)
- [QDomDocument domDocument() const](#domDocument)
- [KXMLGUIFactory \*factory() const](#factory)
- [void insertChildClient(KXMLGUIClient \*child)](#insertChildClient)
- [KXMLGUIClient \*parentClient() const](#parentClient)
- [void plugActionList(const QString &name, const QList\<QAction \*\> &actionList)](#plugActionList)
- [void reloadXML()](#reloadXML)
- [void removeChildClient(KXMLGUIClient \*child)](#removeChildClient)
- [void replaceXMLFile(const QString &xmlfile, const QString &localxmlfile, bool merge = false)](#replaceXMLFile)
- [void setClientBuilder(KXMLGUIBuilder \*builder)](#setClientBuilder)
- [void setFactory(KXMLGUIFactory \*factory)](#setFactory)
- [void unplugActionList(const QString &name)](#unplugActionList)
- [QString xmlFile() const](#xmlFile)

## Static Public Members

- [QString findVersionNumber(const QString &xml)](#findVersionNumber)
- [QString standardsXmlFileLocation()](#standardsXmlFileLocation)

## Protected Functions

- [void loadStandardsXmlFile()](#loadStandardsXmlFile)
- [void setComponentName(const QString &componentName, const QString &componentDisplayName)](#setComponentName)
- [void setDOMDocument(const QDomDocument &document, bool merge = false)](#setDOMDocument)
- [void setLocalXMLFile(const QString &file)](#setLocalXMLFile)
- [void setXML(const QString &document, bool merge = false)](#setXML)
- [void setXMLFile(const QString &file, bool merge = false, bool setXMLDoc = true)](#setXMLFile)
- [void stateChanged(const QString &newstate, KXMLGUIClient::ReverseStateChange reverse = StateNoReverse)](#stateChanged)

## Detailed Description {#details}

A [KXMLGUIClient](kxmlguiclient.md) can be used with [KXMLGUIFactory](kxmlguifactory.md) to create a GUI from actions and an XML document, and can be dynamically merged with other KXMLGUIClients.

## Member Function Documentation {#member-function-documentation}

### KXMLGUIClient::KXMLGUIClient() {#KXMLGUIClient}

Constructs a [KXMLGUIClient](kxmlguiclient.md) that can be used with a [KXMLGUIFactory](kxmlguifactory.md) to create a GUI from actions and an XML document, and that can be dynamically merged with other KXMLGUIClients.

### \[explicit\] KXMLGUIClient::KXMLGUIClient(KXMLGUIClient \**parent*) {#KXMLGUIClient-1}

Constructs a [KXMLGUIClient](kxmlguiclient.md) that can be used with a [KXMLGUIFactory](kxmlguifactory.md) to create a GUI from actions and an XML document, and that can be dynamically merged with other KXMLGUIClients.

This constructor takes an additional `parent` argument, which makes the client a child client of the parent.

Child clients are automatically added to the GUI if the parent is added.

### \[virtual noexcept\] KXMLGUIClient::~KXMLGUIClient() {#dtor.KXMLGUIClient}

Destructs the [KXMLGUIClient](kxmlguiclient.md).

If the client was in a factory, the factory is NOT informed about the client being removed. This is a feature, it makes window destruction fast (the xmlgui is not updated for every client being deleted), but if you want to simply remove one client and to keep using the window, make sure to call factory-\>removeClient(client) before deleting the client.

### \[virtual\] QAction \*KXMLGUIClient::action(const QDomElement &*element*) const {#action}

Retrieves an action for a given [QDomElement](https://doc.qt.io/qt-6/qdomelement.html) `element`.

The default implementation uses the "name" attribute to query the action object via the other action() method.

### \[since 6.0\] QAction \*KXMLGUIClient::action(const QString &*name*) const {#action-1}

Retrieves an action of the client by `name`.

If not found, it looks in its child clients.

This method is provided for convenience, as it uses [actionCollection](kxmlguiclient.md#actionCollection)() to get the action object.

This function was introduced in Qt 6.0.

### \[virtual\] KActionCollection \*KXMLGUIClient::actionCollection() const {#actionCollection}

Retrieves the entire action collection for the GUI client.

### QList\<KXMLGUIClient \*\> KXMLGUIClient::childClients() {#childClients}

Retrieves a list of all child clients.

### KXMLGUIBuilder \*KXMLGUIClient::clientBuilder() const {#clientBuilder}

Retrieves the client's GUI builder or nullptr if no client specific builder has been assigned via [setClientBuilder](kxmlguiclient.md#setClientBuilder)().

*See also* [setClientBuilder](kxmlguiclient.md#setClientBuilder)()

### \[virtual\] QString KXMLGUIClient::componentName() const {#componentName}

Returns the component name for this GUI client.

*See also* [setComponentName](kxmlguiclient.md#setComponentName)()

### \[virtual\] QDomDocument KXMLGUIClient::domDocument() const {#domDocument}

Returns the parsed XML in a [QDomDocument](https://doc.qt.io/qt-6/qdomdocument.html), set by [setXMLFile](kxmlguiclient.md#setXMLFile)() or [setXML](kxmlguiclient.md#setXML)().

This document describes the layout of the GUI.

### KXMLGUIFactory \*KXMLGUIClient::factory() const {#factory}

Retrieves a pointer to the [KXMLGUIFactory](kxmlguifactory.md) this client is associated with.

Will return nullptr if the client's GUI has not been built by a [KXMLGUIFactory](kxmlguifactory.md).

*See also* [setFactory](kxmlguiclient.md#setFactory)()

### \[static\] QString KXMLGUIClient::findVersionNumber(const QString &*xml*) {#findVersionNumber}

Returns the version number of the given `xml` data belonging to an XML rc file.

### void KXMLGUIClient::insertChildClient(KXMLGUIClient \**child*) {#insertChildClient}

Makes a client a `child` client of another client.

Usually you don't need to call this method, as it is called automatically when using the second constructor, which takes a parent argument.

### \[protected\] void KXMLGUIClient::loadStandardsXmlFile() {#loadStandardsXmlFile}

Load the ui\_standards.rc file.

Usually followed by [setXMLFile](kxmlguiclient.md#setXMLFile)([xmlFile](kxmlguiclient.md#xmlFile), true) for merging.

### KXMLGUIClient \*KXMLGUIClient::parentClient() const {#parentClient}

Returns a pointer to the parent client or nullptr if it has no parent client assigned.

KXMLGUIClients can form a simple child/parent object tree.

### void KXMLGUIClient::plugActionList(const QString &*name*, const QList\<QAction \*\> &*actionList*) {#plugActionList}

Plugs a new `actionList` with the given `name`.

ActionLists are a way for XMLGUI to support dynamic lists of actions. E.g. if you are writing a file manager, and there is a menu file whose contents depend on the mimetype of the file that is selected, then you can achieve this using ActionLists. It works as follows: In your xxxui.rc file (the one that you set in [setXMLFile](kxmlguiclient.md#setXMLFile)() / pass to setupGUI()), you put a tag \<ActionList name="xxx"\>.

Example:

```cpp
<gui name="xxx_part" version="1">
<MenuBar>
  <Menu name="file">
    ...  <!-- some useful actions-->
    <ActionList name="xxx_file_actionlist" />
    ...  <!-- even more useful actions-->
  </Menu>
  ...
</MenuBar>
</gui>
```

This tag will get expanded to a list of actions. In the example above ( a file manager with a dynamic file menu ), you would call:

```cpp
QList<QAction*> file_actions;
for( ... )
  if( ... )
    file_actions.append( cool_action );
unplugActionList( "xxx_file_actionlist" );
plugActionList( "xxx_file_actionlist", file_actions );
```

Every time a file is selected, unselected or ...

> **Note:** You should not call [KXmlGuiWindow::createGUI](kxmlguiwindow.md#createGUI)() after calling this function. In fact, that would remove the newly added actionlists again...

> **Note:** Forgetting to call [unplugActionList](kxmlguiclient.md#unplugActionList)() before plugActionList() would leave the previous actions in the menu too..

*See also* [unplugActionList](kxmlguiclient.md#unplugActionList)()

### void KXMLGUIClient::reloadXML() {#reloadXML}

Forces this client to re-read its XML resource file.

This is intended to be used when you know that the resource file has changed and you will soon be rebuilding the GUI. This will only have an effect if the client is then removed and re-added to the factory.

This method is only for child clients, do not call it for a mainwindow! For a mainwindow, use [loadStandardsXmlFile](kxmlguiclient.md#loadStandardsXmlFile) + setXmlFile([xmlFile](kxmlguiclient.md#xmlFile)()) instead.

### void KXMLGUIClient::removeChildClient(KXMLGUIClient \**child*) {#removeChildClient}

Removes the given `child` from the client's children list.

### void KXMLGUIClient::replaceXMLFile(const QString &*xmlfile*, const QString &*localxmlfile*, bool *merge* = false) {#replaceXMLFile}

Sets a new `xmlfile` and `localxmlfile`.

The purpose of this public method is to allow non-inherited objects to replace the ui definition of an embedded client with a customized version. It corresponds to the usual calls to [setXMLFile](kxmlguiclient.md#setXMLFile)() and [setLocalXMLFile](kxmlguiclient.md#setLocalXMLFile)().

`xmlfile` The xml file to use. Contrary to [setXMLFile](kxmlguiclient.md#setXMLFile)(), this must be an absolute file path.

`localxmlfile` The local xml file to set. This should be the full path to a writeable file, usually using [QStandardPaths::writableLocation](https://doc.qt.io/qt-6/qstandardpaths.html#writableLocation). You can set this to QString(), but no user changes to shortcuts / toolbars will be possible in this case.

`merge` Whether to merge with the global document.

> **Note:** If in any doubt whether you need this or not, use [setXMLFile](kxmlguiclient.md#setXMLFile)() and [setLocalXMLFile](kxmlguiclient.md#setLocalXMLFile)(), instead of this function.

> **Note:** Just like [setXMLFile](kxmlguiclient.md#setXMLFile)(), this function has to be called before the client is added to a [KXMLGUIFactory](kxmlguifactory.md) in order to have an effect.

*See also* [setLocalXMLFile](kxmlguiclient.md#setLocalXMLFile)()

### void KXMLGUIClient::setClientBuilder(KXMLGUIBuilder \**builder*) {#setClientBuilder}

Use this method to assign your `builder` instance to the client (so that the [KXMLGUIFactory](kxmlguifactory.md) can use it when building the client's GUI).

A client can have its own [KXMLGUIBuilder](kxmlguibuilder.md).

Client specific guibuilders are useful if you want to create custom container widgets for your GUI.

*See also* [clientBuilder](kxmlguiclient.md#clientBuilder)()

### \[virtual protected\] void KXMLGUIClient::setComponentName(const QString &*componentName*, const QString &*componentDisplayName*) {#setComponentName}

Sets the component name for this part.

Call this first in the inherited class constructor (at least before [setXMLFile](kxmlguiclient.md#setXMLFile)()).

`componentName` The name of the directory where the XMLGUI files will be found.

`componentDisplayName` A user-visible name (e.g. for the toolbar editor).

*See also* [componentName](kxmlguiclient.md#componentName)()

### \[virtual protected\] void KXMLGUIClient::setDOMDocument(const QDomDocument &*document*, bool *merge* = false) {#setDOMDocument}

Sets the `document` for the part, describing the layout of the GUI, and whether to `merge` with the global document.

Call this in the Part-inherited class constructor if you don't call [setXMLFile](kxmlguiclient.md#setXMLFile)() or [setXML](kxmlguiclient.md#setXML)().

> **Warning:** Using this method is not recommended. Many code paths lead to reloading from the XML file on disk. And editing toolbars requires that the result is written to disk anyway, and loaded from there the next time.

For application-specific changes to a client's XML, it is a better idea to save the modified dom document to an app/default-client.xml and define a local-xml-file to something specific like app/local-client.xml, using [replaceXMLFile](kxmlguiclient.md#replaceXMLFile)(). See kdepimlibs/kontactinterface/plugin.cpp for an example.

### void KXMLGUIClient::setFactory(KXMLGUIFactory \**factory*) {#setFactory}

Sets a new `factory`.

This method is called by the [KXMLGUIFactory](kxmlguifactory.md) as soon as the client is added to the [KXMLGUIFactory](kxmlguifactory.md)'s GUI.

*See also* [factory](kxmlguiclient.md#factory)()

### \[virtual protected\] void KXMLGUIClient::setLocalXMLFile(const QString &*file*) {#setLocalXMLFile}

Set the full path to the "local" xml `file` used for saving toolbar and shortcut changes.

You normally don't need to call this if you pass a simple filename to [setXMLFile](kxmlguiclient.md#setXMLFile)().

### \[virtual protected\] void KXMLGUIClient::setXML(const QString &*document*, bool *merge* = false) {#setXML}

Sets the XML `document` for the part and whether to `merge` with the global document.

Call this in the Part-inherited class constructor if you don't call [setXMLFile](kxmlguiclient.md#setXMLFile)().

### \[virtual protected\] void KXMLGUIClient::setXMLFile(const QString &*file*, bool *merge* = false, bool *setXMLDoc* = true) {#setXMLFile}

Sets the name of the rc `file` containing the XML for the part.

Call this in the inherited class constructor, for parts and plugins.

> **Note:** For mainwindows, don't call this, pass the name of the xml file to [KXmlGuiWindow::setupGUI](kxmlguiwindow.md#setupGUI)() or [KXmlGuiWindow::createGUI](kxmlguiwindow.md#createGUI)().

`file` Either an absolute path for the file, or simply the filename. See below for details. If you pass an absolute path here, make sure to also call [setLocalXMLFile](kxmlguiclient.md#setLocalXMLFile), otherwise toolbar editing won't work.

`merge` Whether to merge with the global document.

`setXMLDoc` Specify whether to call [setXML](kxmlguiclient.md#setXML). Default is true.

The preferred way to call this method is with a simple filename for the `file` argument.

Since 5.1, the file will then be assumed to be installed in DATADIR/kxmlgui5/, under a directory named after the component name. You should use ${KDE\_INSTALL\_KXMLGUIDIR}/componentname in your CMakeLists.txt file to install the .rc file(s).

Since 5.4, the file will then be assumed to be installed in a Qt resource in :/kxmlgui5/, under a directory named after the component name.

### \[static protected\] QString KXMLGUIClient::standardsXmlFileLocation() {#standardsXmlFileLocation}

Returns the full path to the ui\_standards.rc, always non-empty.

Might return a resource path.

### \[virtual protected\] void KXMLGUIClient::stateChanged(const QString &*newstate*, KXMLGUIClient::ReverseStateChange *reverse* = StateNoReverse) {#stateChanged}

Emitted when an action has changed state to `newstate`.

Actions can collectively be assigned a "State". To accomplish this the respective actions are tagged as \<enable\> or \<disable\> in a \<State\> \</State\> group of the XMLfile. During program execution the programmer can call stateChanged() to set actions to a defined state.

`newstate` Name of a State in the XMLfile.

`reverse` If the `reverse` flag is set to StateReverse, the State is reversed (actions to be enabled will be disabled and action to be disabled will be enabled).

### void KXMLGUIClient::unplugActionList(const QString &*name*) {#unplugActionList}

Unplugs the action list `name` from the XMLGUI.

Calling this removes the specified action list, i.e. this is the complement to [plugActionList](kxmlguiclient.md#plugActionList)(). See [plugActionList](kxmlguiclient.md#plugActionList)() for a more detailed example.

*See also* [plugActionList](kxmlguiclient.md#plugActionList)()

### \[virtual\] QString KXMLGUIClient::xmlFile() const {#xmlFile}

Returns the name of the XML file as set by [setXMLFile](kxmlguiclient.md#setXMLFile)(); if [setXML](kxmlguiclient.md#setXML)() is used directly, then this will return an empty string.

The filename that this returns is obvious for components as each component has exactly one XML file. In non-components, however, there are usually two: the global file and the local file. This function doesn't really care about that, though. It will always return the last XML file set. This, in almost all cases, will be the local XML file.
