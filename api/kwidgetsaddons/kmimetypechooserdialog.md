---
title: "KMimeTypeChooserDialog Class"
description: "A dialog to select MIME types from the list of available ones on the system."
---

# KMimeTypeChooserDialog Class

A dialog to select MIME types from the list of available ones on the system. [More...](#details)

- **Header:** `#include <KMimeTypeChooser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kmimetypechooserdialog-members.md)  
[Deprecated members](kmimetypechooserdialog-obsolete.md)

## Public Functions

- [KMimeTypeChooserDialog(const QString &title = QString(), const QString &text = QString(), const QStringList &selectedMimeTypes = QStringList(), const QString &defaultGroup = QString(), const QStringList &groupsToShow = QStringList(), int visuals = KMimeTypeChooser::Comments \| KMimeTypeChooser::Patterns \| KMimeTypeChooser::EditButton, QWidget \*parent = nullptr)](#KMimeTypeChooserDialog)
- [KMimeTypeChooser \*chooser()](#chooser)

## Detailed Description {#details}

This dialog embeds [KMimeTypeChooser](kmimetypechooser.md) widget, presenting a checkable tree list of MIME types, each with its associated icon, and optionally associated glob patterns (displayed in a separate column); also an optional Edit button to launch a MIME type editor to edit the selected MIME type.

Here is an example, using the dialog to set the text of two line edits with the list of MIME type names and glob patterns, respectively, of the MIME types that the user has selected:

```cpp
QLineEdit *leMimetypes = new QLineEdit();
QLineEdit *leGlobPatterns = new QLineEdit();
[...]
QString textLine = i18n("Select MIME types");
QStringList mimeList = QStringList::split(QRegularExpression("\\s*;\\s*"), leMimetypes->text());
KMimeTypeChooserDialog dlg(i18n("Select MIME Types"), textLine, mimeList, "text", this);
if (dlg.exec() == QDialog::Accepted) {
    leMimetypes->setText(dlg.chooser()->mimeTypes().join(";"));
    leGlobPatterns->setText(dlg.chooser()->patterns().join(";"));
}
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KMimeTypeChooserDialog::KMimeTypeChooserDialog(const QString &*title* = QString(), const QString &*text* = QString(), const QStringList &*selectedMimeTypes* = QStringList(), const QString &*defaultGroup* = QString(), const QStringList &*groupsToShow* = QStringList(), int *visuals* = KMimeTypeChooser::Comments \| KMimeTypeChooser::Patterns \| KMimeTypeChooser::EditButton, QWidget \**parent* = nullptr) {#KMimeTypeChooserDialog}

Create a [KMimeTypeChooser](kmimetypechooser.md) dialog.

`title` The title of the dialog

`text` A plain text line to display above the list

`selectedMimeTypes` A list of MIME type names, these will be initially selected in the list, provided they exist

`visuals` OR'd KMimetypeChooser::Visuals enum values to to set whether to show the MIME type comment and glob patterns columns and an Edit button, respectively, or not

`defaultGroup` The group (e.g. "text") to expand in the treeview when no groups are selected. If not provided, no group is expanded by default If `groupsToShow` is provided and it doesn't include `defaultGroup`, this parameter is ignored

`groupsToShow` A list of MIME type groups to show. If empty, all groups are shown

`parent` The parent widget to use

### KMimeTypeChooser \*KMimeTypeChooserDialog::chooser() {#chooser}

Returns a pointer to the [KMimeTypeChooser](kmimetypechooser.md) widget
