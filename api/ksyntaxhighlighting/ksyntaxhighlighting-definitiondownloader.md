---
title: "KSyntaxHighlighting::DefinitionDownloader Class"
description: "Helper class to download definition file updates."
---

# KSyntaxHighlighting::DefinitionDownloader Class

Helper class to download definition file updates. [More...](#details)

- **Header:** `#include <KSyntaxHighlighting/DefinitionDownloader>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting)`  
  `target_link_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ksyntaxhighlighting-definitiondownloader-members.md)

## Public Functions

- [DefinitionDownloader(KSyntaxHighlighting::Repository \*repo, QObject \*parent = nullptr)](#DefinitionDownloader)
- [void start()](#start)

## Signals

- [void done()](#done)
- [void informationMessage(const QString &msg)](#informationMessage)

## Detailed Description {#details}

With the [DefinitionDownloader](ksyntaxhighlighting-definitiondownloader.md) you can download new and update existing syntax highlighting definition files (xml files).

An example that updates the highlighting Definition%s and prints the current update progress to the console may look as follows:

```cpp
auto downloader = new DefinitionDownloader(repo); // repo is a pointer to a Repository

// print update progress to console
QObject::connect(downloader, &DefinitionDownloader::informationMessage, [](const QString &msg) {
    std::cout << qPrintable(msg) << std::endl;
});

// connect to signal done to delete the downloader later
QObject::connect(downloader, &DefinitionDownloader::done,
                 downloader, &DefinitionDownloader::deleteLater);
downloader->start();
```

*See also* [Repository](ksyntaxhighlighting-repository.md), [Definition](ksyntaxhighlighting-definition.md)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] DefinitionDownloader::DefinitionDownloader(KSyntaxHighlighting::Repository \**repo*, QObject \**parent* = nullptr) {#DefinitionDownloader}

Constructor. The Repository `repo` is used as reference to compare the versions of the existing Definition%s with the ones that are available online.

Optionally, `parent` is a pointer to the owner of this instance.

### \[signal\] void DefinitionDownloader::done() {#done}

This signal is emitted when there are no pending downloads anymore.

### \[signal\] void DefinitionDownloader::informationMessage(const QString &*msg*) {#informationMessage}

Prints the information about the current state of the definition files. If all files are up-to-date, this signal is emitted informing you that all highlighting files are up-to-date. If there are updates, this signal is emitted for each update being downloaded.

### void DefinitionDownloader::start() {#start}

Starts the update procedure. Once no more updates are available (i.e. either the local definition files are up-to-date, or all updates have been downloaded), the signal [done](ksyntaxhighlighting-definitiondownloader.md#done)() is emitted.

During the update process, the signal [informationMessage](ksyntaxhighlighting-definitiondownloader.md#informationMessage)() can be used to display the current update progress to the user.

*See also* [done](ksyntaxhighlighting-definitiondownloader.md#done)(), [informationMessage](ksyntaxhighlighting-definitiondownloader.md#informationMessage)()
