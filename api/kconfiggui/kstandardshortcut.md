---
title: "KStandardShortcut Namespace"
description: "Convenient methods for access to the common accelerator keys in the key configuration."
---

# KStandardShortcut Namespace

Convenient methods for access to the common accelerator keys in the key configuration. [More...](#details)

- Header: KStandardShortcut
- CMake: find\_package(KF6 REQUIRED COMPONENTS Config) target\_link\_libraries(mytarget PRIVATE KF6::ConfigGui)

## Detailed Description {#details}

These are the standard keybindings that should be used in all KDE applications. They will be configurable, so do not hardcode the default behavior.

## Classes {#classes}

### class [StandardShortcutWatcher](kstandardshortcut-standardshortcutwatcher.md)

## Type Documentation {#type-documentation}

### enum KStandardShortcut::Category {#Category-enum}

Categories in which the standard shortcuts can be classified

| Constant |   |
| --- | --- |
| `KStandardShortcut::Category::InvalidCategory` | `-1` |
| `KStandardShortcut::Category::File` | `0` |
| `KStandardShortcut::Category::Edit` | `1` |
| `KStandardShortcut::Category::Navigation` | `2` |
| `KStandardShortcut::Category::View` | `3` |
| `KStandardShortcut::Category::Settings` | `4` |
| `KStandardShortcut::Category::Help` | `5` |

### enum KStandardShortcut::StandardShortcut {#StandardShortcut-enum}

Defines the identifier of all standard accelerators.

| Constant | Value |   |
| --- | --- | --- |
| `KStandardShortcut::AccelNone` | `0` |   |
| `KStandardShortcut::Open` | `1` | Open file. |
| `KStandardShortcut::New` | `2` | Create a new document. |
| `KStandardShortcut::Close` | `3` | Close current document. |
| `KStandardShortcut::Save` | `4` | Save current document. |
| `KStandardShortcut::Print` | `5` | Print current document. |
| `KStandardShortcut::Quit` | `6` | Quit the program. |
| `KStandardShortcut::Undo` | `7` | Undo last operation. |
| `KStandardShortcut::Redo` | `8` | Redo last operation. |
| `KStandardShortcut::Cut` | `9` | Cut selected area and store it in the clipboard. |
| `KStandardShortcut::Copy` | `10` | Copy selected area into the clipboard. |
| `KStandardShortcut::Paste` | `11` | Paste contents of clipboard at mouse/cursor position. |
| `KStandardShortcut::PasteSelection` | `12` | Paste the selection at mouse/cursor position. |
| `KStandardShortcut::SelectAll` | `13` | Select all. |
| `KStandardShortcut::Deselect` | `14` | Deselect any selected elements. |
| `KStandardShortcut::DeleteWordBack` | `15` | Delete a word back from mouse/cursor position. |
| `KStandardShortcut::DeleteWordForward` | `16` | Delete a word forward from mouse/cursor position. |
| `KStandardShortcut::Find` | `17` | Initiate a 'find' request in the current document. |
| `KStandardShortcut::FindNext` | `18` | Find the next instance of a stored 'find'. |
| `KStandardShortcut::FindPrev` | `19` | Find a previous instance of a stored 'find'. |
| `KStandardShortcut::Replace` | `20` | Find and replace matches. |
| `KStandardShortcut::Home` | `21` | Go to home page. |
| `KStandardShortcut::Begin` | `22` | Go to beginning of the document. |
| `KStandardShortcut::End` | `23` | Go to end of the document. |
| `KStandardShortcut::Prior` | `24` | Scroll up one page. |
| `KStandardShortcut::Next` | `25` | Scroll down one page. |
| `KStandardShortcut::Up` | `26` | Up. |
| `KStandardShortcut::Back` | `27` | Back. |
| `KStandardShortcut::Forward` | `28` | Forward. |
| `KStandardShortcut::Reload` | `29` | Reload. |
| `KStandardShortcut::BeginningOfLine` | `30` | Go to beginning of current line. |
| `KStandardShortcut::EndOfLine` | `31` | Go to end of current line. |
| `KStandardShortcut::GotoLine` | `32` | Go to line. |
| `KStandardShortcut::BackwardWord` | `33` | BackwardWord. |
| `KStandardShortcut::ForwardWord` | `34` | ForwardWord. |
| `KStandardShortcut::AddBookmark` | `35` | Add current page to bookmarks. |
| `KStandardShortcut::ZoomIn` | `36` | Zoom in. |
| `KStandardShortcut::ZoomOut` | `37` | Zoom out. |
| `KStandardShortcut::FullScreen` | `38` | Full Screen mode. |
| `KStandardShortcut::ShowMenubar` | `39` | Show Menu Bar. |
| `KStandardShortcut::TabNext` | `40` | Next Tab. |
| `KStandardShortcut::TabPrev` | `41` | Previous Tab. |
| `KStandardShortcut::Help` | `42` | Help the user in the current situation. |
| `KStandardShortcut::WhatsThis` | `43` | What's This button. |
| `KStandardShortcut::TextCompletion` | `44` | Complete text in input widgets. |
| `KStandardShortcut::PrevCompletion` | `45` | Iterate through a list when completion returns multiple items. |
| `KStandardShortcut::NextCompletion` | `46` | Iterate through a list when completion returns multiple items. |
| `KStandardShortcut::SubstringCompletion` | `47` | Find a string within another string or list of strings. |
| `KStandardShortcut::RotateUp` | `48` | Help users iterate through a list of entries. |
| `KStandardShortcut::RotateDown` | `49` | Help users iterate through a list of entries. |
| `KStandardShortcut::OpenRecent` | `50` | Open a recently used document. |
| `KStandardShortcut::SaveAs` | `51` | Save the current document under a different name. |
| `KStandardShortcut::Revert` | `52` | Revert the current document to the last saved version. |
| `KStandardShortcut::PrintPreview` | `53` | Show a print preview of the current document. |
| `KStandardShortcut::Mail` | `54` | Send the current document by mail. |
| `KStandardShortcut::Clear` | `55` | Clear the content of the focus widget. |
| `KStandardShortcut::ActualSize` | `56` | View the document at its actual size. |
| `KStandardShortcut::FitToPage` | `57` | Fit the document view to the size of the current window. |
| `KStandardShortcut::FitToWidth` | `58` | Fit the document view to the width of the current window. |
| `KStandardShortcut::FitToHeight` | `59` | Fit the document view to the height of the current window. |
| `KStandardShortcut::Zoom` | `60` | Select the current zoom level. |
| `KStandardShortcut::Goto` | `61` | Jump to some specific location in the document. |
| `KStandardShortcut::GotoPage` | `62` | Go to a specific page. |
| `KStandardShortcut::DocumentBack` | `63` | Move back (document style menu). |
| `KStandardShortcut::DocumentForward` | `64` | Move forward (document style menu). |
| `KStandardShortcut::EditBookmarks` | `65` | Edit the application bookmarks. |
| `KStandardShortcut::Spelling` | `66` | Pop up the spell checker. |
| `KStandardShortcut::ShowToolbar` | `67` | Show/Hide the toolbar. |
| `KStandardShortcut::ShowStatusbar` | `68` | Show/Hide the statusbar. |
| `KStandardShortcut::KeyBindings` | `69` | Display the configure key bindings dialog. |
| `KStandardShortcut::Preferences` | `70` | Display the preferences/options dialog. |
| `KStandardShortcut::ConfigureToolbars` | `71` | Display the toolbar configuration dialog. |
| `KStandardShortcut::ConfigureNotifications` | `72` | Display the notifications configuration dialog. |
| `KStandardShortcut::ReportBug` | `73` | Display the Report Bug dialog. |
| `KStandardShortcut::SwitchApplicationLanguage` | `74` | Display the Switch Application Language dialog. |
| `KStandardShortcut::AboutApp` | `75` | Display the application's About dialog. |
| `KStandardShortcut::AboutKDE` | `76` | Display the About KDE dialog. |
| `KStandardShortcut::DeleteFile (since Qt 5.25)` | `77` | Permanently delete files or folders. |
| `KStandardShortcut::RenameFile (since Qt 5.25)` | `78` | Rename files or folders. |
| `KStandardShortcut::MoveToTrash (since Qt 5.25)` | `79` | Move files or folders to the trash. |
| `KStandardShortcut::Donate (since Qt 5.26)` | `80` | Open donation page on kde.org. |
| `KStandardShortcut::ShowHideHiddenFiles (since Qt 5.70)` | `81` | Toggle showing or hiding hidden files |
| `KStandardShortcut::CreateFolder (since Qt 5.74)` | `82` | Create a folder. |
| `KStandardShortcut::OpenMainMenu (since Qt 6.0)` | `83` | Open a main menu like the menu bar or a hamburger menu. Necessary for accessibility. \* |
| `KStandardShortcut::OpenContextMenu (since Qt 6.0)` | `84` | Open a context menu for the object with keyboard focus. Necessary for accessibility. |

## Function Documentation {#function-documentation}

### const QList\<QKeySequence\> &KStandardShortcut::addBookmark() {#addBookmark}

Add current page to bookmarks. Default: Ctrl+B

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::back() {#back}

Back. Default: Alt+Left

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::backwardWord() {#backwardWord}

[BackwardWord](kstandardshortcut.md#StandardShortcut-enum). Default: Ctrl+Left

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::begin() {#begin}

Go to beginning of the document. Default: Ctrl-Home

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::beginningOfLine() {#beginningOfLine}

Go to beginning of current line. Default: Home

Returns the shortcut of the standard accelerator

### KStandardShortcut::Category KStandardShortcut::category(KStandardShortcut::StandardShortcut *id*) {#category}

Returns the appropriate category for the given [StandardShortcut](kstandardshortcut.md#StandardShortcut-enum) `id`.

### const QList\<QKeySequence\> &KStandardShortcut::close() {#close}

Close current document. Default: Ctrl-w

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::completion() {#completion}

Complete text in input widgets. Default Ctrl+E

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::copy() {#copy}

Copy selected area into the clipboard. Default: Ctrl-c

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::createFolder() {#createFolder}

Create a folder. Default: Ctrl+Shift+N

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::cut() {#cut}

Cut selected area and store it in the clipboard. Default: Ctrl-x

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::deleteFile() {#deleteFile}

Permanently delete files or folders. Default: Shift+Delete

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::deleteWordBack() {#deleteWordBack}

Delete a word back from mouse/cursor position. Default: Ctrl-Backspace

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::deleteWordForward() {#deleteWordForward}

Delete a word forward from mouse/cursor position. Default: Ctrl-Delete

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::end() {#end}

Go to end of the document. Default: Ctrl-End

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::endOfLine() {#endOfLine}

Go to end of current line. Default: End

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::find() {#find}

Initiate a 'find' request in the current document. Default: Ctrl-f

Returns the shortcut of the standard accelerator

### KStandardShortcut::StandardShortcut KStandardShortcut::find(const QKeySequence &*keySeq*) {#find-1}

Return the [StandardShortcut](kstandardshortcut.md#StandardShortcut-enum) id of the standard accel action which uses this key sequence, or [AccelNone](kstandardshortcut.md#StandardShortcut-enum) if none of them do.

This is used by class KKeyChooser.

`keySeq` the key sequence to search

### KStandardShortcut::StandardShortcut KStandardShortcut::findByName(const QString &*name*) {#findByName}

Return the [StandardShortcut](kstandardshortcut.md#StandardShortcut-enum) id of the standard accelerator action which has `name` as its name, or [AccelNone](kstandardshortcut.md#StandardShortcut-enum) if none of them do.

`name` the name as returned by name([StandardShortcut](kstandardshortcut.md#StandardShortcut-enum) id)

### const QList\<QKeySequence\> &KStandardShortcut::findNext() {#findNext}

Find the next instance of a stored 'find' Default: F3

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::findPrev() {#findPrev}

Find a previous instance of a stored 'find'. Default: Shift-F3

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::forward() {#forward}

Forward. Default: ALT+Right

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::forwardWord() {#forwardWord}

[ForwardWord](kstandardshortcut.md#StandardShortcut-enum). Default: Ctrl+Right

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::fullScreen() {#fullScreen}

Full Screen Mode. Default: Ctrl+Shift+F

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::gotoLine() {#gotoLine}

Go to line. Default: Ctrl+G

Returns the shortcut of the standard accelerator

### QList\<QKeySequence\> KStandardShortcut::hardcodedDefaultShortcut(KStandardShortcut::StandardShortcut *id*) {#hardcodedDefaultShortcut}

Returns the hardcoded default shortcut for `id`.

This does not take into account the user's configuration.

`id` the id of the accelerator

### const QList\<QKeySequence\> &KStandardShortcut::help() {#help}

Help the user in the current situation. Default: F1

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::home() {#home}

Go to home page. Default: Alt-Home

Returns the shortcut of the standard accelerator

### QString KStandardShortcut::label(KStandardShortcut::StandardShortcut *id*) {#label}

Returns a localized label for user-visible display.

`id` the id of the accelerator

### const QList\<QKeySequence\> &KStandardShortcut::moveToTrash() {#moveToTrash}

Moves files or folders to the trash. Default: Delete

Returns the shortcut of the standard accelerator

### QString KStandardShortcut::name(KStandardShortcut::StandardShortcut *id*) {#name}

Returns a unique name for the given accel.

`id` the id of the accelerator

### const QList\<QKeySequence\> &KStandardShortcut::next() {#next}

Scroll down one page. Default: Next

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::nextCompletion() {#nextCompletion}

Iterate through a list when completion returns multiple items. Default: Ctrl+Down

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::open() {#open}

Open file. Default: Ctrl-o

Returns the shortcut of the standard accelerator

### \[since 6.0\] const QList\<QKeySequence\> &KStandardShortcut::openContextMenu() {#openContextMenu}

Open a context menu for the object with keyboard focus. Necessary for accessibility. Default: Menu, Shift+F10

Returns the shortcut of the standard accelerator

This function was introduced in Qt 6.0.

### \[since 6.0\] const QList\<QKeySequence\> &KStandardShortcut::openMainMenu() {#openMainMenu}

Open a main menu like the menu bar or a hamburger menu. Necessary for accessibility. Default: F10

Returns the shortcut of the standard accelerator

This function was introduced in Qt 6.0.

### const QList\<QKeySequence\> &KStandardShortcut::openNew() {#openNew}

Create a new document (or whatever). Default: Ctrl-n

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::paste() {#paste}

Paste contents of clipboard at mouse/cursor position. Default: Ctrl-v

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::pasteSelection() {#pasteSelection}

Paste the selection at mouse/cursor position. Default: Ctrl-Shift-Insert

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::preferences() {#preferences}

Opens the app's settings window. Default: Ctrl+Shift+Comma

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::prevCompletion() {#prevCompletion}

Iterate through a list when completion returns multiple items. Default: Ctrl+Up

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::print() {#print}

Print current document. Default: Ctrl-p

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::prior() {#prior}

Scroll up one page. Default: Prior

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::quit() {#quit}

Quit the program. Default: Ctrl-q

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::redo() {#redo}

Redo last operation. Default: Shift-Ctrl-z

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::reload() {#reload}

Reload. Default: F5

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::renameFile() {#renameFile}

Rename files or folders. Default: F2

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::replace() {#replace}

Find and replace matches. Default: Ctrl-r

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::rotateDown() {#rotateDown}

Help users iterate through a list of entries. Default: Down

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::rotateUp() {#rotateUp}

Help users iterate through a list of entries. Default: Up

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::save() {#save}

Save current document. Default: Ctrl-s

Returns the shortcut of the standard accelerator

### void KStandardShortcut::saveShortcut(KStandardShortcut::StandardShortcut *id*, const QList\<QKeySequence\> &*newShortcut*) {#saveShortcut}

Saves the new shortcut `cut` for standard accel `id`.

### const QList\<QKeySequence\> &KStandardShortcut::selectAll() {#selectAll}

Select all. Default: Ctrl-A

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::shortcut(KStandardShortcut::StandardShortcut *id*) {#shortcut}

Returns the keybinding for `accel`.

On X11, if QApplication was initialized with GUI disabled, the default keybinding will always be returned.

`id` the id of the accelerator

### KStandardShortcut::StandardShortcutWatcher \*shortcutWatcher() {#shortcutWatcher}

Returns the global KStandardShortcutWatcher instance of this program. In addition to the notifying about changes it also keeps the information returned by the functions in [KStandardShortcut](kstandardshortcut.md) up to date. The object is created by the first call to this function.

### const QList\<QKeySequence\> &KStandardShortcut::showHideHiddenFiles() {#showHideHiddenFiles}

Shows or hides hidden files. Defaults: Ctrl+H, Alt+.

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::showMenubar() {#showMenubar}

Show Menu Bar. Default: Ctrl-M

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::substringCompletion() {#substringCompletion}

Find a string within another string or list of strings. Default: Ctrl-T

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::tabNext() {#tabNext}

Next Tab. Defaults: Ctrl+PgDown, Ctrl+\]

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::tabPrev() {#tabPrev}

Previous Tab. Defaults: Ctrl+PgUp, Ctrl+\[

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::undo() {#undo}

Undo last operation. Default: Ctrl-z

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::up() {#up}

Up. Default: Alt+Up

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::whatsThis() {#whatsThis}

What's This button. Default: Shift+F1

Returns the shortcut of the standard accelerator

### QString KStandardShortcut::whatsThis(KStandardShortcut::StandardShortcut *id*) {#whatsThis-1}

Returns an extended [WhatsThis](kstandardshortcut.md#StandardShortcut-enum) description for the given accelerator.

`id` the id of the accelerator

### const QList\<QKeySequence\> &KStandardShortcut::zoomIn() {#zoomIn}

Zoom in. Default: Ctrl-Plus

Returns the shortcut of the standard accelerator

### const QList\<QKeySequence\> &KStandardShortcut::zoomOut() {#zoomOut}

Zoom out. Default: Ctrl-Minus

Returns the shortcut of the standard accelerator
