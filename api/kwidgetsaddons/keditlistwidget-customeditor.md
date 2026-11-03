---
title: "KEditListWidget::CustomEditor Class"
description: "Custom editor class."
---

# KEditListWidget::CustomEditor Class

Custom editor class. [More...](#details)

- **Header:** `#include <KEditListWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

[List of all members, including inherited members](keditlistwidget-customeditor-members.md)

## Public Functions

- [CustomEditor()](#CustomEditor)
- [QLineEdit \*lineEdit() const](#lineEdit)
- [QWidget \*representationWidget() const](#representationWidget)
- [void setLineEdit(QLineEdit \*edit)](#setLineEdit)
- [void setRepresentationWidget(QWidget \*repWidget)](#setRepresentationWidget)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### CustomEditor::CustomEditor() {#CustomEditor}

### \[virtual\] QLineEdit \*CustomEditor::lineEdit() const {#lineEdit}

*See also* [setLineEdit](keditlistwidget-customeditor.md#setLineEdit)()

### \[virtual\] QWidget \*CustomEditor::representationWidget() const {#representationWidget}

*See also* [setRepresentationWidget](keditlistwidget-customeditor.md#setRepresentationWidget)()

### void CustomEditor::setLineEdit(QLineEdit \**edit*) {#setLineEdit}

*See also* [lineEdit](keditlistwidget-customeditor.md#lineEdit)()

### void CustomEditor::setRepresentationWidget(QWidget \**repWidget*) {#setRepresentationWidget}

*See also* [representationWidget](keditlistwidget-customeditor.md#representationWidget)()
