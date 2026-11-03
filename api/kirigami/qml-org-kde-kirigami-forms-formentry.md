---
title: "FormEntry QML Type"
description: "The base type of all Form entries. This type was introduced in Qt 6.24."
---

# FormEntry QML Type

The base type of all Form entries. This type was introduced in Qt 6.24. [More...](#details)

- Import Statement: import org.kde.kirigami.forms
- Since: Qt 6.24
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)
- Inherited By: [FormAction](qml-org-kde-kirigami-forms-formaction.md)

## Detailed Description {#details}

This element should always be positioned in a [FormGroup](qml-org-kde-kirigami-forms-formgroup.md). It is The base for all the items livinging in a Form and will take care of common styling and behaviors, like positioning of titles and subtitles, background and what happens when the item is clicked even outside the [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop).

Example usage:

```qml
import QtQuick.Controls as QQC
import org.kde.kirigami as Kirigami

Kirigami.Form {
  Kirigami.FormGroup {
      title: "Global Settings"
      Kirigami.FormEntry {
          contentItem: QQC.CheckBox {
              text: "Show Sidebar"
          }
      }
      Kirigami.FormEntry {
          contentItem: QQC.CheckBox {
              text: "Auto Save"
          }
      }
  }
  Kirigami.FormGroup {
      title: "Theme Options"
      Kirigami.FormEntry {
          title: "Colors"
          contentItem: QQC.CheckBox {
              text: "Dark Theme"
          }
      }
      Kirigami.FormSeparator {}
      Kirigami.FormEntry {
          contentItem: QQC.CheckBox {
              text: "High Contrast"
          }
      }
      ...
  }
}
```

The form entry will contain a main central [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop), with optional title, subtitle, and leading and trailing items, with the following layout:

*See also* [Form](qml-org-kde-kirigami-forms-form.md), [FormGroup](qml-org-kde-kirigami-forms-formgroup.md)

## Property Documentation {#property-documentation}

### clickEnabled : bool {#clickEnabled-prop}

Make the whole entry behave like a button

When true, clicking anywhere on this will emit the clicked signal. Depending on contentITem, if it's a clickable item itself, the click will be passed to it: for instance if [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop) is a [CheckBox](https://doc.qt.io/qt-6/qml-qtquick-controls-checkbox.html), clicking anywhere, even outside the checkbox will toggle the [CheckBox](https://doc.qt.io/qt-6/qml-qtquick-controls-checkbox.html) checked status.

### contentItem : Item {#contentItem-prop}

The main contents of this entry.

The contentItem is what contains the main contents of the entry, which are usually a simple Control such as a [CheckBox](https://doc.qt.io/qt-6/qml-qtquick-controls-checkbox.html), a [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html) and so on. If is needed to have more than one control, set a layout as contentItem, such as a [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html), GridLAyout and so on.

### fullWidth : bool {#fullWidth-prop}

Make sure the [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop) will always take the full width

When true, there will never be a label laid out on the left of the [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop). If a title is set, it will always be on top

### leadingItems : list\<Item\> {#leadingItems-prop}

Items to be positioned before the [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop)

a list of items to be laid out before the [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop) (at the left on LTR locales) for instance a big icon, that will cover the cumulative height of the title, [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop) and subtitle.

### subtitle : string {#subtitle-prop}

Extra subtitle.

If set a subtitle (potentially on multiple lines) will be displayed under the [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop). Use this for form entries with a more technical meaning that need more explanation or entries that contain a potentially dangerous action.

### title : string {#title-prop}

Entry title.

If set, a title will be displayed nearby the [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop), either on top or on the left, Depending from the style or form factor. Use this when the [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop) appearance doesn't provide enough explanation on what it does.

### trailingItems : list\<Item\> {#trailingItems-prop}

Items to be positioned after the [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop)

a list of items to be laid out after the [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop) (at the right on LTR locales) for instance a [ContextualHelpButton](qml-org-kde-kirigami-contextualhelpbutton.md), that will cover the cumulative height of the title, [contentItem](qml-org-kde-kirigami-forms-formentry.md#contentItem-prop) and subtitle.

## Signal Documentation {#signal-documentation}

### clicked() {#clicked-signal}

Emitted when the user clicks or taps over this Entry.

> **Note:** The corresponding handler is `onClicked`.
