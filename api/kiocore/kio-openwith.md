---
title: "KIO::OpenWith Class"
description: "Core class for open with style dialog handling."
---

# KIO::OpenWith Class

Core class for open with style dialog handling. [More...](#details)

- **Header:** `#include <KIO/OpenWith>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kio-openwith-members.md)

## Static Public Members

- [KIO::OpenWith::AcceptResult accept(KService::Ptr &service, const QString &typedExec, bool remember, const QString &mimeType, bool openInTerminal, bool lingerTerminal, bool saveNewApps)](#accept)

## Detailed Description {#details}

This only implements core functionality. For an actual open with implementation see [KOpenWithDialog](../kiowidgets/kopenwithdialog.md). For a way to trigger open with dialogs see OpenUrlJob and OpenWithHandlerInterface.

## Member Function Documentation {#member-function-documentation}

### \[static\] KIO::OpenWith::AcceptResult OpenWith::accept(KService::Ptr &*service*, const QString &*typedExec*, bool *remember*, const QString &*mimeType*, bool *openInTerminal*, bool *lingerTerminal*, bool *saveNewApps*) {#accept}

Accept an openwith request with the provided arguments as context. This function may have side effects to do with accepting, such as setting the default application for the mimetype if `remember` is true.

Returns an AcceptResult
