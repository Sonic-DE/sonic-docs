---
title: "KStandardAction Namespace"
description: "Convenience methods to access all standard KDE actions."
---

# KStandardAction Namespace

Convenience methods to access all standard KDE actions. [More...](#details)

- **Header:** `#include <KStandardAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`

## Detailed Description {#details}

These actions should be used instead of hardcoding menubar and toolbar items. Using these actions helps your application easily conform to the [KDE Human Interface Guidelines](https://develop.kde.org/hig/).

All of the documentation for [QAction](https://doc.qt.io/qt-6/qaction.html) holds for [KStandardAction](kstandardaction.md) also. When in doubt on how things work, check the [QAction](https://doc.qt.io/qt-6/qaction.html) documentation first. Please note that calling any of these methods automatically adds the action to the actionCollection() of the [QObject](https://doc.qt.io/qt-6/qobject.html) given by the 'parent' parameter.

Simple Example:

In general, using standard actions should be a drop in replacement for regular actions. For example, if you previously had:

```cpp
QAction *newAct = new QAction(QIcon::fromTheme("document-new"),
                              i18n("&New"),
                              this);
newAct->setShortcut(KStandardShortcut::shortcut(KStandardShortcut::New).constFirst());
connect(newAct, &QAction::triggered, this, &ClassFoo::fileNew);
```

You can replace it with:

```cpp
QAction *newAct = KStandardAction::openNew(this, &ClassFoo::fileNew, this);
```

Alternatively you can instantiate the action using the [StandardAction](kstandardaction.md#StandardAction-enum) enums provided. This author can't think of a reason why you would want to, but, hey, if you do, here's how:

```cpp
QAction *newAct = KStandardAction::create(KStandardAction::New, this, &ClassFoo::fileNew, this);
```

Relationship with KActionCollection from KXMLGui

If a KActionCollection is passed as the parent then the action will be automatically added to that collection:

```cpp
QAction *cut = KStandardAction::cut(this, &ClassFoo::editCut, actionCollection());
```

Each action has a unique internal name which can be queried using the name method. For example [KStandardAction::name](kstandardaction.md#name)([KStandardAction::Cut](kstandardaction.md#StandardAction-enum)) would return 'edit\_cut'. This name can be used as a unique identifier for the actions. So if you wanted to add an existing standard action to an action collection you can do so like this:

```cpp
QAction *cut = KStandardAction::cut(this, &ClassFoo::editCut, this);
actionCollection()->addAction(KStandardAction::name(KStandardAction::Cut), cut);
```

You can then get a pointer to the action using

```cpp
QAction *cutPtr = actionCollection()->action(KStandardAction::name(KStandardAction::Cut));
```

## Type Documentation {#type-documentation}

### enum KStandardAction::StandardAction {#StandardAction-enum}

The standard menubar and toolbar actions.

## Function Documentation {#function-documentation}

### QAction \*KStandardAction::aboutApp(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#aboutApp}

Display the application's About box.

### QAction \*KStandardAction::aboutKDE(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#aboutKDE}

Display the About KDE dialog.

### QList\<KStandardAction::StandardAction\> KStandardAction::actionIds() {#actionIds}

Returns a list of all actionIds.

### QAction \*KStandardAction::actualSize(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#actualSize}

View the document at its actual size.

### QAction \*KStandardAction::addBookmark(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#addBookmark}

Add the current page to the bookmarks tree.

### QAction \*KStandardAction::back(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#back}

Move back (web style menu).

### QAction \*KStandardAction::clear(QObject \**parent*) {#clear}

Clear selected area. Calls clear() on the widget with the current focus. Note that for some widgets, this may not provide the intended behavior. For example if you make use of the code above and a K3ListView has the focus, clear() will clear all of the items in the list. If this is not the intended behavior and you want to make use of this slot, you can subclass K3ListView and reimplement this slot. For example the following code would implement a K3ListView without this behavior:

```cpp
class MyListView : public K3ListView {
  Q_OBJECT
public:
  MyListView( QWidget * parent = 0, const char * name = 0, WFlags f = 0 ) : K3ListView( parent, name, f ) {}
  virtual ~MyListView() {}
public Q_SLOTS:
  virtual void clear() {}
};
```

### QAction \*KStandardAction::clear(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#clear-1}

Clear the content of the focus widget

### QAction \*KStandardAction::close(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#close}

Close the current document.

### QAction \*KStandardAction::configureNotifications(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#configureNotifications}

Display the notifications configuration dialog.

### QAction \*KStandardAction::configureToolbars(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#configureToolbars}

Display the toolbar configuration dialog.

### QAction \*KStandardAction::copy(QObject \**parent*) {#copy}

Copy selected area and store it in the clipboard. Calls copy() on the widget with the current focus.

### QAction \*KStandardAction::copy(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#copy-1}

Copy the selected area into the clipboard.

### QAction \*KStandardAction::create(KStandardAction::StandardAction *id*, const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#create}

Creates an action corresponding to one of the [KStandardAction::StandardAction](kstandardaction.md#StandardAction-enum) actions, which is connected to the given object and `slot`, and is owned by `parent`.

The signal that is connected to `slot` is triggered(bool), except for the case of [OpenRecent](kstandardaction.md#StandardAction-enum) standard action, which uses the urlSelected(const [QUrl](https://doc.qt.io/qt-6/qurl.html) &) signal of [KRecentFilesAction](krecentfilesaction.md).

`id` The [StandardAction](kstandardaction.md#StandardAction-enum) identifier to create a [QAction](https://doc.qt.io/qt-6/qaction.html) for.

`recvr` The [QObject](https://doc.qt.io/qt-6/qobject.html) to receive the signal, or `nullptr` if no notification is needed.

`slot` The slot to connect the signal to (remember to use the SLOT() macro).

`parent` The [QObject](https://doc.qt.io/qt-6/qobject.html) that should own the created [QAction](https://doc.qt.io/qt-6/qaction.html), or `nullptr` if no parent will own the [QAction](https://doc.qt.io/qt-6/qaction.html) returned (ensure you delete it manually in this case).

### \[since 5.23 (The connectionType argument was added in 5.95)\] template \<typename Receiver, typename Func\> typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, QAction\>::type \*KStandardAction::create(KStandardAction::StandardAction *id*, const Receiver \**recvr*, Func *slot*, QObject \**parent*, std::optional\<Qt::ConnectionType\> *connectionType* = std::nullopt) {#create-1}

This overloads [create](kstandardaction.md#create)() to allow using the new connect syntax

> **Note:** if you use `OpenRecent` as `id`, you should manually connect to the urlSelected(const [QUrl](https://doc.qt.io/qt-6/qurl.html) &) signal of the returned [KRecentFilesAction](krecentfilesaction.md) instead or use [KStandardAction::openRecent](kstandardaction.md#openRecent)(Receiver \*, Func).

If not explicitly specified, `connectionType` will be AutoConnection for all actions except for [ConfigureToolbars](kstandardaction.md#StandardAction-enum) it will be QueuedConnection.

`create(StandardAction, const QObject *, const char *, QObject *)`

This function was introduced in 5.23 (The connectionType argument was added in 5.95).

### QAction \*KStandardAction::cut(QObject \**parent*) {#cut}

Cut selected area and store it in the clipboard. Calls cut() on the widget with the current focus.

### QAction \*KStandardAction::cut(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#cut-1}

Cut selected area and store it in the clipboard.

### QAction \*KStandardAction::deleteFile(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#deleteFile}

Permanently deletes files or folders.

### QAction \*KStandardAction::deselect(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#deselect}

Deselect any selected elements in the current document.

### QAction \*KStandardAction::documentBack(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#documentBack}

Move back (document style menu).

### QAction \*KStandardAction::documentForward(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#documentForward}

Move forward (document style menu).

### QAction \*KStandardAction::donate(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#donate}

Open donation page on kde.org.

### QAction \*KStandardAction::editBookmarks(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#editBookmarks}

Edit the application bookmarks.

### QAction \*KStandardAction::find(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#find}

Initiate a 'find' request in the current document.

### QAction \*KStandardAction::findNext(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#findNext}

Find the next instance of a stored 'find'.

### QAction \*KStandardAction::findPrev(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#findPrev}

Find a previous instance of a stored 'find'.

### QAction \*KStandardAction::firstPage(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#firstPage}

Jump to the first page.

### QAction \*KStandardAction::fitToHeight(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#fitToHeight}

Fit the document view to the height of the current window.

### QAction \*KStandardAction::fitToPage(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#fitToPage}

Fit the document view to the size of the current window.

### QAction \*KStandardAction::fitToWidth(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#fitToWidth}

Fit the document view to the width of the current window.

### QAction \*KStandardAction::forward(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#forward}

Move forward (web style menu).

### KToggleFullScreenAction \*KStandardAction::fullScreen(const QObject \**recvr*, const char \**slot*, QWidget \**window*, QObject \**parent*) {#fullScreen}

Switch to/from full screen mode

### template \<typename Receiver, typename Func\> typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, KToggleFullScreenAction\>::type \*KStandardAction::fullScreen(const Receiver \**recvr*, Func *slot*, QWidget \**window*, QObject \**parent*) {#fullScreen-1}

Switch to/from full screen mode

### QAction \*KStandardAction::goTo(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#goTo}

Jump to some specific location in the document.

### QAction \*KStandardAction::gotoLine(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#gotoLine}

Go to a specific line.

### QAction \*KStandardAction::gotoPage(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#gotoPage}

Go to a specific page.

### KHamburgerMenu \*KStandardAction::hamburgerMenu(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#hamburgerMenu}

Opens a menu that substitutes the menubar.

### QAction \*KStandardAction::helpContents(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#helpContents}

Display the handbook of the application.

### QAction \*KStandardAction::home(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#home}

Go to the "Home" position or document.

### QAction \*KStandardAction::keyBindings(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#keyBindings}

Display the configure keyboard shortcuts dialog.

Note that you might be able to use the pre-built KXMLGUIFactory's function:

```cpp
KStandardAction::keyBindings(guiFactory(), &KXMLGUIFactory::showConfigureShortcutsDialog, actionCollection());
```

### QAction \*KStandardAction::lastPage(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#lastPage}

Jump to the last page.

### QAction \*KStandardAction::mail(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#mail}

Send the current document by mail.

### QAction \*KStandardAction::moveToTrash(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#moveToTrash}

Moves files or folders to the trash.

### QString KStandardAction::name(KStandardAction::StandardAction *id*) {#name}

This will return the internal name of a given standard action.

### QAction \*KStandardAction::next(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#next}

Scroll down one page.

### QAction \*KStandardAction::open(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#open}

Open an existing file.

### QAction \*KStandardAction::openNew(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#openNew}

Create a new document or window.

### KRecentFilesAction \*KStandardAction::openRecent(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#openRecent}

Open a recently used document. The signature of the slot being called is of the form slotURLSelected( const [QUrl](https://doc.qt.io/qt-6/qurl.html) & ). `recvr` object to receive slot `slot` The SLOT to invoke when a URL is selected. The slot's signature is slotURLSelected( const [QUrl](https://doc.qt.io/qt-6/qurl.html) & ). `parent` parent widget

### template \<typename Receiver, typename Func\> typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, KRecentFilesAction\>::type \*KStandardAction::openRecent(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#openRecent-1}

The same as [openRecent](kstandardaction.md#openRecent)(const [QObject](https://doc.qt.io/qt-6/qobject.html) \*, const char \*, [QObject](https://doc.qt.io/qt-6/qobject.html) \*), but using new-style connect syntax `openRecent(const QObject *, const char *, QObject *)`

### QAction \*KStandardAction::paste(QObject \**parent*) {#paste}

Paste the contents of clipboard at the current mouse or cursor Calls paste() on the widget with the current focus.

### QAction \*KStandardAction::paste(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#paste-1}

Paste the contents of clipboard at the current mouse or cursor position.

### QAction \*KStandardAction::preferences(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#preferences}

Display the preferences/options dialog.

### QAction \*KStandardAction::print(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#print}

Print the current document.

### QAction \*KStandardAction::printPreview(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#printPreview}

Show a print preview of the current document.

### QAction \*KStandardAction::prior(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#prior}

Scroll up one page.

### QAction \*KStandardAction::quit(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#quit}

Quit the program.

Note that you probably want to connect this action to either [QWidget::close](https://doc.qt.io/qt-6/qwidget.html#close)() or [QApplication::closeAllWindows](https://doc.qt.io/qt-6/qapplication.html#closeAllWindows)(), but not [QApplication::quit](https://doc.qt.io/qt-6/qcoreapplication.html#quit)(), so that KMainWindow::queryClose() is called on any open window (to warn the user about unsaved changes for example).

### QAction \*KStandardAction::redisplay(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#redisplay}

Redisplay or redraw the document.

### QAction \*KStandardAction::redo(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#redo}

Redo the last operation.

### QAction \*KStandardAction::renameFile(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#renameFile}

Renames files or folders.

### QAction \*KStandardAction::replace(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#replace}

Find and replace matches.

### QAction \*KStandardAction::reportBug(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#reportBug}

Open up the Report Bug dialog.

### QAction \*KStandardAction::revert(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#revert}

Revert the current document to the last saved version (essentially will undo all changes).

### QAction \*KStandardAction::save(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#save}

Save the current document.

### QAction \*KStandardAction::saveAs(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#saveAs}

Save the current document under a different name.

### QAction \*KStandardAction::selectAll(QObject \**parent*) {#selectAll}

Calls selectAll() on the widget with the current focus.

### QAction \*KStandardAction::selectAll(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#selectAll-1}

Select all elements in the current document.

### KStandardShortcut::StandardShortcut KStandardAction::shortcutForActionId(KStandardAction::StandardAction *id*) {#shortcutForActionId}

Returns the standardshortcut associated with @a actionId.

`id` The identifier whose associated shortcut is wanted.

### KToggleAction \*KStandardAction::showMenubar(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#showMenubar}

Show/Hide the menubar.

### template \<typename Receiver, typename Func\> typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, KToggleAction\>::type \*KStandardAction::showMenubar(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#showMenubar-1}

The same as [showMenubar](kstandardaction.md#showMenubar)(const [QObject](https://doc.qt.io/qt-6/qobject.html) \*, const char \*, [QObject](https://doc.qt.io/qt-6/qobject.html) \*), but using new-style connect syntax `showMenubar(const QObject *, const char *, QObject *)`

### KToggleAction \*KStandardAction::showStatusbar(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#showStatusbar}

Show/Hide the statusbar.

### template \<typename Receiver, typename Func\> typename std::enable\_if\<!std::is\_convertible\<Func, const char \*\>::value, KToggleAction\>::type \*KStandardAction::showStatusbar(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#showStatusbar-1}

Show/Hide the statusbar.

### QAction \*KStandardAction::spelling(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#spelling}

Pop up the spell checker.

### QStringList KStandardAction::stdNames() {#stdNames}

Returns a list of all standard names. Used by KAccelManager to give those higher weight.

### QAction \*KStandardAction::switchApplicationLanguage(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#switchApplicationLanguage}

Display the Switch Application Language dialog.

### QAction \*KStandardAction::undo(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#undo}

Undo the last operation.

### QAction \*KStandardAction::up(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#up}

Move up (web style menu).

### QAction \*KStandardAction::whatsThis(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#whatsThis}

Trigger the What's This cursor.

### QAction \*KStandardAction::zoom(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#zoom}

Select the current zoom level.

### QAction \*KStandardAction::zoomIn(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#zoomIn}

Zoom in the current document view.

### QAction \*KStandardAction::zoomOut(const QObject \**recvr*, const char \**slot*, QObject \**parent*) {#zoomOut}

Zoom out the current document view.
