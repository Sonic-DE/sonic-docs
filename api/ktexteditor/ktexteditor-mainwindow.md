---
title: "KTextEditor::MainWindow Class"
description: "This class allows the application that embeds the KTextEditor component to allow it to access parts of its main window."
---

# KTextEditor::MainWindow Class

This class allows the application that embeds the [KTextEditor](ktexteditor-module.md) component to allow it to access parts of its main window. [More...](#details)

- **Header:** `#include <KTextEditor/MainWindow>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ktexteditor-mainwindow-members.md)

## Public Types

- [enum MainWindow::ToolViewPosition](#ToolViewPosition-enum)

## Public Functions

- [MainWindow(QObject \*parent)](#MainWindow)
- [~MainWindow()](#dtor.MainWindow)
- [KTextEditor::View \*activateView(KTextEditor::Document \*document)](#activateView)
- [void activateWidget(QWidget \*widget)](#activateWidget) (since 6.0)
- [KTextEditor::View \*activeView()](#activeView)
- [QWidget \*activeWidget()](#activeWidget) (since 6.0)
- [bool addWidget(QWidget \*widget)](#addWidget)
- [void addWidgetToViewBar(KTextEditor::View \*view, QWidget \*bar)](#addWidgetToViewBar)
- [bool closeSplitView(KTextEditor::View \*view)](#closeSplitView)
- [bool closeView(KTextEditor::View \*view)](#closeView)
- [QWidget \*createToolView(KTextEditor::Plugin \*plugin, const QString &identifier, KTextEditor::MainWindow::ToolViewPosition pos, const QIcon &icon, const QString &text)](#createToolView)
- [QWidget \*createViewBar(KTextEditor::View \*view)](#createViewBar)
- [void deleteViewBar(KTextEditor::View \*view)](#deleteViewBar)
- [KXMLGUIFactory \*guiFactory()](#guiFactory)
- [bool hideToolView(QWidget \*widget)](#hideToolView)
- [void hideViewBar(KTextEditor::View \*view)](#hideViewBar)
- [bool moveToolView(QWidget \*widget, KTextEditor::MainWindow::ToolViewPosition pos)](#moveToolView)
- [KTextEditor::View \*openUrl(const QUrl &url, const QString &encoding = QString())](#openUrl)
- [QObject \*pluginView(const QString &name)](#pluginView)
- [bool removeWidget(QWidget \*widget)](#removeWidget) (since 6.0)
- [bool showMessage(const QVariantMap &message)](#showMessage)
- [bool showPluginConfigPage(KTextEditor::Plugin \*plugin, int page)](#showPluginConfigPage)
- [bool showToolView(QWidget \*widget)](#showToolView)
- [void showViewBar(KTextEditor::View \*view)](#showViewBar)
- [void splitView(Qt::Orientation orientation)](#splitView)
- [QList\<KTextEditor::View \*\> views()](#views)
- [bool viewsInSameSplitView(KTextEditor::View \*view1, KTextEditor::View \*view2)](#viewsInSameSplitView)
- [QWidgetList widgets()](#widgets) (since 6.0)
- [QWidget \*window()](#window)

## Signals

- [void pluginViewCreated(const QString &name, QObject \*pluginView)](#pluginViewCreated)
- [void pluginViewDeleted(const QString &name, QObject \*pluginView)](#pluginViewDeleted)
- [void unhandledShortcutOverride(QEvent \*e)](#unhandledShortcutOverride)
- [void viewChanged(KTextEditor::View \*view)](#viewChanged)
- [void viewCreated(KTextEditor::View \*view)](#viewCreated)
- [void widgetAdded(QWidget \*widget)](#widgetAdded) (since 6.0)
- [void widgetRemoved(QWidget \*widget)](#widgetRemoved) (since 6.0)

## Detailed Description {#details}

For example the component can get a place to show view bar widgets (e.g. search&replace, goto line, ...). This is useful to e.g. have one place inside the window to show such stuff even if the application allows the user to have multiple split views available per window.

The application must pass a pointer to the [MainWindow](ktexteditor-mainwindow.md) object to the createView method on view creation and ensure that this main window stays valid for the complete lifetime of the view.

It must not reimplement this class but construct an instance and pass a pointer to a [QObject](https://doc.qt.io/qt-6/qobject.html) that has the required slots to receive the requests.

kte\_plugin\_hosting

## Member Type Documentation {#member-type-documentation}

### enum MainWindow::ToolViewPosition {#ToolViewPosition-enum}

Toolview position. A toolview can only be at one side at a time.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::MainWindow::Left` | `0` | Left side |
| `KTextEditor::MainWindow::Right` | `1` | Right side |
| `KTextEditor::MainWindow::Top` | `2` | Top side |
| `KTextEditor::MainWindow::Bottom` | `3` | Bottom side |

## Member Function Documentation {#member-function-documentation}

### MainWindow::MainWindow(QObject \**parent*) {#MainWindow}

Construct an [MainWindow](ktexteditor-mainwindow.md) wrapper object. The passed parent is both the parent of this [QObject](https://doc.qt.io/qt-6/qobject.html) and the receiver of all interface calls via invokeMethod.

`parent` is the object the calls are relayed to

### \[override virtual noexcept\] MainWindow::~MainWindow() {#dtor.MainWindow}

Virtual Destructor

### KTextEditor::View \*MainWindow::activateView(KTextEditor::Document \**document*) {#activateView}

Activate the view with the corresponding `document`. If none exist for this document, create one

`document` is the document

Returns activated view of this document, return nullptr if not possible

### \[since 6.0\] void MainWindow::activateWidget(QWidget \**widget*) {#activateWidget}

activate `widget`. If the widget is not present in the window, it will be added to the window

`widget` is the widget to activate

This function was introduced in Qt 6.0.

### KTextEditor::View \*MainWindow::activeView() {#activeView}

Access the active view. Returns active view, nullptr if not available

### \[since 6.0\] QWidget \*MainWindow::activeWidget() {#activeWidget}

returns the currently active widget. It can be a non-[KTextEditor::View](ktexteditor-view.md) widget or a [KTextEditor::View](ktexteditor-view.md)

This function was introduced in Qt 6.0.

### bool MainWindow::addWidget(QWidget \**widget*) {#addWidget}

Add a widget to the main window. This is useful to show non-[KTextEditor::View](ktexteditor-view.md) widgets in the main window. The host application should try to manage this like some [KTextEditor::View](ktexteditor-view.md) (e.g. as a tab) and provide the means to close it.

`widget` is the widget to add

Returns success, if false, the plugin needs to take care to show the widget itself, otherwise the main window will take ownership of the widget

### void MainWindow::addWidgetToViewBar(KTextEditor::View \**view*, QWidget \**bar*) {#addWidgetToViewBar}

Add a widget to the view bar.

`view` is the view for which the view bar is used

`bar` is the widget, shall have the viewBarParent() as parent widget

### bool MainWindow::closeSplitView(KTextEditor::View \**view*) {#closeSplitView}

Close the split view that contains the given view.

`view` is the view.

Returns true if the split view was closed.

### bool MainWindow::closeView(KTextEditor::View \**view*) {#closeView}

Close selected view

`view` is the view to close

Returns true if view was closed

### QWidget \*MainWindow::createToolView(KTextEditor::Plugin \**plugin*, const QString &*identifier*, KTextEditor::MainWindow::ToolViewPosition *pos*, const QIcon &*icon*, const QString &*text*) {#createToolView}

Create a new toolview with unique `identifier` at side `pos` with `icon` and caption `text`. Use the returned widget to embed your widgets.

`plugin` is the plugin which owns this tool view

`identifier` is unique identifier for this toolview

`pos` is the position for the toolview, if we are in session restore, this is only a preference

`icon` is the icon to use in the sidebar for the toolview

`text` is translated text (i18n()) to use in addition to icon

Returns created toolview on success, otherwise NULL

### QWidget \*MainWindow::createViewBar(KTextEditor::View \**view*) {#createViewBar}

Try to create a view bar for the given view.

`view` is the view for which we want a view bar

Returns suitable widget that can host view bars widgets or nullptr

### void MainWindow::deleteViewBar(KTextEditor::View \**view*) {#deleteViewBar}

Delete the view bar for the given view.

`view` is the view for which we want to delete the view bar

### KXMLGUIFactory \*MainWindow::guiFactory() {#guiFactory}

Accessor to the XMLGUIFactory.

Returns the mainwindow's [KXMLGUIFactory](../kxmlgui/kxmlguifactory.md), nullptr if not available

### bool MainWindow::hideToolView(QWidget \**widget*) {#hideToolView}

Hide the toolview `widget`.

`widget` is the toolview to hide, where the widget was constructed by [createToolView](ktexteditor-mainwindow.md#createToolView)().

Returns *true* on success, otherwise *false*

### void MainWindow::hideViewBar(KTextEditor::View \**view*) {#hideViewBar}

Hide the view bar for the given view

`view` is the view for which the view bar is used

### bool MainWindow::moveToolView(QWidget \**widget*, KTextEditor::MainWindow::ToolViewPosition *pos*) {#moveToolView}

Move the toolview `widget` to position `pos`.

`widget` is the toolview to move, where the widget was constructed by [createToolView](ktexteditor-mainwindow.md#createToolView)().

`pos` is the new position to move the widget to

Returns *true* on success, otherwise *false*

### KTextEditor::View \*MainWindow::openUrl(const QUrl &*url*, const QString &*encoding* = QString()) {#openUrl}

Open the document URL with the given encoding.

`url` is the document's URL

`encoding` is the preferred encoding. If encoding is QString() the encoding will be guessed or the default encoding will be used.

Returns a pointer to the created view for the new document, if a document with this url is already existing, its view will be activated, return nullptr if not possible

### QObject \*MainWindow::pluginView(const QString &*name*) {#pluginView}

Get a plugin view for the plugin with with identifier `name`.

`name` is the plugin's name

Returns pointer to the plugin view if a plugin with `name` is loaded and has a view for this mainwindow, otherwise NULL

### \[signal\] void MainWindow::pluginViewCreated(const QString &*name*, QObject \**pluginView*) {#pluginViewCreated}

This signal is emitted when the view of some Plugin is created for this main window.

`name` is the name of the plugin

`pluginView` is the new plugin view

### \[signal\] void MainWindow::pluginViewDeleted(const QString &*name*, QObject \**pluginView*) {#pluginViewDeleted}

This signal is emitted when the view of some Plugin got deleted.

> **Warning:** Do not access the data referenced by the pointer, it is already invalid. Use the pointer only to remove mappings in hash or maps

`name` is the name of the plugin

`pluginView` is the deleted plugin view

### \[since 6.0\] bool MainWindow::removeWidget(QWidget \**widget*) {#removeWidget}

remove this `widget` from this mainwindow. The widget will be deleted afterwards

`widget` is the widget to be removed

Returns true on success

This function was introduced in Qt 6.0.

### bool MainWindow::showMessage(const QVariantMap &*message*) {#showMessage}

Display a message to the user. The host application might show this inside a dedicated output view.

`message` is the incoming message we shall handle

Returns true, if the host application was able to handle the message, else false

details of message format:

message text, will be trimmed before output

message\["text"\] = i18n("your cool message")

the text will be split in lines, all lines beside the first can be collapsed away

message type, we support at the moment

message\["type"\] = "Error" message\["type"\] = "Warning" message\["type"\] = "Info" message\["type"\] = "Log"

this is take from https://microsoft.github.io/language-server-protocol/specification#window_showMessage MessageType of LSP

will lead to appropriate icons/... in the output view

a message should have some category, like Git, LSP, ....

message\["category"\] = i18n(...)

will be used to allow the user to filter for

one can additionally provide a categoryIcon

message\["categoryIcon"\] = QIcon(...)

the categoryIcon icon [QVariant](https://doc.qt.io/qt-6/qvariant.html) must contain a QIcon, nothing else!

A string token can be passed to allow to replace messages already send out with new ones. That is useful for e.g. progress output

message\["token"\] = "yourmessagetoken"

### bool MainWindow::showPluginConfigPage(KTextEditor::Plugin \**plugin*, int *page*) {#showPluginConfigPage}

Shows the `plugin`'s config page. The `page` specifies which config page will be shown, see KTextEditor::Plugin::configPages().

Returns *true* on success, otherwise *false*

### bool MainWindow::showToolView(QWidget \**widget*) {#showToolView}

Show the toolview `widget`.

`widget` is the toolview to show, where the widget was constructed by [createToolView](ktexteditor-mainwindow.md#createToolView)().

Returns *true* on success, otherwise *false* TODO add focus parameter: bool showToolView ([QWidget](https://doc.qt.io/qt-6/qwidget.html) \*widget, bool giveFocus );

### void MainWindow::showViewBar(KTextEditor::View \**view*) {#showViewBar}

Show the view bar for the given view

`view` is the view for which the view bar is used

### void MainWindow::splitView(Qt::Orientation *orientation*) {#splitView}

Split current view space according to `orientation`

`orientation` defines the split orientation (horizontal or vertical)

### \[signal\] void MainWindow::unhandledShortcutOverride(QEvent \**e*) {#unhandledShortcutOverride}

This signal is emitted for every unhandled ShortcutOverride in the window

`e` is the responsible event

### \[signal\] void MainWindow::viewChanged(KTextEditor::View \**view*) {#viewChanged}

This signal is emitted whenever the active view changes.

`view` is the new active view

### \[signal\] void MainWindow::viewCreated(KTextEditor::View \**view*) {#viewCreated}

This signal is emitted whenever a new view is created

`view` is the view that was created

### QList\<KTextEditor::View \*\> MainWindow::views() {#views}

Get a list of all views for this main window.

It is beneficial if the list is sorted by most recently used, as the library will e.g. try to use the most recent used url() by walking over this list for save and other such things.

Returns all views, might be empty!

### bool MainWindow::viewsInSameSplitView(KTextEditor::View \**view1*, KTextEditor::View \**view2*) {#viewsInSameSplitView}

Returns `true` if the given views `view1` and `view2` share the same split view, false otherwise.

### \[signal, since 6.0\] void MainWindow::widgetAdded(QWidget \**widget*) {#widgetAdded}

Emitted when a widget was added to this window.

`widget` is the widget that was added

This function was introduced in Qt 6.0.

### \[signal, since 6.0\] void MainWindow::widgetRemoved(QWidget \**widget*) {#widgetRemoved}

Emitted when a widget was added to this window.

`widget` is the widget that was removed

This function was introduced in Qt 6.0.

### \[since 6.0\] QWidgetList MainWindow::widgets() {#widgets}

returns the list of non-[KTextEditor::View](ktexteditor-view.md) widgets in this main window.

This function was introduced in Qt 6.0.

*See also* [addWidget](ktexteditor-mainwindow.md#addWidget)

### QWidget \*MainWindow::window() {#window}

Get the toplevel widget.

Returns the real main window widget, nullptr if not available
