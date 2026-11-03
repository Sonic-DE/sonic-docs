---
title: "KFontChooserDialog Class"
description: "A font selection dialog."
---

# KFontChooserDialog Class

A font selection dialog. [More...](#details)

- **Header:** `#include <KFontChooserDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kfontchooserdialog-members.md)

## Public Functions

- [KFontChooserDialog(const KFontChooser::DisplayFlags &flags = KFontChooser::NoDisplayFlags, QWidget \*parent = nullptr)](#KFontChooserDialog)
- [QFont font() const](#font)
- [void setFont(const QFont &font, bool onlyFixed = false)](#setFont)

## Signals

- [void fontSelected(const QFont &font)](#fontSelected)

## Static Public Members

- [int getFont(QFont &theFont, const KFontChooser::DisplayFlags &flags = KFontChooser::NoDisplayFlags, QWidget \*parent = nullptr)](#getFont)
- [int getFontDiff(QFont &theFont, KFontChooser::FontDiffFlags &diffFlags, const KFontChooser::DisplayFlags &flags = KFontChooser::NoDisplayFlags, QWidget \*parent = nullptr)](#getFontDiff)

## Detailed Description {#details}

The [KFontChooserDialog](kfontchooserdialog.md) provides a dialog for interactive font selection. It is basically a thin wrapper around the [KFontChooser](kfontchooser.md) widget (the latter can also be used standalone). In most cases, the simplest use of this class is the static method [KFontChooserDialog::getFont](kfontchooserdialog.md#getFont)(), which shows the dialog, allows the user to select a font, and returns when the dialog is closed.

Features offered by [KFontChooserDialog](kfontchooserdialog.md)/[KFontChooser](kfontchooser.md):

- The ability to set decimal font sizes (e.g. "12.1")
- When selecting an initial font, if the styleName property of that font isn't set, the dialog will try and select the correct font style from the styles list
- The ability to set multiple fonts at once, for an example of this functionality see "Adjust All Fonts" in the Fonts KCM in Systemsettings; and you can change the font family, style or size separately
- Discarding the styleName property when closing the dialog for "Regular" font styles, since it doesn't make sense to set that property for such fonts and this allows setBold(true) to work correctly for more details see: https://bugreports.qt.io/browse/QTBUG-63792 https://bugs.kde.org/show_bug.cgi?id=378523

Example, using the static [getFont](kfontchooserdialog.md#getFont)() method:

```cpp
QFont myFont;
int result = KFontChooserDialog::getFont(myFont);
if (result == QDialog::Accepted) {
      ...
}
```

Another example, this time showing the dialog with [show](https://doc.qt.io/qt-6/qwidget.html#show)() (or [open](https://doc.qt.io/qt-6/qdialog.html#open)()):

```cpp
KFontChooserDialog *fontDlg = new KFontChooserDialog(KFontChooser::NoDisplayFlags, this);
// Delete the dialog when it's closed
fontDlg->setAttribute(Qt::WA_DeleteOnClose);

connect(fontDlg, &QDialog::accepted, this, [fontDlg]() {
    // Get the selected font via fontDlg->font() and apply it, save it to
    // the settings... etc.
});

fontDlg->show();
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFontChooserDialog::KFontChooserDialog(const KFontChooser::DisplayFlags &*flags* = KFontChooser::NoDisplayFlags, QWidget \**parent* = nullptr) {#KFontChooserDialog}

Constructs a font selection dialog.

`flags` flags to define how the font chooser is displayed

`parent` parent widget of the dialog, if any, the dialog will be centered relative to it

### QFont KFontChooserDialog::font() const {#font}

Returns the currently selected font in the dialog

*See also* [setFont](kfontchooserdialog.md#setFont)()

### \[signal\] void KFontChooserDialog::fontSelected(const QFont &*font*) {#fontSelected}

Emitted whenever the currently selected font changes. Connect to this to monitor the font as it is selected if you are not running modal.

### \[static\] int KFontChooserDialog::getFont(QFont &*theFont*, const KFontChooser::DisplayFlags &*flags* = KFontChooser::NoDisplayFlags, QWidget \**parent* = nullptr) {#getFont}

Creates a modal font dialog, lets the user choose a font, and returns when the dialog is closed.

`theFont` a reference to the font to write the chosen font into

`flags` flags to define how the font chooser is displayed

`parent` parent widget of the dialog, if any, the dialog will be centered relative to it

Returns [QDialog::result](https://doc.qt.io/qt-6/qdialog.html#result)()

### \[static\] int KFontChooserDialog::getFontDiff(QFont &*theFont*, KFontChooser::FontDiffFlags &*diffFlags*, const KFontChooser::DisplayFlags &*flags* = KFontChooser::NoDisplayFlags, QWidget \**parent* = nullptr) {#getFontDiff}

Creates a modal font difference dialog, lets the user choose a selection of changes that should be made to a set of fonts, and returns when the dialog is closed. Useful for choosing slight adjustments to the font set when the user would otherwise have to manually edit a number of fonts.

`theFont` a reference to the font to write the chosen font into

`flags` flags to define how the font chooser is displayed

`diffFlags` a reference to the integer bitmask into which the chosen difference selection bitmask should be written. Check the bitmask afterwards like:

```cpp
if ( diffFlags & KFontChooser::FontDiffFamily )  {
    [...]
}
if ( diffFlags & KFontChooser::FontDiffStyle ) {
    [...]
}
if ( diffFlags & KFontChooser::FontDiffSize ) {
    [...]
}
```

`parent` parent widget of the dialog, if any, the dialog will be centered relative to it

Returns [QDialog::result](https://doc.qt.io/qt-6/qdialog.html#result)()

### void KFontChooserDialog::setFont(const QFont &*font*, bool *onlyFixed* = false) {#setFont}

Sets the currently selected font in the dialog.

`font` the font to select

`onlyFixed` if `true`, the font list will show only fixed width (monospace) fonts, otherwise all available fonts are shown

*See also* [font](kfontchooserdialog.md#font)()
