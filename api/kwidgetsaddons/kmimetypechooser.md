---
title: "KMimeTypeChooser Class"
description: "This widget provides a checkable list of all available MIME types."
---

# KMimeTypeChooser Class

This widget provides a checkable list of all available MIME types. [More...](#details)

- **Header:** `#include <KMimeTypeChooser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kmimetypechooser-members.md)

## Public Types

- [enum KMimeTypeChooser::Visuals](#Visuals-enum)

## Public Functions

- [KMimeTypeChooser(const QString &text = QString(), const QStringList &selectedMimeTypes = QStringList(), const QString &defaultGroup = QString(), const QStringList &groupsToShow = QStringList(), int visuals = Comments \| Patterns \| EditButton, QWidget \*parent = nullptr)](#KMimeTypeChooser)
- [QStringList mimeTypes() const](#mimeTypes)
- [QStringList patterns() const](#patterns)

## Detailed Description {#details}

Presented as a treeview, with the MIME type comment and glob patterns as individual columns.

It allows users to edit a MIME type by launching a MIME type editor (if it's available on the system).

When the user clicks the OK button, a list of the selected MIME type names and associated glob patterns can be retrieved respectively; those lists can be used to populate a text line edit, or set a configuration entry... etc.

## Member Type Documentation {#member-type-documentation}

### enum KMimeTypeChooser::Visuals {#Visuals-enum}

Buttons and data for display.

| Constant | Value | Description |
| --- | --- | --- |
| `KMimeTypeChooser::Comments` | `1` | Show the MIME type comment (e.g. "HTML Document") in a column |
| `KMimeTypeChooser::Patterns` | `2` | Show the MIME types glob patterns (e.g. "\*.html;\*.htm") in a column |
| `KMimeTypeChooser::EditButton` | `4` | Show the "Edit" button, allowing to edit the selected type |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KMimeTypeChooser::KMimeTypeChooser(const QString &*text* = QString(), const QStringList &*selectedMimeTypes* = QStringList(), const QString &*defaultGroup* = QString(), const QStringList &*groupsToShow* = QStringList(), int *visuals* = Comments \| Patterns \| EditButton, QWidget \**parent* = nullptr) {#KMimeTypeChooser}

Create a new [KMimeTypeChooser](kmimetypechooser.md).

`text` A plain text line to display above the list

`selectedMimeTypes` A list of MIME type names, these will be initially selected in the list (provided they exist)

`visuals` OR'd KMimetypeChooser::Visuals enum values to to set whether to show the MIME type comment and glob patterns columns and an Edit button, respectively, or not

`defaultGroup` The group (e.g. "text") to expand in the treeview when no groups are selected. If not provided, no group is expanded by default. If `groupsToShow` is provided and it doesn't include `defaultGroup`, this parameter is ignored

`groupsToShow` a list of MIME type groups to show. If empty, all groups are shown

`parent` The parent widget to use

### QStringList KMimeTypeChooser::mimeTypes() const {#mimeTypes}

Returns a list of all selected MIME type names

### QStringList KMimeTypeChooser::patterns() const {#patterns}

Returns a list of the filename glob patterns associated with all selected MIME types
