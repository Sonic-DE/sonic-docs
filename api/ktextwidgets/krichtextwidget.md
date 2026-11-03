---
title: "KRichTextWidget Class"
description: "A KRichTextEdit with common actions."
---

# KRichTextWidget Class

A [KRichTextEdit](krichtextedit.md) with common actions. [More...](#details)

- **Header:** `#include <KRichTextWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextWidgets)`
- **Inherits:** [KRichTextEdit](krichtextedit.md)

[List of all members, including inherited members](krichtextwidget-members.md)

## Public Types

- [enum KRichTextWidget::RichTextSupportValues](#RichTextSupportValues-enum)

## Public Functions

- [KRichTextWidget(QWidget \*parent)](#KRichTextWidget)
- [KRichTextWidget(const QString &text, QWidget \*parent = nullptr)](#KRichTextWidget-1)
- [~KRichTextWidget()](#dtor.KRichTextWidget)
- [QList\<QAction \*\> createActions()](#createActions)
- [KRichTextWidget::RichTextSupport richTextSupport() const](#richTextSupport)
- [void setRichTextSupport(const KRichTextWidget::RichTextSupport &support)](#setRichTextSupport)
- [void updateActionStates()](#updateActionStates)

## Public Slots

- [void setActionsEnabled(bool enabled)](#setActionsEnabled)

## Detailed Description {#details}

This class implements common actions which are often used with [KRichTextEdit](krichtextedit.md). All you need to do is to call [createActions](krichtextwidget.md#createActions)(), and the actions will be added to your KXMLGUIWindow. Remember to also add the chosen actions to your application ui.rc file.

See the [KRichTextWidget::RichTextSupportValues](krichtextwidget.md#RichTextSupportValues-enum) enum for an overview of supported actions.

## Member Type Documentation {#member-type-documentation}

### enum KRichTextWidget::RichTextSupportValues {#RichTextSupportValues-enum}

**flags KRichTextWidget::RichTextSupport**

These flags describe what actions will be created by [createActions](krichtextwidget.md#createActions)() after passing a combination of these flags to [setRichTextSupport](krichtextwidget.md#setRichTextSupport)().

| Constant | Value | Description |
| --- | --- | --- |
| `KRichTextWidget::DisableRichText` | `0x00` | No rich text support at all, no actions will be created. Do not use in combination with other flags. |
| `KRichTextWidget::SupportBold` | `0x01` | Action to format the selected text as bold. If no text is selected, the word under the cursor is formatted bold. This is a KToggleAction. The status is automatically updated when the text cursor is moved. |
| `KRichTextWidget::SupportItalic` | `0x02` | Action to format the selected text as italic. If no text is selected, the word under the cursor is formatted italic. This is a KToggleAction. The status is automatically updated when the text cursor is moved. |
| `KRichTextWidget::SupportUnderline` | `0x04` | Action to underline the selected text. If no text is selected, the word under the cursor is underlined. This is a KToggleAction. The status is automatically updated when the text cursor is moved. |
| `KRichTextWidget::SupportStrikeOut` | `0x08` | Action to strike out the selected text. If no text is selected, the word under the cursor is struck out. This is a KToggleAction. The status is automatically updated when the text cursor is moved. |
| `KRichTextWidget::SupportFontFamily` | `0x10` | Action to change the font family of the currently selected text. If no text is selected, the font family of the word under the cursor is changed. Displayed as a combobox when inserted into the toolbar. This is a KFontAction. The status is automatically updated when the text cursor is moved. |
| `KRichTextWidget::SupportFontSize` | `0x20` | Action to change the font size of the currently selected text. If no text is selected, the font size of the word under the cursor is changed. Displayed as a combobox when inserted into the toolbar. This is a KFontSizeAction. The status is automatically updated when the text cursor is moved. |
| `KRichTextWidget::SupportTextForegroundColor` | `0x40` | Action to change the text color of the currently selected text. If no text is selected, the text color of the word under the cursor is changed. Opens a [QColorDialog](https://doc.qt.io/qt-6/qcolordialog.html) to select the color. |
| `KRichTextWidget::SupportTextBackgroundColor` | `0x80` | Action to change the background color of the currently selected text. If no text is selected, the background color of the word under the cursor is changed. Opens a [QColorDialog](https://doc.qt.io/qt-6/qcolordialog.html) to select the color. |
| `KRichTextWidget::FullTextFormattingSupport` | `0xff` | A combination of all the flags above. Includes all actions that change the format of the text. |
| `KRichTextWidget::SupportChangeListStyle` | `0x100` | Action to make the current line a list element, change the list style or remove list formatting. Displayed as a combobox when inserted into a toolbar. This is a KSelectAction. The status is automatically updated when the text cursor is moved. |
| `KRichTextWidget::SupportIndentLists` | `0x200` | Action to increase the current list nesting level. This makes it possible to create nested lists. |
| `KRichTextWidget::SupportDedentLists` | `0x400` | Action to decrease the current list nesting level. |
| `KRichTextWidget::FullListSupport` | `0xf00` | All of the three list actions above. Includes all list-related actions. |
| `KRichTextWidget::SupportAlignment` | `0x100000` | Actions to align the current paragraph left, right, center or justify. These actions are KToogleActions. The status is automatically updated when the text cursor is moved. |
| `KRichTextWidget::SupportRuleLine` | `0x400000` | Action to insert a horizontal line. |
| `KRichTextWidget::SupportHyperlinks` | `0x800000` | Action to convert the current text to a hyperlink. If no text is selected, the word under the cursor is converted. This action opens a dialog where the user can enter the link target. |
| `KRichTextWidget::SupportFormatPainting` | `0x1000000` | Action to make the mouse cursor a format painter. The user can select text with that painter. The selected text gets the same format as the text that was previously selected. |
| `KRichTextWidget::SupportToPlainText` | `0x2000000` | Action to change the text of the whole text edit to plain text. All rich text formatting will get lost. |
| `KRichTextWidget::SupportSuperScriptAndSubScript` | `0x4000000` | Actions to format text as superscript or subscript. If no text is selected, the word under the cursor is formatted as selected. This is a KToggleAction. The status is automatically updated when the text cursor is moved. |
| `KRichTextWidget::SupportDirection` | `0x8000000` | Action to change direction of text to Right-To-Left or Left-To-Right. |
| `KRichTextWidget::SupportHeading (since Qt 5.70)` | `0x10000000` | Action to make the current line a heading (up to six levels, corresponding to HTML h1...h6 tags). Displayed as a combobox when inserted into a toolbar. This is a KSelectAction. The status is automatically updated when the text cursor is moved. |
| `KRichTextWidget::FullSupport` | `0xffffffff` | Includes all above actions for full rich text support |

The `RichTextSupport` type is a typedef for `QFlags<RichTextSupportValues>. `It stores an OR combination of `RichTextSupportValues` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KRichTextWidget::KRichTextWidget(QWidget \**parent*) {#KRichTextWidget}

Constructor `parent` the parent widget

### \[explicit\] KRichTextWidget::KRichTextWidget(const QString &*text*, QWidget \**parent* = nullptr) {#KRichTextWidget-1}

Constructs a [KRichTextWidget](krichtextwidget.md) object

`text` The initial text of the text edit, which is interpreted as HTML.

`parent` The parent widget

### \[override virtual noexcept\] KRichTextWidget::~KRichTextWidget() {#dtor.KRichTextWidget}

Destructor

### \[virtual\] QList\<QAction \*\> KRichTextWidget::createActions() {#createActions}

Creates the actions and adds them to the given action collection.

Call this before calling setupGUI() in your application, but after calling [setRichTextSupport](krichtextwidget.md#setRichTextSupport)().

The XML file of your KXmlGuiWindow needs to have the action names in them, so that the actions actually appear in the menu and in the toolbars.

Below is a list of actions that are created, depending on the supported rich text subset set by [setRichTextSupport](krichtextwidget.md#setRichTextSupport)(). The list contains action names. Those names need to be the same in your XML file.

See the [KRichTextWidget::RichTextSupportValues](krichtextwidget.md#RichTextSupportValues-enum) enum documentation for a detailed explanation of each action.

| XML Name | [RichTextSupportValues](krichtextwidget.md#RichTextSupportValues-enum) flag |
| --- | --- |
| format\_text\_foreground\_color | [SupportTextForegroundColor](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_text\_background\_color | [SupportTextBackgroundColor](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_font\_family | [SupportFontFamily](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_font\_size | [SupportFontSize](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_text\_bold | [SupportBold](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_text\_italic | [SupportItalic](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_text\_underline | [SupportUnderline](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_text\_strikeout | [SupportStrikeOut](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_align\_left | [SupportAlignment](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_align\_center | [SupportAlignment](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_align\_right | [SupportAlignment](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_align\_justify | [SupportAlignment](krichtextwidget.md#RichTextSupportValues-enum) |
| direction\_ltr | [SupportDirection](krichtextwidget.md#RichTextSupportValues-enum) |
| direction\_rtl | [SupportDirection](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_list\_style | [SupportChangeListStyle](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_list\_indent\_more | [SupportIndentLists](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_list\_indent\_less | [SupportDedentLists](krichtextwidget.md#RichTextSupportValues-enum) |
| insert\_horizontal\_rule | [SupportRuleLine](krichtextwidget.md#RichTextSupportValues-enum) |
| manage\_link | [SupportHyperlinks](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_painter | [SupportFormatPainting](krichtextwidget.md#RichTextSupportValues-enum) |
| action\_to\_plain\_text | [SupportToPlainText](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_text\_subscript & format\_text\_superscript | [SupportSuperScriptAndSubScript](krichtextwidget.md#RichTextSupportValues-enum) |
| format\_heading\_level | [SupportHeading](krichtextwidget.md#RichTextSupportValues-enum) |

### KRichTextWidget::RichTextSupport KRichTextWidget::richTextSupport() const {#richTextSupport}

Returns the supported rich text subset available. Returns The supported subset.

> **Note:** Getter function for property richTextSupport.

*See also* [setRichTextSupport](krichtextwidget.md#setRichTextSupport)()

### \[slot\] void KRichTextWidget::setActionsEnabled(bool *enabled*) {#setActionsEnabled}

Disables or enables all of the actions created by [createActions](krichtextwidget.md#createActions)().

This may be useful in cases where rich text mode may be set on or off.

`enabled` Whether to enable or disable the actions.

### void KRichTextWidget::setRichTextSupport(const KRichTextWidget::RichTextSupport &*support*) {#setRichTextSupport}

Sets the supported rich text subset available.

The default is [KRichTextWidget::FullSupport](krichtextwidget.md#RichTextSupportValues-enum) and will be set in the constructor.

You need to call [createActions](krichtextwidget.md#createActions)() afterwards.

`support` The supported subset.

> **Note:** Setter function for property richTextSupport.

*See also* [richTextSupport](krichtextwidget.md#richTextSupport)()

### void KRichTextWidget::updateActionStates() {#updateActionStates}

Tells [KRichTextWidget](krichtextwidget.md) to update the state of the actions created by [createActions](krichtextwidget.md#createActions)().

This is normally automatically done, but there might be a few cases where you'll need to manually call this function.

Call this function only after calling [createActions](krichtextwidget.md#createActions)().
