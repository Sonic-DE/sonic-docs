---
title: "SelectableLabel QML Type"
description: "This is a label which supports text selection."
---

# SelectableLabel QML Type

This is a label which supports text selection. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Control](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html)

## Detailed Description {#details}

The label uses [TextEdit](https://doc.qt.io/qt-6/qml-qtquick-textedit.html) component, which is wrapped inside a Control component.

Example usage:

```cpp
Kirigami.SelectableLabel {
    text: "Label"
}
```

*See also* [https://bugreports.qt.io/browse/QTBUG-14077](https://bugreports.qt.io/browse/QTBUG-14077)

## Property Documentation {#property-documentation}

### activeFocusOnPress : alias {#activeFocusOnPress-prop}

### baseUrl : alias {#baseUrl-prop}

### \[read-only\] canPaste : alias {#canPaste-prop}

### \[read-only\] canRedo : alias {#canRedo-prop}

### \[read-only\] canUndo : alias {#canUndo-prop}

### color : alias {#color-prop}

### \[read-only\] contentHeight : alias {#contentHeight-prop}

### \[read-only\] contentWidth : alias {#contentWidth-prop}

### cursorDelegate : alias {#cursorDelegate-prop}

### cursorPosition : alias {#cursorPosition-prop}

### \[read-only\] cursorRectangle : alias {#cursorRectangle-prop}

### \[read-only\] cursorSelection : alias {#cursorSelection-prop}

### cursorShape : var {#cursorShape-prop}

### cursorVisible : alias {#cursorVisible-prop}

### \[read-only\] effectiveHorizontalAlignment : alias {#effectiveHorizontalAlignment-prop}

### horizontalAlignment : alias {#horizontalAlignment-prop}

### \[read-only\] hoveredLink : alias {#hoveredLink-prop}

### \[read-only\] inputMethodComposing : alias {#inputMethodComposing-prop}

### inputMethodHints : alias {#inputMethodHints-prop}

### \[read-only\] length : alias {#length-prop}

### \[read-only\] lineCount : alias {#lineCount-prop}

### mouseSelectionMode : alias {#mouseSelectionMode-prop}

### overwriteMode : alias {#overwriteMode-prop}

### persistentSelection : alias {#persistentSelection-prop}

### \[read-only\] preeditText : alias {#preeditText-prop}

### readOnly : alias {#readOnly-prop}

### renderType : alias {#renderType-prop}

### selectByKeyboard : alias {#selectByKeyboard-prop}

### selectByMouse : alias {#selectByMouse-prop}

### \[read-only\] selectedText : alias {#selectedText-prop}

### selectedTextColor : alias {#selectedTextColor-prop}

### selectionColor : alias {#selectionColor-prop}

### \[read-only\] selectionEnd : alias {#selectionEnd-prop}

### \[read-only\] selectionStart : alias {#selectionStart-prop}

### tabStopDistance : alias {#tabStopDistance-prop}

### text : alias {#text-prop}

### \[read-only\] textDocument : alias {#textDocument-prop}

### textFormat : alias {#textFormat-prop}

### textMargin : alias {#textMargin-prop}

### verticalAlignment : alias {#verticalAlignment-prop}

### wrapMode : alias {#wrapMode-prop}

## Signal Documentation {#signal-documentation}

### clicked() {#clicked-signal}

> **Note:** The corresponding handler is `onClicked`.

### editingFinished() {#editingFinished-signal}

> **Note:** The corresponding handler is `onEditingFinished`.

### linkActivated(string *link*) {#linkActivated-signal}

> **Note:** The corresponding handler is `onLinkActivated`.

### linkHovered(string *link*) {#linkHovered-signal}

> **Note:** The corresponding handler is `onLinkHovered`.
