---
title: "KMimeTypeEditor Namespace"
description: "This namespace provides a method for starting the file types editor."
---

# KMimeTypeEditor Namespace

This namespace provides a method for starting the file types editor. [More...](#details)

- **Header:** `#include <KMimeTypeEditor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### void KMimeTypeEditor::editMimeType(const QString &*mimeType*, QWidget \**widget*) {#editMimeType}

Starts the file types editor for a given MIME type.

Displays an error message if the mimetype editing tool (keditfiletype) couldn't be launched.

`mimeType` the MIME type to edit, e.g. "text/plain"

`widget` the parent widget
