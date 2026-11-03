---
title: "KTextEditor::View Class"
description: "A text widget with KXMLGUIClient that represents a Document. This class was introduced in Qt 6.23)."
---

# KTextEditor::View Class

A text widget with [KXMLGUIClient](../kxmlgui/kxmlguiclient.md) that represents a Document. This class was introduced in Qt 6.23). [More...](#details)

- **Header:** `#include <KTextEditor/View>`
- **Since:** Qt 6.23)
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html) and [KXMLGUIClient](../kxmlgui/kxmlguiclient.md)

[List of all members, including inherited members](ktexteditor-view-members.md)

## Public Types

- [\[since 6.20\] enum View::CoordinatesToCursorFlag](#CoordinatesToCursorFlag-enum)
- [enum View::InputMode](#InputMode-enum)
- [enum View::LineType](#LineType-enum)
- [enum View::ViewMode](#ViewMode-enum)

## Public Functions

- [~View()](#dtor.View)
- [void abortCompletion()](#abortCompletion)
- [KTextEditor::AbstractAnnotationItemDelegate \*annotationItemDelegate() const](#annotationItemDelegate) (since 6.0)
- [KTextEditor::AnnotationModel \*annotationModel() const](#annotationModel)
- [bool blockSelection() const](#blockSelection)
- [QList\<KTextEditor::CodeCompletionModel \*\> codeCompletionModels() const](#codeCompletionModels)
- [QStringList configKeys() const](#configKeys)
- [QVariant configValue(const QString &key)](#configValue)
- [QMenu \*contextMenu() const](#contextMenu)
- [KTextEditor::Cursor coordinatesToCursor(const QPoint &coord) const](#coordinatesToCursor)
- [KTextEditor::Cursor coordinatesToCursor(QPoint coords, KTextEditor::View::CoordinatesToCursorFlags flags) const](#coordinatesToCursor-1)
- [KTextEditor::Cursor cursorPosition() const](#cursorPosition)
- [QPoint cursorPositionCoordinates() const](#cursorPositionCoordinates)
- [KTextEditor::Cursor cursorPositionVirtual() const](#cursorPositionVirtual)
- [QList\<KTextEditor::Cursor\> cursorPositions() const](#cursorPositions)
- [QPoint cursorToCoordinate(KTextEditor::Cursor cursor) const](#cursorToCoordinate)
- [QMenu \*defaultContextMenu(QMenu \*menu = nullptr) const](#defaultContextMenu)
- [QExplicitlySharedDataPointer\<KTextEditor::Attribute\> defaultStyleAttribute(KSyntaxHighlighting::Theme::TextStyle defaultStyle) const](#defaultStyleAttribute)
- [KTextEditor::Document \*document() const](#document)
- [QWidget \*editorWidget() const](#editorWidget) (since 6.20)
- [bool evaluateScript(const QString &script, QVariant \*result = nullptr)](#evaluateScript) (since 6.15)
- [int firstDisplayedLine(KTextEditor::View::LineType lineType = RealLine) const](#firstDisplayedLine)
- [void forceCompletion()](#forceCompletion)
- [QScrollBar \*horizontalScrollBar() const](#horizontalScrollBar) (since 6.0)
- [bool insertTemplate(KTextEditor::Cursor insertPosition, const QString &templateString, const QString &script = QString())](#insertTemplate)
- [bool insertText(const QString &text)](#insertText)
- [bool isAnnotationBorderVisible() const](#isAnnotationBorderVisible)
- [bool isAutomaticInvocationEnabled() const](#isAutomaticInvocationEnabled)
- [bool isCompletionActive() const](#isCompletionActive)
- [bool isLineVisible(int realLine) const](#isLineVisible) (since 6.27)
- [bool isStatusBarEnabled() const](#isStatusBarEnabled)
- [int lastDisplayedLine(KTextEditor::View::LineType lineType = RealLine) const](#lastDisplayedLine)
- [QList\<KTextEditor::AttributeBlock\> lineAttributes(int line)](#lineAttributes)
- [KTextEditor::MainWindow \*mainWindow() const](#mainWindow)
- [KTextEditor::Cursor maxScrollPosition() const](#maxScrollPosition)
- [bool mouseTrackingEnabled() const](#mouseTrackingEnabled)
- [bool print()](#print)
- [void printPreview()](#printPreview)
- [void readSessionConfig(const KConfigGroup &config, const QSet\<QString\> &flags = QSet\<QString\>())](#readSessionConfig)
- [int realToVisibleLine(int realLine) const](#realToVisibleLine) (since 6.27)
- [void registerCompletionModel(KTextEditor::CodeCompletionModel \*model)](#registerCompletionModel)
- [void registerInlineNoteProvider(KTextEditor::InlineNoteProvider \*provider)](#registerInlineNoteProvider)
- [void registerTextHintProvider(KTextEditor::TextHintProvider \*provider)](#registerTextHintProvider)
- [bool removeSelection()](#removeSelection)
- [bool removeSelectionText()](#removeSelectionText)
- [bool selection() const](#selection)
- [KTextEditor::Range selectionRange() const](#selectionRange)
- [QList\<KTextEditor::Range\> selectionRanges() const](#selectionRanges)
- [QString selectionText() const](#selectionText)
- [void setAnnotationBorderVisible(bool visible)](#setAnnotationBorderVisible)
- [void setAnnotationItemDelegate(KTextEditor::AbstractAnnotationItemDelegate \*delegate)](#setAnnotationItemDelegate) (since 6.0)
- [void setAnnotationModel(KTextEditor::AnnotationModel \*model)](#setAnnotationModel)
- [void setAnnotationUniformItemSizes(bool uniformItemSizes)](#setAnnotationUniformItemSizes) (since 6.0)
- [void setAutomaticInvocationEnabled(bool enabled = true)](#setAutomaticInvocationEnabled)
- [bool setBlockSelection(bool on)](#setBlockSelection)
- [void setConfigValue(const QString &key, const QVariant &value)](#setConfigValue)
- [void setContextMenu(QMenu \*menu)](#setContextMenu)
- [bool setCursorPosition(KTextEditor::Cursor position)](#setCursorPosition)
- [void setCursorPositions(const QList\<KTextEditor::Cursor\> &positions)](#setCursorPositions)
- [void setHorizontalScrollPosition(int x)](#setHorizontalScrollPosition)
- [bool setMouseTrackingEnabled(bool enable)](#setMouseTrackingEnabled)
- [void setScrollPosition(KTextEditor::Cursor cursor)](#setScrollPosition)
- [bool setSelection(KTextEditor::Range range)](#setSelection)
- [void setSelections(const QList\<KTextEditor::Range\> &ranges)](#setSelections)
- [void setStatusBarEnabled(bool enable)](#setStatusBarEnabled)
- [void setTextHintDelay(int delay)](#setTextHintDelay)
- [void setViewInputMode(KTextEditor::View::InputMode inputMode)](#setViewInputMode)
- [void startCompletion(KTextEditor::Range word, KTextEditor::CodeCompletionModel \*model)](#startCompletion)
- [void startCompletion(const KTextEditor::Range &word, const QList\<KTextEditor::CodeCompletionModel \*\> &models = QList\<CodeCompletionModel \*\>(), KTextEditor::CodeCompletionModel::InvocationType invocationType = KTextEditor::CodeCompletionModel::ManualInvocation)](#startCompletion-1)
- [QRect textAreaRect() const](#textAreaRect)
- [int textHintDelay() const](#textHintDelay)
- [KSyntaxHighlighting::Theme theme() const](#theme)
- [bool uniformAnnotationItemSizes() const](#uniformAnnotationItemSizes) (since 6.0)
- [void unregisterCompletionModel(KTextEditor::CodeCompletionModel \*model)](#unregisterCompletionModel)
- [void unregisterInlineNoteProvider(KTextEditor::InlineNoteProvider \*provider)](#unregisterInlineNoteProvider)
- [void unregisterTextHintProvider(KTextEditor::TextHintProvider \*provider)](#unregisterTextHintProvider)
- [QScrollBar \*verticalScrollBar() const](#verticalScrollBar) (since 6.0)
- [KTextEditor::View::InputMode viewInputMode() const](#viewInputMode)
- [QString viewInputModeHuman() const](#viewInputModeHuman)
- [KTextEditor::View::ViewMode viewMode() const](#viewMode)
- [QString viewModeHuman() const](#viewModeHuman)
- [int visibleLines() const](#visibleLines) (since 6.27)
- [int visibleToRealLine(int visibleLine) const](#visibleToRealLine) (since 6.27)
- [void writeSessionConfig(KConfigGroup &config, const QSet\<QString\> &flags = QSet\<QString\>())](#writeSessionConfig)

## Signals

- [void annotationActivated(KTextEditor::View \*view, int line)](#annotationActivated)
- [void annotationBorderVisibilityChanged(KTextEditor::View \*view, bool visible)](#annotationBorderVisibilityChanged)
- [void annotationContextMenuAboutToShow(KTextEditor::View \*view, QMenu \*menu, int line)](#annotationContextMenuAboutToShow)
- [void configChanged(KTextEditor::View \*view)](#configChanged)
- [void contextMenuAboutToShow(KTextEditor::View \*view, QMenu \*menu)](#contextMenuAboutToShow)
- [void cursorPositionChanged(KTextEditor::View \*view, KTextEditor::Cursor newPosition)](#cursorPositionChanged)
- [void displayRangeChanged(KTextEditor::View \*view)](#displayRangeChanged) (since 6.8)
- [void focusIn(KTextEditor::View \*view)](#focusIn)
- [void focusOut(KTextEditor::View \*view)](#focusOut)
- [void horizontalScrollPositionChanged(KTextEditor::View \*view)](#horizontalScrollPositionChanged)
- [void mousePositionChanged(KTextEditor::View \*view, KTextEditor::Cursor newPosition)](#mousePositionChanged)
- [void selectionChanged(KTextEditor::View \*view)](#selectionChanged)
- [void statusBarEnabledChanged(KTextEditor::View \*view, bool enabled)](#statusBarEnabledChanged)
- [void textInserted(KTextEditor::View \*view, KTextEditor::Cursor position, const QString &text)](#textInserted)
- [void verticalScrollPositionChanged(KTextEditor::View \*view, KTextEditor::Cursor newPos)](#verticalScrollPositionChanged)
- [void viewInputModeChanged(KTextEditor::View \*view, KTextEditor::View::InputMode mode)](#viewInputModeChanged)
- [void viewModeChanged(KTextEditor::View \*view, KTextEditor::View::ViewMode mode)](#viewModeChanged)

## Static Public Members

- [KTextEditor::View \*fromEditorWidget(QWidget \*editorWidget)](#fromEditorWidget) (since 6.20)

## Protected Functions

- [View(KTextEditor::ViewPrivate \*impl, QWidget \*parent)](#View)

## Detailed Description {#details}

### Introduction {#introduction}

The View class represents a single view of a [KTextEditor::Document](ktexteditor-document.md), get the document on which the view operates with [document](ktexteditor-view.md#document)(). A view provides both the graphical representation of the text and the [KXMLGUIClient](../kxmlgui/kxmlguiclient.md) for the actions. The view itself does not provide text manipulation, use the methods from the Document instead. The only method to insert text is [insertText](ktexteditor-view.md#insertText)(), which inserts the given text at the current cursor position and emits the signal [textInserted](ktexteditor-view.md#textInserted)().

Usually a view is created by using [Document::createView](ktexteditor-document.md#createView)(). Furthermore a view can have a context menu. Set it with [setContextMenu](ktexteditor-view.md#setContextMenu)() and get it with [contextMenu](ktexteditor-view.md#contextMenu)().

### Merging the View's GUI {#merging-the-view-s-gui}

A View is derived from the class [KXMLGUIClient](../kxmlgui/kxmlguiclient.md), so its GUI elements (like menu entries and toolbar items) can be merged into the application's GUI (or into a [KXMLGUIFactory](../kxmlgui/kxmlguifactory.md)) by calling

```cpp
// view is of type KTextEditor::View*
mainWindow()->guiFactory()->addClient( view );
```

You can add only one view as client, so if you have several views, you first have to remove the current view, and then add the new one, like this

```cpp
mainWindow()->guiFactory()->removeClient( currentView );
mainWindow()->guiFactory()->addClient( newView );
```

### Text Selection {#text-selection}

As the view is a graphical text editor it provides *normal* and *block* text selection. You can check with [selection](ktexteditor-view.md#selection)() whether a selection exists. [removeSelection](ktexteditor-view.md#removeSelection)() will remove the selection without removing the text, whereas [removeSelectionText](ktexteditor-view.md#removeSelectionText)() also removes both, the selection and the selected text. Use [selectionText](ktexteditor-view.md#selectionText)() to get the selected text and [setSelection](ktexteditor-view.md#setSelection)() to specify the selected text range. The signal [selectionChanged](ktexteditor-view.md#selectionChanged)() is emitted whenever the selection changed.

### Cursor Positions {#cursor-positions}

A view has one Cursor which represents a line/column tuple. Two different kinds of cursor positions are supported: first is the *real* cursor position where a *tab* character only counts one character. Second is the *virtual* cursor position, where a *tab* character counts as many spaces as defined. Get the real position with [cursorPosition](ktexteditor-view.md#cursorPosition)() and the virtual position with [cursorPositionVirtual](ktexteditor-view.md#cursorPositionVirtual)(). Set the real cursor position with [setCursorPosition](ktexteditor-view.md#setCursorPosition)(). The signal [cursorPositionChanged](ktexteditor-view.md#cursorPositionChanged)() is emitted whenever the cursor position changed.

Screen coordinates of the current text cursor position in pixels are obtained through [cursorPositionCoordinates](ktexteditor-view.md#cursorPositionCoordinates)(). Further conversion of screen pixel coordinates and text cursor positions are provided by [cursorToCoordinate](ktexteditor-view.md#cursorToCoordinate)() and [coordinatesToCursor](ktexteditor-view.md#coordinatesToCursor)().

### Mouse Tracking {#mouse-tracking}

It is possible to get notified via the signal [mousePositionChanged](ktexteditor-view.md#mousePositionChanged)() for mouse move events, if [mouseTrackingEnabled](ktexteditor-view.md#mouseTrackingEnabled)() returns *true*. Mouse tracking can be turned on/off by calling [setMouseTrackingEnabled](ktexteditor-view.md#setMouseTrackingEnabled)(). If an editor implementation does not support mouse tracking, [mouseTrackingEnabled](ktexteditor-view.md#mouseTrackingEnabled)() will always return *false*.

### Input/View Modes {#input-view-modes}

A view supports several input modes. Common input modes are *NormalInputMode* and *ViInputMode*. Which input modes the editor supports depends on the implementation. The getter [viewInputMode](ktexteditor-view.md#viewInputMode)() returns enum InputMode representing the current mode.

Input modes can have their own view modes. In case of default *NormalInputMode* those are *NormalModeInsert* and *NormalModeOverwrite*. You can use [viewMode](ktexteditor-view.md#viewMode)() getter to obtain those.

For [viewMode](ktexteditor-view.md#viewMode)() and [viewInputMode](ktexteditor-view.md#viewInputMode)() there are also variants with *Human* suffix, which returns the human readable representation (i18n) usable for displaying in user interface.

Whenever the input/view mode changes the signals [viewInputModeChanged](ktexteditor-view.md#viewInputModeChanged)()/[viewModeChanged](ktexteditor-view.md#viewModeChanged)() are emitted.

### View Config {#view-config}

Config provides methods to access and modify the low level config information for a given View [KTextEditor::View](ktexteditor-view.md) has support for the following keys:

| Key | Type | Description |
| --- | --- | --- |
| line-numbers | \[bool\] | show/hide line numbers |
| icon-bar | \[bool\] | show/hide icon bar |
| folding-bar | \[bool\] | show/hide the folding bar |
| folding-preview | \[bool\] | enable/disable folding preview when mouse hovers on folded region |
| dynamic-word-wrap | \[bool\] | enable/disable dynamic word wrap |
| background-color | \[QColor\] | read/set the default background color |
| selection-color | \[QColor\] | read/set the default color for selections |
| search-highlight-color | \[QColor\] | read/set the background color for search |
| replace-highlight-color | \[QColor\] | read/set the background color for replaces |
| default-mark-type | \[uint\] | read/set the default mark type |
| allow-mark-menu | \[bool\] | enable/disable the menu shown when right clicking on the left gutter. When disabled, click on the gutter will always set or clear the mark of default type. |
| icon-border-color | \[QColor\] | read/set the icon border color (on the left with the line numbers) |
| folding-marker-color | \[QColor\] | read/set folding marker colors (in the icon border) |
| line-number-color | \[QColor\] | read/set line number colors (in the icon border) |
| current-line-number-color | \[QColor\] | read/set current line number color (in the icon border) |
| modification-markers | \[bool\] | read/set whether the modification markers are shown |
| word-count | \[bool\] | enable/disable the counting of words and characters in the statusbar |
| line-count | \[bool\] | show/hide the total number of lines in the status bar ( |
| scrollbar-minimap | \[bool\] | enable/disable scrollbar minimap |
| scrollbar-preview | \[bool\] | enable/disable scrollbar text preview on hover |
| font | \[QFont\] | change the font |
| theme | \[[QString](https://doc.qt.io/qt-6/qstring.html)\] | change the theme |
| word-completion-minimal-word-length | \[int\] | minimal word length to trigger word completion |
| enter-to-insert-completion | \[bool\] | enable/disable whether pressing enter inserts completion |
| disable-current-line-highlight-if-inactive | \[bool\] | disable current line highlight if the view has no focus ( |
| hide-cursor-if-inactive | \[bool\] | hide cursor if the view has no focus ( |
| disable-bracket-match-highlight-if-inactive | \[bool\] | disable bracket match and code folding highlight if the view has no focus ( |

You can retrieve the value of a config key using [configValue](ktexteditor-view.md#configValue)() and set the value for a config key using [setConfigValue](ktexteditor-view.md#setConfigValue)().

### Annotation Interface {#annotation-interface}

The Annotation Interface allows to do these things:

1. show/hide the annotation border along with the possibility to add actions into its context menu.
2. set a separate AnnotationModel for the View: Note that this interface inherits the AnnotationInterface.
3. set a custom AbstractAnnotationItemDelegate for the View.

For a more detailed explanation about whether you want to set a custom delegate for rendering the annotations, read the detailed documentation about the AbstractAnnotationItemDelegate.

### Inline Notes {#inline-notes}

The inline notes interface provides a way to render arbitrary things in the text. The text layout of the line is adapted to create space for the note. Possible applications include showing a name of a function parameter in a function call or rendering a square with a color preview next to CSS color property.

To register as inline note provider, call [registerInlineNoteProvider](ktexteditor-view.md#registerInlineNoteProvider)() with an instance that inherits InlineNoteProvider. Finally, make sure you remove your inline note provider by calling [unregisterInlineNoteProvider](ktexteditor-view.md#unregisterInlineNoteProvider)().

### Text Hints {#text-hints}

The text hint interface provides a way to show tool tips for text located under the mouse. Possible applications include showing a value of a variable when debugging an application, or showing a complete path of an include directive.

To register as text hint provider, call [registerTextHintProvider](ktexteditor-view.md#registerTextHintProvider)() with an instance that inherits TextHintProvider. Finally, make sure you remove your text hint provider by calling [unregisterTextHintProvider](ktexteditor-view.md#unregisterTextHintProvider)().

Text hints are shown after the user hovers with the mouse for a delay of [textHintDelay](ktexteditor-view.md#textHintDelay)() milliseconds over the same word. To change the delay, call [setTextHintDelay](ktexteditor-view.md#setTextHintDelay)().

### Completion Interface {#completion-interface}

The Completion Interface is designed to provide code completion functionality for a [KTextEditor::View](ktexteditor-view.md). This interface provides the basic mechanisms to display a list of completions, update this list according to user input, and allow the user to select a completion.

Essentially, this provides an item view for the available completions. In order to use this interface, you will need to implement a [CodeCompletionModel](ktexteditor-codecompletionmodel.md) that generates the relevant completions given the current input.

More information about interfaces for the view can be found in: kte\_group\_view\_extensions.

*See also* [KTextEditor::Document](ktexteditor-index.md), [KXMLGUIClient](../kxmlgui/kxmlguiclient.md)

## Member Type Documentation {#member-type-documentation}

### \[since 6.20\] enum View::CoordinatesToCursorFlag {#CoordinatesToCursorFlag-enum}

**flags View::CoordinatesToCursorFlags**

Modifiers to the conversion of coordinates to cursor.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::View::InvalidCursorOutsideText` | `1` | If this flag is set, an invalid cursor is returned for coordinates outside text. Otherwise (by default) the closest cursor on the same line is returned. |

This enum was introduced in Qt 6.20.

The `CoordinatesToCursorFlags` type is a typedef for `QFlags<CoordinatesToCursorFlag>. `It stores an OR combination of `CoordinatesToCursorFlag` values.

### enum View::InputMode {#InputMode-enum}

Possible input modes. These correspond to various modes the text editor might be in.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::View::NormalInputMode` | `0` | Normal mode. |
| `KTextEditor::View::ViInputMode` | `1` | Vi mode. The view will behave like the editor vi(m). |

### enum View::LineType {#LineType-enum}

Possible line types.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::View::RealLine` | `0` | A real line. |
| `KTextEditor::View::VisibleLine` | `1` | A visible line. Line that is not folded. |

### enum View::ViewMode {#ViewMode-enum}

Possible view modes the text editor might be in.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::View::NormalModeInsert` | `0` | Insert mode. Characters will be added. |
| `KTextEditor::View::NormalModeOverwrite` | `1` | Overwrite mode. Characters will be replaced. |
| `KTextEditor::View::ViModeNormal` | `10` |   |
| `KTextEditor::View::ViModeInsert` | `11` |   |
| `KTextEditor::View::ViModeVisual` | `12` |   |
| `KTextEditor::View::ViModeVisualLine` | `13` |   |
| `KTextEditor::View::ViModeVisualBlock` | `14` |   |
| `KTextEditor::View::ViModeReplace` | `15` |   |

## Member Function Documentation {#member-function-documentation}

### \[protected\] View::View(KTextEditor::ViewPrivate \**impl*, QWidget \**parent*) {#View}

Constructor.

Create a view attached to the widget `parent`.

Pass it the internal implementation to store a d-pointer.

`impl` is the d-pointer to use

`parent` is the parent widget

*See also* [Document::createView](ktexteditor-document.md#createView)()

### \[override virtual noexcept\] View::~View() {#dtor.View}

Virtual destructor.

### \[pure virtual\] void View::abortCompletion() {#abortCompletion}

Abort the currently displayed code completion without executing any currently selected completion. This is safe, even when the completion box is not currently active.

*See also* [isCompletionActive](ktexteditor-view.md#isCompletionActive)()

### \[signal\] void View::annotationActivated(KTextEditor::View \**view*, int *line*) {#annotationActivated}

This signal is emitted when an entry on the annotation border was activated, for example by clicking or double-clicking it. This follows the KDE wide setting for activation via click or double-clcik

`view` is the view to which the activated border belongs to

`line` is the document line that the activated position belongs to

### \[signal\] void View::annotationBorderVisibilityChanged(KTextEditor::View \**view*, bool *visible*) {#annotationBorderVisibilityChanged}

This signal is emitted when the annotation border is shown or hidden.

`view` is the view to which the border belongs to

`visible` is the current visibility state

### \[signal\] void View::annotationContextMenuAboutToShow(KTextEditor::View \**view*, QMenu \**menu*, int *line*) {#annotationContextMenuAboutToShow}

This signal is emitted before a context menu is shown on the annotation border for the given line and view.

> **Note:** Kate Part implementation detail: In Kate Part, the menu has an entry to hide the annotation border.

`view` is the view that the annotation border belongs to

`menu` is the context menu that will be shown

`line` is the annotated line for which the context menu is shown

### \[pure virtual, since 6.0\] KTextEditor::AbstractAnnotationItemDelegate \*View::annotationItemDelegate() const {#annotationItemDelegate}

Returns the currently used AbstractAnnotationItemDelegate

Returns the current AbstractAnnotationItemDelegate

This function was introduced in Qt 6.0.

*See also* [setAnnotationItemDelegate](ktexteditor-view.md#setAnnotationItemDelegate)()

### \[pure virtual\] KTextEditor::AnnotationModel \*View::annotationModel() const {#annotationModel}

Returns the currently set AnnotationModel or 0 if there's none set

*See also* [setAnnotationModel](ktexteditor-view.md#setAnnotationModel)()

### \[pure virtual\] bool View::blockSelection() const {#blockSelection}

Get the status of the selection mode. *true* indicates that block selection mode is on. If this is *true*, selections applied via the SelectionInterface are handled as block selections and the Copy&Paste functions work on rectangular blocks of text rather than normal.

Returns *true*, if block selection mode is enabled, otherwise *false*

*See also* [setBlockSelection](ktexteditor-view.md#setBlockSelection)()

### \[pure virtual\] QList\<KTextEditor::CodeCompletionModel \*\> View::codeCompletionModels() const {#codeCompletionModels}

Obtain the list of registered code completion models.

Returns a list of a models that are currently registered

*See also* registerCompletionModel(CodeCompletionModel\*)

### \[signal\] void View::configChanged(KTextEditor::View \**view*) {#configChanged}

This signal is emitted whenever the current view configuration is changed.

`view` is the view whose config has changed

### \[pure virtual\] QStringList View::configKeys() const {#configKeys}

Get a list of all available keys.

### \[pure virtual\] QVariant View::configValue(const QString &*key*) {#configValue}

Get a value for the `key`.

*See also* [setConfigValue](ktexteditor-view.md#setConfigValue)()

### \[pure virtual\] QMenu \*View::contextMenu() const {#contextMenu}

Get the context menu for this view. The return value can be NULL if no context menu object was set and kxmlgui is not initialized yet. If there is no user set menu, the kxmlgui menu is returned. Do not delete this menu, if if it is the xmlgui menu.

Returns context menu object

*See also* [setContextMenu](ktexteditor-view.md#setContextMenu)()

### \[signal\] void View::contextMenuAboutToShow(KTextEditor::View \**view*, QMenu \**menu*) {#contextMenuAboutToShow}

Signal which is emitted immediately prior to showing the current context `menu`.

`view` is the related view

### \[pure virtual\] KTextEditor::Cursor View::coordinatesToCursor(const QPoint &*coord*) const {#coordinatesToCursor}

Returns coordinatesToCursor(coord, {})

### KTextEditor::Cursor View::coordinatesToCursor(QPoint *coords*, KTextEditor::View::CoordinatesToCursorFlags *flags*) const {#coordinatesToCursor-1}

Get the text-cursor in the document from the screen coordinates, relative to the view widget.

To map a cursor to pixel coordinates (the reverse transformation) use [cursorToCoordinate](ktexteditor-view.md#cursorToCoordinate)().

`coords` is the coordinates relative to the view widget `flags` is the modifiers to the conversion

Returns cursor in the View, that points onto the character under the given coordinate. May be KTextEditor::Cursor::invalid().

### \[pure virtual\] KTextEditor::Cursor View::cursorPosition() const {#cursorPosition}

Get the view's current cursor position. A *TAB* character is handled as only one character.

Returns current cursor position

*See also* [setCursorPosition](ktexteditor-view.md#setCursorPosition)()

### \[signal\] void View::cursorPositionChanged(KTextEditor::View \**view*, KTextEditor::Cursor *newPosition*) {#cursorPositionChanged}

This signal is emitted whenever the `view`'s cursor position changed.

`view` is the view which emitted the signal

`newPosition` is the new position of the cursor (Kate will pass the real cursor position, not the virtual)

*See also* [cursorPosition](ktexteditor-view.md#cursorPosition)(), [cursorPositionVirtual](ktexteditor-view.md#cursorPositionVirtual)()

### \[pure virtual\] QPoint View::cursorPositionCoordinates() const {#cursorPositionCoordinates}

Get the screen coordinates (x, y) of the cursor position in pixels. The returned coordinates are relative to the View such that (0, 0) represents the top-left corner of the View.

If global screen coordinates are required, e.g. for showing a [QToolTip](https://doc.qt.io/qt-6/qtooltip.html), convert the view coordinates to global screen coordinates as follows:

```cpp
QPoint viewCoordinates = view->cursorPositionCoordinates();
QPoint globalCoorinates = view->mapToGlobal(viewCoordinates);
```

Returns cursor screen coordinates

*See also* [cursorToCoordinate](ktexteditor-view.md#cursorToCoordinate)(), [coordinatesToCursor](ktexteditor-view.md#coordinatesToCursor)()

### \[pure virtual\] KTextEditor::Cursor View::cursorPositionVirtual() const {#cursorPositionVirtual}

Get the current *virtual* cursor position, *virtual* means the tabulator character (TAB) counts *multiple* characters, as configured by the user (e.g. one TAB is 8 spaces). The virtual cursor position provides access to the user visible values of the current cursor position.

Returns virtual cursor position

*See also* [cursorPosition](ktexteditor-view.md#cursorPosition)()

### QList\<KTextEditor::Cursor\> View::cursorPositions() const {#cursorPositions}

Get the view's current cursor positions. A *TAB* character is handled as only one character.

The returned vector contains the primary cursor as first element.

Returns all currently existing cursors

*See also* [setCursorPositions](ktexteditor-view.md#setCursorPositions)()

### \[pure virtual\] QPoint View::cursorToCoordinate(KTextEditor::Cursor *cursor*) const {#cursorToCoordinate}

Get the screen coordinates (x, y) of the supplied `cursor` relative to the view widget in pixels. Thus, (0, 0) represents the top left hand of the view widget.

To map pixel coordinates to a Cursor position (the reverse transformation) use [coordinatesToCursor](ktexteditor-view.md#coordinatesToCursor)().

`cursor` is the cursor to determine coordinate for.

Returns cursor screen coordinates relative to the view widget

*See also* [cursorPositionCoordinates](ktexteditor-view.md#cursorPositionCoordinates)(), [coordinatesToCursor](ktexteditor-view.md#coordinatesToCursor)()

### \[pure virtual\] QMenu \*View::defaultContextMenu(QMenu \**menu* = nullptr) const {#defaultContextMenu}

Populate `menu` with default text editor actions. If `menu` is null, a menu will be created with the view as its parent.

> **Note:** to use this menu, you will next need to call [setContextMenu](ktexteditor-view.md#setContextMenu)(), as this does not assign the new context menu.

> **Warning:** This contains only basic options from the editor component (katepart). Plugins are **not** merged/integrated into it! If you want to be a better citizen and take full advantage of [KTextEditor](ktexteditor-module.md) plugins do something like:

```cpp
KXMLGUIClient* client = view;
// search parent XmlGuiClient
while (client->parentClient()) {
  client = client->parentClient();
}

if (client->factory()) {
  const QList<QWidget*> menuContainers = client->factory()->containers("menu");
  for (QWidget *w : menuContainers) {
    if (w->objectName() == "ktexteditor_popup") {
      // do something with the menu (ie adding an onshow handler)
      break;
    }
  }
}
```

> **Warning:** or simply use the aboutToShow, aboutToHide signals !!!!!

`menu` is the menu to be populated, or null to create a new menu.

Returns the menu, whether created or passed initially

### \[pure virtual\] QExplicitlySharedDataPointer\<KTextEditor::Attribute\> View::defaultStyleAttribute(KSyntaxHighlighting::Theme::TextStyle *defaultStyle*) const {#defaultStyleAttribute}

Returns the attribute for the default style `defaultStyle`.

`defaultStyle` default style to get the attribute for

*See also* [KTextEditor::Attribute](ktexteditor-index.md)

### \[signal, since 6.8\] void View::displayRangeChanged(KTextEditor::View \**view*) {#displayRangeChanged}

This signal is emitted whenever the displayed range changes

**\<Unknown command\>`see`**[firstDisplayedLine](ktexteditor-view.md#firstDisplayedLine)() **\<Unknown command\>`see`** [lastDisplayedLine](ktexteditor-view.md#lastDisplayedLine)()

This function was introduced in Qt 6.8.

### \[pure virtual\] KTextEditor::Document \*View::document() const {#document}

Get the view's *document*, that means the view is a view of the returned document. Returns the view's document

### \[since 6.20\] QWidget \*View::editorWidget() const {#editorWidget}

Get the view's editor widget.

Returns the non-null editor widget, which contains the actual text editing area

This function was introduced in Qt 6.20.

*See also* [fromEditorWidget](ktexteditor-view.md#fromEditorWidget)()

### \[since 6.15\] bool View::evaluateScript(const QString &*script*, QVariant \**result* = nullptr) {#evaluateScript}

Run a piece of javascript.

`script` is the javascript code to run

`result` is set to a [QVariant](https://doc.qt.io/qt-6/qvariant.html) representing the return value, or - in case of an error - the error message as a string. If set to nullptr, no result is passed. Note that many but not all javascript objects can be accurately represented as a [QVariant](https://doc.qt.io/qt-6/qvariant.html). Consider simplifying / stringifying complex objects, if this may be an issue.

Returns *true* on success, *false* if an error orrcured. Note that the document may still have been modified, before an error!

This function was introduced in Qt 6.15.

*See also* [insertTemplate](ktexteditor-view.md#insertTemplate)()

### int View::firstDisplayedLine(KTextEditor::View::LineType *lineType* = RealLine) const {#firstDisplayedLine}

Get the first displayed line in the view.

> **Note:** If code is folded, many hundred lines can be between firstDisplayedLine() and [lastDisplayedLine](ktexteditor-view.md#lastDisplayedLine)().

`lineType` if [RealLine](ktexteditor-view.md#LineType-enum) (the default), it returns the real line number accounting for folded regions. In that case it walks over all folded regions O(n) for n == number of folded ranges

Returns the first displayed line

*See also* [lastDisplayedLine](ktexteditor-view.md#lastDisplayedLine)()

### \[signal\] void View::focusIn(KTextEditor::View \**view*) {#focusIn}

This signal is emitted whenever the `view` gets the focus.

`view` is the view which gets focus

*See also* [focusOut](ktexteditor-view.md#focusOut)()

### \[signal\] void View::focusOut(KTextEditor::View \**view*) {#focusOut}

This signal is emitted whenever the `view` loses the focus.

`view` is view which lost focus

*See also* [focusIn](ktexteditor-view.md#focusIn)()

### \[pure virtual\] void View::forceCompletion() {#forceCompletion}

Force execution of the currently selected completion, and hide the code completion box.

### \[static, since 6.20\] KTextEditor::View \*View::fromEditorWidget(QWidget \**editorWidget*) {#fromEditorWidget}

Get the view that owns a given editor widget.

`editorWidget` is a widget that has been returned from [editorWidget](ktexteditor-view.md#editorWidget)()

Returns the matching view or `nullptr` for a null widget

This function was introduced in Qt 6.20.

### \[pure virtual, since 6.0\] QScrollBar \*View::horizontalScrollBar() const {#horizontalScrollBar}

Returns The horizontal scrollbar of this view

This function was introduced in Qt 6.0.

### \[signal\] void View::horizontalScrollPositionChanged(KTextEditor::View \**view*) {#horizontalScrollPositionChanged}

This signal should be emitted whenever the `view` is scrolled horizontally.

`view` is the view which emitted the signal

### bool View::insertTemplate(KTextEditor::Cursor *insertPosition*, const QString &*templateString*, const QString &*script* = QString()) {#insertTemplate}

Insert a template into the document. The template can have editable fields which can be filled by the user. You can create editable fields with ${fieldname}; multiple fields with the same name will have their contents synchronized automatically, and only the first one is editable in this case. Fields can have a default value specified by writing ${fieldname=default}. Note that \`default' is a JavaScript expression and strings need to be quoted. You can also provide a piece of JavaScript for more complex logic. To create a field which provides text based on a JS function call and the values of the other, editable fields, use the ${func()} syntax. func() must be a callable object defined in `script`. You can pass arguments to the function by just writing any constant expression or a field name.

`insertPosition` is where to insert the template

`templateString` is the template to insert using the above syntax

`script` is a script with functions which can be used in `templateString`

Returns true on success, false if insertion failed (e.g. read-only mode)

*See also* [evaluateScript](ktexteditor-view.md#evaluateScript)()

### \[virtual\] bool View::insertText(const QString &*text*) {#insertText}

This is a convenience function which inserts `text` at the view's current cursor position. You do not necessarily need to reimplement it, except you want to do some special things.

`text` is the text to be inserted

Returns *true* on success of insertion, otherwise *false*

*See also* [textInserted](ktexteditor-view.md#textInserted)()

### \[pure virtual\] bool View::isAnnotationBorderVisible() const {#isAnnotationBorderVisible}

Returns true if he View's annotation border is visible.

### \[pure virtual\] bool View::isAutomaticInvocationEnabled() const {#isAutomaticInvocationEnabled}

Returns true if automatic code completion invocation is enabled.

### \[pure virtual\] bool View::isCompletionActive() const {#isCompletionActive}

Returns true if the code completion box is currently displayed.

### \[since 6.27\] bool View::isLineVisible(int *realLine*) const {#isLineVisible}

Returns whether the given `realLine` is currently visible, i.e. not hidden inside a folded region.

*realLine* the real line number to query (0-indexed) Returns `true` if the line is visible, `false` if it is hidden inside a fold or if `realLine` is out of range

**\<Unknown command\>`see`**[realToVisibleLine](ktexteditor-view.md#realToVisibleLine)()

This function was introduced in Qt 6.27.

### bool View::isStatusBarEnabled() const {#isStatusBarEnabled}

Is the status bar enabled?

Returns status bar enabled?

### int View::lastDisplayedLine(KTextEditor::View::LineType *lineType* = RealLine) const {#lastDisplayedLine}

Get the last displayed line in the view.

> **Note:** If code is folded, many hundred lines can be between [firstDisplayedLine](ktexteditor-view.md#firstDisplayedLine)() and lastDisplayedLine().

`lineType` is if [RealLine](ktexteditor-view.md#LineType-enum) (the default), it returns the real line number accounting for folded regions. In that case it walks over all folded regions. O(n) for n == number of folded ranges

Returns the last displayed line

*See also* [firstDisplayedLine](ktexteditor-view.md#firstDisplayedLine)()

### \[pure virtual\] QList\<KTextEditor::AttributeBlock\> View::lineAttributes(int *line*) {#lineAttributes}

Get the list of AttributeBlocks for a given `line` in the document.

Returns list of AttributeBlocks for given `line`.

### \[pure virtual\] KTextEditor::MainWindow \*View::mainWindow() const {#mainWindow}

Get the view's main window, if any

Returns the view's main window, will always return at least some non-nullptr dummy interface

### KTextEditor::Cursor View::maxScrollPosition() const {#maxScrollPosition}

Get the cursor corresponding to the maximum position the view can vertically scroll to.

Returns cursor position of the maximum vertical scroll position.

### \[signal\] void View::mousePositionChanged(KTextEditor::View \**view*, KTextEditor::Cursor *newPosition*) {#mousePositionChanged}

This signal is emitted whenever the position of the mouse changes over this `view`. If the mouse moves off the view, an invalid cursor position should be emitted, i.e. [Cursor::invalid](ktexteditor-cursor.md#invalid)().

> **Note:** If [mouseTrackingEnabled](ktexteditor-view.md#mouseTrackingEnabled)() returns *false*, this signal is never emitted.

`view` is the view which emitted the signal

`newPosition` is the new position of the mouse or [Cursor::invalid](ktexteditor-cursor.md#invalid)(), if the mouse moved out of the `view`.

*See also* [mouseTrackingEnabled](ktexteditor-view.md#mouseTrackingEnabled)()

### \[pure virtual\] bool View::mouseTrackingEnabled() const {#mouseTrackingEnabled}

Check, whether mouse tracking is enabled.

Mouse tracking is required to have the signal [mousePositionChanged](ktexteditor-view.md#mousePositionChanged)() emitted.

Returns *true*, if mouse tracking is enabled, otherwise *false*

*See also* [setMouseTrackingEnabled](ktexteditor-view.md#setMouseTrackingEnabled)(), [mousePositionChanged](ktexteditor-view.md#mousePositionChanged)()

### \[pure virtual\] bool View::print() {#print}

Print the document. This should result in showing the print dialog.

Returns true if document was printed

### \[pure virtual\] void View::printPreview() {#printPreview}

Shows the print preview dialog/

### \[pure virtual\] void View::readSessionConfig(const KConfigGroup &*config*, const QSet\<QString\> &*flags* = QSet\<QString\>()) {#readSessionConfig}

Read session settings from the given `config`.

Known flags: none atm

`config` is the [KConfigGroup](../kconfigcore/kconfiggroup.md) to read the session settings from

`flags` is additional flags

*See also* [writeSessionConfig](ktexteditor-view.md#writeSessionConfig)()

### \[since 6.27\] int View::realToVisibleLine(int *realLine*) const {#realToVisibleLine}

Convert a real line number to a visible line number.

> **Note:** If the line is hidden inside a folded region, returns the visible line number of the last visible line before the fold. To test whether a lilne is visible, use [isLineVisible](ktexteditor-view.md#isLineVisible)() instead.

*realLine* the real line number to convert (0-indexed) Returns the corresponding visible line number, or -1 if `realLine` is out of range.

**\<Unknown command\>`see`**[visibleToRealLine](ktexteditor-view.md#visibleToRealLine)() **\<Unknown command\>`see`** [visibleLines](ktexteditor-view.md#visibleLines)() **\<Unknown command\>`see`** [isLineVisible](ktexteditor-view.md#isLineVisible)()

This function was introduced in Qt 6.27.

### \[pure virtual\] void View::registerCompletionModel(KTextEditor::CodeCompletionModel \**model*) {#registerCompletionModel}

Register a new code completion `model`.

`model` is new completion model

*See also* [unregisterCompletionModel](ktexteditor-view.md#unregisterCompletionModel)()

### \[pure virtual\] void View::registerInlineNoteProvider(KTextEditor::InlineNoteProvider \**provider*) {#registerInlineNoteProvider}

Register the inline note provider `provider`.

Whenever a line is painted, the `provider` will be queried for notes that should be painted in it. When the provider is about to be destroyed, make sure to call [unregisterInlineNoteProvider](ktexteditor-view.md#unregisterInlineNoteProvider)() to avoid a dangling pointer.

`provider` inline note provider

*See also* [unregisterInlineNoteProvider](ktexteditor-view.md#unregisterInlineNoteProvider)(), [KTextEditor::InlineNoteProvider](ktexteditor-index.md)

### \[pure virtual\] void View::registerTextHintProvider(KTextEditor::TextHintProvider \**provider*) {#registerTextHintProvider}

Register the text hint provider `provider`.

Whenever the user hovers over text, `provider` will be asked for a text hint. When the provider is about to be destroyed, make sure to call [unregisterTextHintProvider](ktexteditor-view.md#unregisterTextHintProvider)() to avoid a dangling pointer.

`provider` text hint provider

*See also* [unregisterTextHintProvider](ktexteditor-view.md#unregisterTextHintProvider)(), [KTextEditor::TextHintProvider](ktexteditor-index.md)

### \[pure virtual\] bool View::removeSelection() {#removeSelection}

Remove the view's current selection, *without* deleting the selected text.

Returns *true* on success, otherwise *false*

*See also* [removeSelectionText](ktexteditor-view.md#removeSelectionText)()

### \[pure virtual\] bool View::removeSelectionText() {#removeSelectionText}

Remove the view's current selection *including* the selected text.

Returns *true* on success, otherwise *false*

*See also* [removeSelection](ktexteditor-view.md#removeSelection)()

### \[pure virtual\] bool View::selection() const {#selection}

Query the view whether it has selected text, i.e. whether a selection exists.

Returns *true* if a text selection exists, otherwise *false*

*See also* [setSelection](ktexteditor-view.md#setSelection)(), [selectionRange](ktexteditor-view.md#selectionRange)()

### \[signal\] void View::selectionChanged(KTextEditor::View \**view*) {#selectionChanged}

This signal is emitted whenever the `view`'s selection changes.

> **Note:** If the mode switches from block selection to normal selection or vice versa this signal should also be emitted.

`view` is the view in which the selection changed

*See also* [selection](ktexteditor-view.md#selection)(), [selectionRange](ktexteditor-view.md#selectionRange)(), [selectionText](ktexteditor-view.md#selectionText)()

### \[pure virtual\] KTextEditor::Range View::selectionRange() const {#selectionRange}

Get the range occupied by the current selection.

Returns selection range, valid only if a selection currently exists.

*See also* [setSelection](ktexteditor-view.md#setSelection)()

### QList\<KTextEditor::Range\> View::selectionRanges() const {#selectionRanges}

Get the ranges occupied by the current selections.

Returns selection ranges, valid only if a selection currently exists.

*See also* [setSelections](ktexteditor-view.md#setSelections)()

### \[pure virtual\] QString View::selectionText() const {#selectionText}

Get the view's selected text.

Returns the selected text

*See also* [setSelection](ktexteditor-view.md#setSelection)()

### \[pure virtual\] void View::setAnnotationBorderVisible(bool *visible*) {#setAnnotationBorderVisible}

This function can be used to show or hide the annotation border The annotation border is hidden by default.

`visible` if *true* the annotation border is shown, otherwise hidden

*See also* [isAnnotationBorderVisible](ktexteditor-view.md#isAnnotationBorderVisible)()

### \[pure virtual, since 6.0\] void View::setAnnotationItemDelegate(KTextEditor::AbstractAnnotationItemDelegate \**delegate*) {#setAnnotationItemDelegate}

Sets the AbstractAnnotationItemDelegate for this view and the model to provide custom rendering of annotation information for each line. Ownership is not transferred.

`delegate` is the new AbstractAnnotationItemDelegate, or `nullptr` to reset to the default delegate

This function was introduced in Qt 6.0.

*See also* [annotationItemDelegate](ktexteditor-view.md#annotationItemDelegate)()

### \[pure virtual\] void View::setAnnotationModel(KTextEditor::AnnotationModel \**model*) {#setAnnotationModel}

Sets a new AnnotationModel for this document to provide annotation information for each line.

`model` is the new AnnotationModel

*See also* [annotationModel](ktexteditor-view.md#annotationModel)()

### \[pure virtual, since 6.0\] void View::setAnnotationUniformItemSizes(bool *uniformItemSizes*) {#setAnnotationUniformItemSizes}

This function can be used to declare whether it is known that the annotation items rendered by the set delegate all have the same size. This enables the view to do some optimizations for performance purposes.

By default the value of this property is `false` .

`uniformItemSizes` if `true` the annotation items are considered to all have the same size

This function was introduced in Qt 6.0.

### \[pure virtual\] void View::setAutomaticInvocationEnabled(bool *enabled* = true) {#setAutomaticInvocationEnabled}

Enable (if `enabled` is true) or disable automatic code completion invocation.

*See also* [isAutomaticInvocationEnabled](ktexteditor-view.md#isAutomaticInvocationEnabled)()

### \[pure virtual\] bool View::setBlockSelection(bool *on*) {#setBlockSelection}

Set block selection mode to state `on`.

`on` if *true*, block selection mode is turned on, otherwise off

Returns *true* on success, otherwise *false*

*See also* [blockSelection](ktexteditor-view.md#blockSelection)()

### \[pure virtual\] void View::setConfigValue(const QString &*key*, const QVariant &*value*) {#setConfigValue}

Set a the `key`'s value to `value`.

*See also* [configValue](ktexteditor-view.md#configValue)()

### \[pure virtual\] void View::setContextMenu(QMenu \**menu*) {#setContextMenu}

Set a context menu for this view to `menu`.

> **Note:** any previously assigned menu is not deleted. If you are finished with the previous menu, you may delete it.

> **Warning:** Use this with care! Plugin xml gui clients are not merged into this menu!

> **Warning:** !!!!!! DON'T USE THIS FUNCTION, UNLESS YOU ARE SURE YOU DON'T WANT PLUGINS TO WORK !!!!!!

`menu` is the new context menu object for this view

*See also* [contextMenu](ktexteditor-view.md#contextMenu)()

### \[pure virtual\] bool View::setCursorPosition(KTextEditor::Cursor *position*) {#setCursorPosition}

Set the view's new cursor to `position`. A *TAB* character is handled as only on character.

`position` is the new cursor position

Returns *true* on success, otherwise *false*

*See also* [cursorPosition](ktexteditor-view.md#cursorPosition)()

### void View::setCursorPositions(const QList\<KTextEditor::Cursor\> &*positions*) {#setCursorPositions}

Set the view's new cursors to `positions`. A *TAB* character is handled as only on character.

This allows to create multiple cursors in this view.

The first passed position will be used for the primary cursor just like if you would call [setCursorPosition](ktexteditor-view.md#setCursorPosition)().

`positions` is the new cursor positions

*See also* [cursorPositions](ktexteditor-view.md#cursorPositions)()

### void View::setHorizontalScrollPosition(int *x*) {#setHorizontalScrollPosition}

Horizontally scroll view to position.

`x` is the pixel position to scroll to.

### \[pure virtual\] bool View::setMouseTrackingEnabled(bool *enable*) {#setMouseTrackingEnabled}

Try to enable or disable mouse tracking according to `enable`. The return value contains the state of mouse tracking *after* the request. Mouse tracking is required to have the [mousePositionChanged](ktexteditor-view.md#mousePositionChanged)() signal emitted.

> **Note:** Implementation Notes: An implementation is not forced to support this, and should always return *false* if it does not have support.

`enable` if *true*, try to enable mouse tracking, otherwise disable it.

Returns the current state of mouse tracking

*See also* [mouseTrackingEnabled](ktexteditor-view.md#mouseTrackingEnabled)(), [mousePositionChanged](ktexteditor-view.md#mousePositionChanged)()

### void View::setScrollPosition(KTextEditor::Cursor *cursor*) {#setScrollPosition}

Scroll view to cursor.

`cursor` is the cursor position to scroll to.

### \[pure virtual\] bool View::setSelection(KTextEditor::Range *range*) {#setSelection}

Set the view's selection to the range selection. The old selection will be discarded.

`range` is the range of the new selection

Returns *true* on success, otherwise *false* (e.g. when the cursor range is invalid)

*See also* [selectionRange](ktexteditor-view.md#selectionRange)(), [selection](ktexteditor-view.md#selection)()

### void View::setSelections(const QList\<KTextEditor::Range\> &*ranges*) {#setSelections}

Set the view's selections to the ranges selection. The old selection will be discarded.

`ranges` is the ranges of the new selections

*See also* [selectionRanges](ktexteditor-view.md#selectionRanges)(), [selection](ktexteditor-view.md#selection)()

### void View::setStatusBarEnabled(bool *enable*) {#setStatusBarEnabled}

Show/hide the status bar of the view. Per default, the status bar is enabled.

`enable` should the status bar be enabled?

*See also* [isStatusBarEnabled](ktexteditor-view.md#isStatusBarEnabled)()

### \[pure virtual\] void View::setTextHintDelay(int *delay*) {#setTextHintDelay}

Set the text hint delay to `delay` milliseconds.

The delay specifies the time the user needs to hover over the text before the tool tip is shown. Therefore, `delay` should not be too large, a value of 500 milliseconds is recommended and set by default.

If `delay` is \<= 0, the default delay will be set.

`delay` is the tool tip delay in milliseconds

*See also* [textHintDelay](ktexteditor-view.md#textHintDelay)()

### \[pure virtual\] void View::setViewInputMode(KTextEditor::View::InputMode *inputMode*) {#setViewInputMode}

Set the view's new input mode.

`inputMode` is new [InputMode](ktexteditor-view.md#InputMode-enum) value

*See also* [viewInputMode](ktexteditor-view.md#viewInputMode)()

### \[pure virtual\] void View::startCompletion(KTextEditor::Range *word*, KTextEditor::CodeCompletionModel \**model*) {#startCompletion}

Invoke code completion over a given range `word` with a specific `model`.

### \[pure virtual\] void View::startCompletion(const KTextEditor::Range &*word*, const QList\<KTextEditor::CodeCompletionModel \*\> &*models* = QList\<CodeCompletionModel \*\>(), KTextEditor::CodeCompletionModel::InvocationType *invocationType* = KTextEditor::CodeCompletionModel::ManualInvocation) {#startCompletion-1}

Invoke code completion over a given range, with specific models and invocation type.

`models` is the list of models to start. If this is an empty list, all registered models are started.

### \[signal\] void View::statusBarEnabledChanged(KTextEditor::View \**view*, bool *enabled*) {#statusBarEnabledChanged}

This signal is emitted whenever the status bar of `view` is toggled.

`enabled` Whether the status bar is currently enabled or not

### QRect View::textAreaRect() const {#textAreaRect}

Get the view's text area rectangle excluding border, scrollbars, etc.

Returns the view's text area rectangle

### \[pure virtual\] int View::textHintDelay() const {#textHintDelay}

Get the text hint delay in milliseconds. By default, the text hint delay is set to 500 milliseconds. It can be changed by calling [setTextHintDelay](ktexteditor-view.md#setTextHintDelay)().

*See also* [setTextHintDelay](ktexteditor-view.md#setTextHintDelay)()

### \[signal\] void View::textInserted(KTextEditor::View \**view*, KTextEditor::Cursor *position*, const QString &*text*) {#textInserted}

This signal is emitted from `view` whenever the users inserts `text` at `position`, that means the user typed/pasted text.

`view` is the view in which the text was inserted

`position` is the position where the text was inserted

`text` is the inserted text

*See also* [insertText](ktexteditor-view.md#insertText)()

### KSyntaxHighlighting::Theme View::theme() const {#theme}

Get the current active theme of this view. Might change during runtime, [configChanged](ktexteditor-view.md#configChanged)() will be emitted in that cases.

Returns current active theme

### \[pure virtual, since 6.0\] bool View::uniformAnnotationItemSizes() const {#uniformAnnotationItemSizes}

Returns true if the annotation items all have the same size.

This function was introduced in Qt 6.0.

### \[pure virtual\] void View::unregisterCompletionModel(KTextEditor::CodeCompletionModel \**model*) {#unregisterCompletionModel}

Unregister a code completion `model`.

`model` is the model that should be unregistered

*See also* [registerCompletionModel](ktexteditor-view.md#registerCompletionModel)()

### \[pure virtual\] void View::unregisterInlineNoteProvider(KTextEditor::InlineNoteProvider \**provider*) {#unregisterInlineNoteProvider}

Unregister the inline note provider `provider`.

`provider` inline note provider to unregister

*See also* [registerInlineNoteProvider](ktexteditor-view.md#registerInlineNoteProvider)(), [KTextEditor::InlineNoteProvider](ktexteditor-index.md)

### \[pure virtual\] void View::unregisterTextHintProvider(KTextEditor::TextHintProvider \**provider*) {#unregisterTextHintProvider}

Unregister the text hint provider `provider`.

`provider` text hint provider to unregister

*See also* [registerTextHintProvider](ktexteditor-view.md#registerTextHintProvider)(), [KTextEditor::TextHintProvider](ktexteditor-index.md)

### \[pure virtual, since 6.0\] QScrollBar \*View::verticalScrollBar() const {#verticalScrollBar}

Returns The vertical scrollbar of this view

This function was introduced in Qt 6.0.

### \[signal\] void View::verticalScrollPositionChanged(KTextEditor::View \**view*, KTextEditor::Cursor *newPos*) {#verticalScrollPositionChanged}

This signal should be emitted whenever the `view` is scrolled vertically.

`view` is the view which emitted the signal

`newPos` is the new scroll position

### \[pure virtual\] KTextEditor::View::InputMode View::viewInputMode() const {#viewInputMode}

Get the view's current input mode. The current mode can be NormalInputMode and ViInputMode. For human translated version

Returns the current input mode of this view

*See also* [setViewInputMode](ktexteditor-view.md#setViewInputMode)(), [viewInputModeHuman](ktexteditor-view.md#viewInputModeHuman), [viewInputModeChanged](ktexteditor-view.md#viewInputModeChanged)()

### \[signal\] void View::viewInputModeChanged(KTextEditor::View \**view*, KTextEditor::View::InputMode *mode*) {#viewInputModeChanged}

This signal is emitted whenever the `view`'s input `mode` changes.

`view` is the view which changed its input mode

`mode` is the new input mode

*See also* [viewInputMode](ktexteditor-view.md#viewInputMode)()

### \[pure virtual\] QString View::viewInputModeHuman() const {#viewInputModeHuman}

Get the view's current input mode in human readable form. The string should be translated (i18n). For id like version

Returns the current input mode of this view in human readable form

*See also* [viewInputMode](ktexteditor-view.md#viewInputMode)

### \[pure virtual\] KTextEditor::View::ViewMode View::viewMode() const {#viewMode}

Get the current view mode/state. This can be used to detect the view's current mode. For example NormalInputMode, ViInputMode or whatever other input modes are supported.

Returns current view mode/state

*See also* [viewModeChanged](ktexteditor-view.md#viewModeChanged)(), [viewModeHuman](ktexteditor-view.md#viewModeHuman)()

### \[signal\] void View::viewModeChanged(KTextEditor::View \**view*, KTextEditor::View::ViewMode *mode*) {#viewModeChanged}

This signal is emitted whenever the view mode of `view` changes.

`view` is the view which changed its mode

`mode` is the new view mode

*See also* [viewMode](ktexteditor-view.md#viewMode)()

### \[pure virtual\] QString View::viewModeHuman() const {#viewModeHuman}

Get the current view mode state.

This can be used to visually indicate the view's current mode, for example *INSERT* mode, *OVERWRITE* mode or *COMMAND* mode - or whatever other edit modes are supported. The string should be translated (i18n), as this is a user aimed representation of the view state, which should be shown in the GUI, for example in the status bar. This string may be rich-text.

Returns Human-readable version of the view mode state

*See also* [viewModeChanged](ktexteditor-view.md#viewModeChanged)()

### \[since 6.27\] int View::visibleLines() const {#visibleLines}

Returns the total number of visible lines, i.e. the number of lines in the document that are not hidden inside a folded region.

This is the upper bound for [visibleToRealLine](ktexteditor-view.md#visibleToRealLine)() and valid visible line numbers are in the range \[0, visibleLines() - 1\].

Returns number of visible (non-folded) lines

**\<Unknown command\>`see`**[visibleToRealLine](ktexteditor-view.md#visibleToRealLine)() **\<Unknown command\>`see`** [realToVisibleLine](ktexteditor-view.md#realToVisibleLine)()

This function was introduced in Qt 6.27.

### \[since 6.27\] int View::visibleToRealLine(int *visibleLine*) const {#visibleToRealLine}

Convert a visible line number to a real line number.

Visible line numbers are a contiguous sequence from 0 to [visibleLines](ktexteditor-view.md#visibleLines)() - 1 that skips all lines hidden inside a folded region.

> **Note:** A line that is "visible" means it is not in a folded region. It may still be scrolled outside the current viewport, i.e. not "displayed". Use [firstDisplayedLine](ktexteditor-view.md#firstDisplayedLine)() and [lastDisplayedLine](ktexteditor-view.md#lastDisplayedLine)() to query what is currently displayed on screen.

*visibleLine* the visible line number to convert (0-indexed) Returns the corresponding real line number, or -1 if `visibleLine` is out of range (i.e. \>= [visibleLines](ktexteditor-view.md#visibleLines)()).

**\<Unknown command\>`see`**[realToVisibleLine](ktexteditor-view.md#realToVisibleLine)() **\<Unknown command\>`see`** [visibleLines](ktexteditor-view.md#visibleLines)()

This function was introduced in Qt 6.27.

### \[pure virtual\] void View::writeSessionConfig(KConfigGroup &*config*, const QSet\<QString\> &*flags* = QSet\<QString\>()) {#writeSessionConfig}

Write session settings to the `config`. See [readSessionConfig](ktexteditor-view.md#readSessionConfig)() for more details.

`config` is the [KConfigGroup](../kconfigcore/kconfiggroup.md) to write the session settings to

`flags` is additional flags (see the known flags listed in [readSessionConfig](ktexteditor-view.md#readSessionConfig)())

*See also* [readSessionConfig](ktexteditor-view.md#readSessionConfig)()
