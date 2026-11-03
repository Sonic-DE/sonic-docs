---
title: "KStandardActions Namespace"
description: "Convenience methods to access all standard KDE actions. This namespace was introduced in Qt 6.3."
---

# KStandardActions Namespace

Convenience methods to access all standard KDE actions. This namespace was introduced in Qt 6.3.

- Header: KStandardActions
- Since: Qt 6.3
- CMake: find\_package(KF6 REQUIRED COMPONENTS Config) target\_link\_libraries(mytarget PRIVATE KF6::ConfigGui)

## Detailed Description {#details}

These actions should be used instead of hardcoding menubar and toolbar items. Using these actions helps your application easily conform to the [KDE Human Interface Guidelines](https://develop.kde.org/hig/).

All of the documentation for [QAction](https://doc.qt.io/qt-6/qaction.html) holds for [KStandardActions](kstandardactions.md) also. When in doubt on how things work, check the [QAction](https://doc.qt.io/qt-6/qaction.html) documentation first. Please note that calling any of these methods automatically adds the action to the actionCollection() of the [QObject](https://doc.qt.io/qt-6/qobject.html) given by the 'parent' parameter.

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
QAction *newAct = KStandardActions::openNew(this, &ClassFoo::fileNew, this);
```

Alternatively you can instantiate the action using the [StandardAction](kstandardactions.md#StandardAction-enum) enums provided. This author can't think of a reason why you would want to, but, hey, if you do, here's how:

```cpp
QAction *newAct = KStandardActions::create(KStandardActions::New, this, &ClassFoo::fileNew, this);
```

Relationship with KActionCollection from KXMLGui

If a KActionCollection is passed as the parent then the action will be automatically added to that collection:

```cpp
QAction *cut = KStandardActions::cut(this, &ClassFoo::editCut, actionCollection());
```

Each action has a unique internal name which can be queried using the name method. For example [KStandardActions::name](kstandardactions.md#name)([KStandardActions::Cut](kstandardactions.md#StandardAction-enum)) would return 'edit\_cut'. This name can be used as a unique identifier for the actions. So if you wanted to add an existing standard action to an action collection you can do so like this:

```cpp
QAction *cut = KStandardActions::cut(this, &ClassFoo::editCut, this);
actionCollection()->addAction(KStandardActions::name(KStandardActions::Cut), cut);
```

You can then get a pointer to the action using

```cpp
QAction *cutPtr = actionCollection()->action(KStandardActions::name(KStandardActions::Cut));
```

## Type Documentation {#type-documentation}

### enum KStandardActions::StandardAction {#StandardAction-enum}

The standard menubar and toolbar actions.

| Constant | Value | Description |
| --- | --- | --- |
| `KStandardActions::New` | `1` | Create a new document or window. |
| `KStandardActions::Open` | `2` | Open an existing file. |
| `KStandardActions::OpenRecent` | `3` | Open a recently used document. |
| `KStandardActions::Save` | `4` | Save the current document. |
| `KStandardActions::SaveAs` | `5` | Save the current document under a different name. |
| `KStandardActions::Revert` | `6` | Revert the current document to the last saved version. |
| `KStandardActions::Close` | `7` | Close the current document. |
| `KStandardActions::Print` | `8` | Print the current document. |
| `KStandardActions::PrintPreview` | `9` | Show a print preview of the current document. |
| `KStandardActions::Mail` | `10` | Send the current document by mail. |
| `KStandardActions::Quit` | `11` | Quit the program. |
| `KStandardActions::Undo` | `12` | Undo the last operation. |
| `KStandardActions::Redo` | `13` | Redo the last operation. |
| `KStandardActions::Cut` | `14` | Cut selected area and store it in the clipboard. |
| `KStandardActions::Copy` | `15` | Copy selected area and store it in the clipboard. |
| `KStandardActions::Paste` | `16` | Paste the contents of clipboard at the current mouse or cursor. |
| `KStandardActions::SelectAll` | `17` | Select all elements in the current document. |
| `KStandardActions::Deselect` | `18` | Deselect any selected elements in the current document. |
| `KStandardActions::Find` | `19` | Initiate a 'find' request in the current document. |
| `KStandardActions::FindNext` | `20` | Find the next instance of a stored 'find' |
| `KStandardActions::FindPrev` | `21` | Find a previous instance of a stored 'find'. |
| `KStandardActions::Replace` | `22` | Find and replace matches. |
| `KStandardActions::ActualSize` | `23` | View the document at its actual size. |
| `KStandardActions::FitToPage` | `24` | Fit the document view to the size of the current window. |
| `KStandardActions::FitToWidth` | `25` | Fit the document view to the width of the current window. |
| `KStandardActions::FitToHeight` | `26` | Fit the document view to the height of the current window. |
| `KStandardActions::ZoomIn` | `27` | Zoom in the current document. |
| `KStandardActions::ZoomOut` | `28` | Zoom out the current document. |
| `KStandardActions::Zoom` | `29` | Select the current zoom level. |
| `KStandardActions::Redisplay` | `30` | Redisplay or redraw the document. |
| `KStandardActions::Up` | `31` | Move up (web style menu). |
| `KStandardActions::Back` | `32` | Move back (web style menu). |
| `KStandardActions::Forward` | `33` | Move forward (web style menu). |
| `KStandardActions::Home` | `34` | Go to the "Home" position or document. |
| `KStandardActions::Prior` | `35` | Scroll up one page. |
| `KStandardActions::Next` | `36` | Scroll down one page. |
| `KStandardActions::Goto` | `37` | Jump to some specific location in the document. |
| `KStandardActions::GotoPage` | `38` | Go to a specific page. |
| `KStandardActions::GotoLine` | `39` | Go to a specific line. |
| `KStandardActions::FirstPage` | `40` | Jump to the first page. |
| `KStandardActions::LastPage` | `41` | Jump to the last page. |
| `KStandardActions::DocumentBack` | `42` | Move back (document style menu). |
| `KStandardActions::DocumentForward` | `43` | Move forward (document style menu). |
| `KStandardActions::AddBookmark` | `44` | Add the current page to the bookmarks tree. |
| `KStandardActions::EditBookmarks` | `45` | Edit the application bookmarks. |
| `KStandardActions::Spelling` | `46` | Pop up the spell checker. |
| `KStandardActions::ShowMenubar` | `47` | Show/Hide the menubar. |
| `KStandardActions::ShowToolbar` | `48` | Show/Hide the toolbar. |
| `KStandardActions::ShowStatusbar` | `49` | Show/Hide the statusbar. |
| `KStandardActions::KeyBindings` | `50` | Display the configure key bindings dialog. |
| `KStandardActions::Preferences` | `51` | Display the preferences/options dialog. |
| `KStandardActions::ConfigureToolbars` | `52` | Display the toolbar configuration dialog. |
| `KStandardActions::HelpContents` | `53` | Display the handbook of the application. |
| `KStandardActions::WhatsThis` | `54` | Trigger the What's This cursor. |
| `KStandardActions::ReportBug` | `55` | Open up the Report Bug dialog. |
| `KStandardActions::AboutApp` | `56` | Display the application's About box. |
| `KStandardActions::AboutKDE` | `57` | Display the About KDE dialog. |
| `KStandardActions::ConfigureNotifications` | `58` | Display the notifications configuration dialog. |
| `KStandardActions::FullScreen` | `59` | Switch to/from full screen mode. |
| `KStandardActions::Clear` | `60` | Clear the content of the focus widget. |
| `KStandardActions::SwitchApplicationLanguage` | `61` | Display the Switch Application Language dialog. |
| `KStandardActions::DeleteFile` | `62` | Permanently deletes files or folders. |
| `KStandardActions::RenameFile` | `63` | Renames files or folders. |
| `KStandardActions::MoveToTrash` | `64` | Moves files or folders to the trash. |
| `KStandardActions::Donate` | `65` | Open donation page on kde.org. |
| `KStandardActions::HamburgerMenu` | `66` | Opens a menu that substitutes the menubar. |

## Function Documentation {#function-documentation}

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::aboutApp(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#aboutApp}

Display the application's About box.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::aboutKDE(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#aboutKDE}

Display the About KDE dialog.

### QList\<KStandardActions::StandardAction\> KStandardActions::actionIds() {#actionIds}

Returns a list of all actionIds.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::actualSize(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#actualSize}

View the document at its actual size.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::addBookmark(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#addBookmark}

Add the current page to the bookmarks tree.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::back(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#back}

Move back (web style menu).

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::clear(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#clear}

Clear the content of the focus widget

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::close(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#close}

Close the current document.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::configureNotifications(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#configureNotifications}

Display the notifications configuration dialog.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::configureToolbars(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#configureToolbars}

Display the toolbar configuration dialog.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::copy(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#copy}

Copy the selected area into the clipboard.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::create(KStandardActions::StandardAction *id*, const Receiver \**recvr*, Func *slot*, QObject \**parent*, std::optional\<Qt::ConnectionType\> *connectionType* = std::nullopt) {#create}

Creates an action corresponding to one of the [KStandardActions::StandardAction](kstandardactions.md#StandardAction-enum) actions, which is connected to the given object and `slot`, and is owned by `parent`.

If not explicitly specified, `connectionType` will be AutoConnection for all actions except for [ConfigureToolbars](kstandardactions.md#StandardAction-enum) it will be QueuedConnection.

*See also* create(StandardAction, const QObject \*, const char \*, QObject \*)

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::cut(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#cut}

Cut selected area and store it in the clipboard.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::deleteFile(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#deleteFile}

Permanently deletes files or folders.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::deselect(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#deselect}

Deselect any selected elements in the current document.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::documentBack(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#documentBack}

Move back (document style menu).

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::documentForward(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#documentForward}

Move forward (document style menu).

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::donate(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#donate}

Open donation page on kde.org.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::editBookmarks(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#editBookmarks}

Edit the application bookmarks.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::find(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#find}

Initiate a 'find' request in the current document.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::findNext(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#findNext}

Find the next instance of a stored 'find'.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::findPrev(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#findPrev}

Find a previous instance of a stored 'find'.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::firstPage(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#firstPage}

Jump to the first page.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::fitToHeight(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#fitToHeight}

Fit the document view to the height of the current window.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::fitToPage(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#fitToPage}

Fit the document view to the size of the current window.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::fitToWidth(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#fitToWidth}

Fit the document view to the width of the current window.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::forward(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#forward}

Move forward (web style menu).

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::goTo(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#goTo}

Jump to some specific location in the document.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::gotoLine(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#gotoLine}

Go to a specific line.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::gotoPage(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#gotoPage}

Go to a specific page.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::helpContents(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#helpContents}

Display the handbook of the application.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::home(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#home}

Go to the "Home" position or document.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::keyBindings(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#keyBindings}

Display the configure key bindings dialog.

Note that you might be able to use the pre-built KXMLGUIFactory's function:

```cpp
KStandardActions::keyBindings(guiFactory(), &KXMLGUIFactory::showConfigureShortcutsDialog, actionCollection());
```

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::lastPage(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#lastPage}

Jump to the last page.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::mail(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#mail}

Mail this document.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::moveToTrash(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#moveToTrash}

Moves files or folders to the trash.

### QString KStandardActions::name(KStandardActions::StandardAction *id*) {#name}

This will return the internal name of a given standard action.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::next(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#next}

Scroll down one page.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::open(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#open}

Open an existing file.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::openNew(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#openNew}

Create a new document or window.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::paste(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#paste}

Paste the contents of clipboard at the current mouse or cursor position.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::preferences(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#preferences}

Display the preferences/options dialog.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::print(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#print}

Print the current document.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::printPreview(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#printPreview}

Show a print preview of the current document.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::prior(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#prior}

Scroll up one page.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::quit(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#quit}

Quit the program.

Note that you probably want to connect this action to either QWidget::close() or QApplication::closeAllWindows(), but not QApplication::quit(), so that KMainWindow::queryClose() is called on any open window (to warn the user about unsaved changes for example).

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::redisplay(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#redisplay}

Redisplay or redraw the document.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::redo(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#redo}

Redo the last operation.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::renameFile(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#renameFile}

Renames files or folders.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::replace(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#replace}

Find and replace matches.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::reportBug(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#reportBug}

Open up the Report Bug dialog.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::revert(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#revert}

Revert the current document to the last saved version (essentially will undo all changes).

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::save(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#save}

Save the current document.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::saveAs(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#saveAs}

Save the current document under a different name.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::selectAll(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#selectAll}

Select all elements in the current document.

### KStandardShortcut::StandardShortcut KStandardActions::shortcutForActionId(KStandardActions::StandardAction *id*) {#shortcutForActionId}

Returns the standardshortcut associated with `actionId`.

`id` The identifier whose associated shortcut is wanted.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::spelling(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#spelling}

Pop up the spell checker.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::switchApplicationLanguage(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#switchApplicationLanguage}

Display the Switch Application Language dialog.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::undo(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#undo}

Undo the last operation.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::up(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#up}

Move up (web style menu).

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::whatsThis(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#whatsThis}

Trigger the What's This cursor.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::zoom(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#zoom}

Select the current zoom level.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::zoomIn(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#zoomIn}

Zoom in the current document view.

### template \<typename Receiver, typename Func\> QAction \*KStandardActions::zoomOut(const Receiver \**recvr*, Func *slot*, QObject \**parent*) {#zoomOut}

Zoom out the current document view.
