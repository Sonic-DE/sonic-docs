---
title: "KRichTextEdit Class"
description: "A KTextEdit that supports both rich text and plain text modes."
---

# KRichTextEdit Class

A [KTextEdit](ktextedit.md) that supports both rich text and plain text modes. [More...](#details)

- **Header:** `#include <KRichTextEdit>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextWidgets)`
- **Inherits:** [KTextEdit](ktextedit.md)
- **Inherited By:** [KRichTextWidget](krichtextwidget.md)

[List of all members, including inherited members](krichtextedit-members.md)

## Public Types

- [enum KRichTextEdit::Mode](#Mode-enum)

## Public Functions

- [KRichTextEdit(QWidget \*parent = nullptr)](#KRichTextEdit)
- [KRichTextEdit(const QString &text, QWidget \*parent = nullptr)](#KRichTextEdit-1)
- [bool canDedentList() const](#canDedentList)
- [bool canIndentList() const](#canIndentList)
- [QString currentLinkText() const](#currentLinkText)
- [QString currentLinkUrl() const](#currentLinkUrl)
- [void enableRichTextMode()](#enableRichTextMode)
- [void selectLinkText() const](#selectLinkText)
- [void selectLinkText(QTextCursor \*cursor) const](#selectLinkText-1)
- [void setTextOrHtml(const QString &text)](#setTextOrHtml)
- [KRichTextEdit::Mode textMode() const](#textMode)
- [QString textOrHtml() const](#textOrHtml)
- [void updateLink(const QString &linkUrl, const QString &linkText)](#updateLink)

## Public Slots

- [void alignCenter()](#alignCenter)
- [void alignJustify()](#alignJustify)
- [void alignLeft()](#alignLeft)
- [void alignRight()](#alignRight)
- [void indentListLess()](#indentListLess)
- [void indentListMore()](#indentListMore)
- [void insertHorizontalRule()](#insertHorizontalRule)
- [void insertPlainTextImplementation()](#insertPlainTextImplementation)
- [void makeLeftToRight()](#makeLeftToRight)
- [void makeRightToLeft()](#makeRightToLeft)
- [void setFont(const QFont &font)](#setFont)
- [void setFontFamily(const QString &fontFamily)](#setFontFamily)
- [void setFontSize(int size)](#setFontSize)
- [void setHeadingLevel(int level)](#setHeadingLevel)
- [void setListStyle(int \_styleIndex)](#setListStyle)
- [void setTextBackgroundColor(const QColor &color)](#setTextBackgroundColor)
- [void setTextBold(bool bold)](#setTextBold)
- [void setTextForegroundColor(const QColor &color)](#setTextForegroundColor)
- [void setTextItalic(bool italic)](#setTextItalic)
- [void setTextStrikeOut(bool strikeOut)](#setTextStrikeOut)
- [void setTextSubScript(bool subscript)](#setTextSubScript)
- [void setTextSuperScript(bool superscript)](#setTextSuperScript)
- [void setTextUnderline(bool underline)](#setTextUnderline)
- [void switchToPlainText()](#switchToPlainText)
- [QString toCleanHtml() const](#toCleanHtml)

## Signals

- [void textModeChanged(KRichTextEdit::Mode mode)](#textModeChanged)

## Detailed Description {#details}

The [KRichTextEdit](krichtextedit.md) class provides a widget to edit and display rich text.

It offers several additional rich text editing functions to [KTextEdit](ktextedit.md) and makes them easier to access including:

- Changing fonts, sizes.
- Font formatting, such as bold, underline, italic, foreground and background color.
- Paragraph alignment
- Ability to edit and remove hyperlinks
- Nested list handling
- Simple actions to insert tables. TODO

The [KRichTextEdit](krichtextedit.md) can be in two modes: Rich text mode and plain text mode. Calling functions which modify the format/style of the text will automatically enable the rich text mode. Rich text mode is sometimes also referred to as HTML mode.

Do not call [setAcceptRichText](https://doc.qt.io/qt-6/qtextedit.html#acceptRichText-prop)() or [acceptRichText](https://doc.qt.io/qt-6/qtextedit.html#acceptRichText-prop)() yourself. Instead simply connect to the slots which insert the rich text, use [switchToPlainText](krichtextedit.md#switchToPlainText)() or [enableRichTextMode](krichtextedit.md#enableRichTextMode)().

## Member Type Documentation {#member-type-documentation}

### enum KRichTextEdit::Mode {#Mode-enum}

The mode the edit widget is in.

| Constant | Value | Description |
| --- | --- | --- |
| `KRichTextEdit::Plain` | `0` | Plain text mode |
| `KRichTextEdit::Rich` | `1` | Rich text mode |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KRichTextEdit::KRichTextEdit(QWidget \**parent* = nullptr) {#KRichTextEdit}

Constructs a [KRichTextEdit](krichtextedit.md) object.

`parent` The parent widget

### \[explicit\] KRichTextEdit::KRichTextEdit(const QString &*text*, QWidget \**parent* = nullptr) {#KRichTextEdit-1}

Constructs a [KRichTextEdit](krichtextedit.md) object

`text` The initial text of the text edit, which is interpreted as HTML.

`parent` The parent widget

### \[slot\] void KRichTextEdit::alignCenter() {#alignCenter}

Sets the alignment of the current block to Centered

### \[slot\] void KRichTextEdit::alignJustify() {#alignJustify}

Sets the alignment of the current block to Justified

### \[slot\] void KRichTextEdit::alignLeft() {#alignLeft}

Sets the alignment of the current block to Left Aligned

### \[slot\] void KRichTextEdit::alignRight() {#alignRight}

Sets the alignment of the current block to Right Aligned

### bool KRichTextEdit::canDedentList() const {#canDedentList}

Returns true if the list item at the current position can be dedented.

*See also* [canIndentList](krichtextedit.md#canIndentList)

### bool KRichTextEdit::canIndentList() const {#canIndentList}

Returns true if the list item at the current position can be indented.

*See also* [canDedentList](krichtextedit.md#canDedentList)

### QString KRichTextEdit::currentLinkText() const {#currentLinkText}

Returns the text of the link at the current position or an empty string if the cursor is not on a link.

*See also* [currentLinkUrl](krichtextedit.md#currentLinkUrl)

### QString KRichTextEdit::currentLinkUrl() const {#currentLinkUrl}

Returns the URL target (href) of the link at the current position or an empty string if the cursor is not on a link.

*See also* [currentLinkText](krichtextedit.md#currentLinkText)

### void KRichTextEdit::enableRichTextMode() {#enableRichTextMode}

This enables rich text mode. Nothing is done except changing the internal mode and allowing rich text pastes.

### \[slot\] void KRichTextEdit::indentListLess() {#indentListLess}

Decreases the nesting level of the current block or selected blocks.

*See also* [canDedentList](krichtextedit.md#canDedentList)

### \[slot\] void KRichTextEdit::indentListMore() {#indentListMore}

Increases the nesting level of the current block or selected blocks.

*See also* [canIndentList](krichtextedit.md#canIndentList)

### \[slot\] void KRichTextEdit::insertHorizontalRule() {#insertHorizontalRule}

Inserts a horizontal rule below the current block.

### \[slot\] void KRichTextEdit::insertPlainTextImplementation() {#insertPlainTextImplementation}

Because of binary compatibility constraints, insertPlainText is not virtual. Therefore it must dynamically detect and call this slot.

### \[slot\] void KRichTextEdit::makeLeftToRight() {#makeLeftToRight}

Sets the direction of the current block to Left-To-Right

### \[slot\] void KRichTextEdit::makeRightToLeft() {#makeRightToLeft}

Sets the direction of the current block to Right-To-Left

### void KRichTextEdit::selectLinkText() const {#selectLinkText}

Convenience function to select the link text using the active cursor.

*See also* selectLinkText

### void KRichTextEdit::selectLinkText(QTextCursor \**cursor*) const {#selectLinkText-1}

If the cursor is on a link, sets the `cursor` to a selection of the text of the link. If the `cursor` is not on a link, selects the current word or existing selection.

`cursor` The cursor to use to select the text.

*See also* [updateLink](krichtextedit.md#updateLink)

### \[slot\] void KRichTextEdit::setFont(const QFont &*font*) {#setFont}

Sets the current word or selection to the font `font`

`font` the font of the text will be set to this font

### \[slot\] void KRichTextEdit::setFontFamily(const QString &*fontFamily*) {#setFontFamily}

Sets the current word or selection to the font family `fontFamily`

`fontFamily` The text's font family will be changed to this one

### \[slot\] void KRichTextEdit::setFontSize(int *size*) {#setFontSize}

Sets the current word or selection to the font size `size`

`size` The text's font will get this size

### \[slot\] void KRichTextEdit::setHeadingLevel(int *level*) {#setHeadingLevel}

Sets the heading level of a current block or selection

`level` Heading level (value should be between 0 and 6) (0 is "normal text", 1 is the largest heading, 6 is the smallest one)

### \[slot\] void KRichTextEdit::setListStyle(int *\_styleIndex*) {#setListStyle}

Sets the list style of the current list, or creates a new list using the current block. The `_styleindex` corresponds to the QTextListFormat::Style

`_styleIndex` The list will get this style

### \[slot\] void KRichTextEdit::setTextBackgroundColor(const QColor &*color*) {#setTextBackgroundColor}

Sets the background color of the current word or selection to `color`.

`color` The text will get this foreground color

### \[slot\] void KRichTextEdit::setTextBold(bool *bold*) {#setTextBold}

Toggles the bold formatting of the current word or selection at the current cursor position.

`bold` If true, the text will be set to bold

### \[slot\] void KRichTextEdit::setTextForegroundColor(const QColor &*color*) {#setTextForegroundColor}

Sets the foreground color of the current word or selection to `color`.

`color` The text will get this background color

### \[slot\] void KRichTextEdit::setTextItalic(bool *italic*) {#setTextItalic}

Toggles the italic formatting of the current word or selection at the current cursor position.

`italic` If true, the text will be set to italic

### void KRichTextEdit::setTextOrHtml(const QString &*text*) {#setTextOrHtml}

Replaces all the content of the text edit with the given string. If the string is in rich text format, the text is inserted as rich text, otherwise it is inserted as plain text.

`text` The text to insert

*See also* [textOrHtml](krichtextedit.md#textOrHtml)()

### \[slot\] void KRichTextEdit::setTextStrikeOut(bool *strikeOut*) {#setTextStrikeOut}

Toggles the strikeout formatting of the current word or selection at the current cursor position.

`strikeOut` If true, the text will be struck out

### \[slot\] void KRichTextEdit::setTextSubScript(bool *subscript*) {#setTextSubScript}

Toggles the subscript formatting of the current word or selection at the current cursor position.

`subscript` If true, the text will be set to subscript

### \[slot\] void KRichTextEdit::setTextSuperScript(bool *superscript*) {#setTextSuperScript}

Toggles the superscript formatting of the current word or selection at the current cursor position.

`superscript` If true, the text will be set to superscript

### \[slot\] void KRichTextEdit::setTextUnderline(bool *underline*) {#setTextUnderline}

Toggles the underline formatting of the current word or selection at the current cursor position.

`underline` If true, the text will be underlined

### \[slot\] void KRichTextEdit::switchToPlainText() {#switchToPlainText}

This will switch the editor to plain text mode. All rich text formatting will be destroyed.

### KRichTextEdit::Mode KRichTextEdit::textMode() const {#textMode}

Returns the current text mode

### \[signal\] void KRichTextEdit::textModeChanged(KRichTextEdit::Mode *mode*) {#textModeChanged}

Emitted whenever the text mode is changed.

`mode` The new text mode

### QString KRichTextEdit::textOrHtml() const {#textOrHtml}

Returns the plain text string if in plain text mode or the HTML code if in rich text mode. The text is not word-wrapped.

*See also* [setTextOrHtml](krichtextedit.md#setTextOrHtml)()

### \[slot\] QString KRichTextEdit::toCleanHtml() const {#toCleanHtml}

This will clean some of the bad html produced by the underlying [QTextEdit](https://doc.qt.io/qt-6/qtextedit.html) It walks over all lines and cleans up a bit. Should be improved to produce our own Html.

### void KRichTextEdit::updateLink(const QString &*linkUrl*, const QString &*linkText*) {#updateLink}

Replaces the current selection with a hyperlink with the link URL `linkUrl` and the link text `linkText`.

`linkUrl` The link will get this URL as href (target)

`linkText` The link will get this alternative text, which is the text displayed in the text edit.

*See also* [selectLinkText](krichtextedit.md#selectLinkText), [currentLinkUrl](krichtextedit.md#currentLinkUrl), [currentLinkText](krichtextedit.md#currentLinkText)
