---
title: "KIO::DesktopExecParser Class"
description: "Parses the Exec= line from a .desktop file, and process all the '%' placeholders, e.g. handling URLs vs local files."
---

# KIO::DesktopExecParser Class

Parses the Exec= line from a .desktop file, and process all the '%' placeholders, e.g. handling URLs vs local files. [More...](#details)

- **Header:** `#include <KIO/DesktopExecParser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kio-desktopexecparser-members.md)

## Public Functions

- [DesktopExecParser(const KService &service, const QList\<QUrl\> &urls)](#DesktopExecParser)
- [QString errorMessage() const](#errorMessage)
- [QStringList resultingArguments() const](#resultingArguments)
- [void setSuggestedFileName(const QString &suggestedFileName)](#setSuggestedFileName)
- [void setUrlsAreTempFiles(bool tempFiles)](#setUrlsAreTempFiles)

## Static Public Members

- [QString executableName(const QString &execLine)](#executableName)
- [QString executablePath(const QString &execLine)](#executablePath)
- [bool hasSchemeHandler(const QUrl &url)](#hasSchemeHandler)
- [bool isProtocolInSupportedList(const QUrl &url, const QStringList &supportedProtocols)](#isProtocolInSupportedList)
- [QStringList supportedProtocols(const KService &service)](#supportedProtocols)

## Detailed Description {#details}

The processing actually happens when calling [resultingArguments](kio-desktopexecparser.md#resultingArguments)(), after setting everything up.

## Member Function Documentation {#member-function-documentation}

### DesktopExecParser::DesktopExecParser(const KService &*service*, const QList\<QUrl\> &*urls*) {#DesktopExecParser}

Creates a parser for a desktop file Exec line.

`service` the service to extract information from. The [KService](../kservice/kservice.md) instance must remain alive as long as the parser is alive.

`urls` The urls the service should open.

### QString DesktopExecParser::errorMessage() const {#errorMessage}

Returns an error message for when [resultingArguments](kio-desktopexecparser.md#resultingArguments)() returns an empty list

### \[static\] QString DesktopExecParser::executableName(const QString &*execLine*) {#executableName}

Given a full command line (e.g. the Exec= line from a .desktop file), extract the name of the executable being run (removing the path, if specified).

`execLine` the full command line

Returns the name of the executable to run, example: "ls"

### \[static\] QString DesktopExecParser::executablePath(const QString &*execLine*) {#executablePath}

Given a full command line (e.g. the Exec= line from a .desktop file), extract the name of the executable being run, including its full path, if specified.

`execLine` the full command line

Returns the name of the executable to run, example: "/bin/ls"

### \[static\] bool DesktopExecParser::hasSchemeHandler(const QUrl &*url*) {#hasSchemeHandler}

Returns true if `protocol` should be opened by a "handler" application, i.e. an application associated to \_all\_ URLs using this protocol (a.k.a. scheme).

### \[static\] bool DesktopExecParser::isProtocolInSupportedList(const QUrl &*url*, const QStringList &*supportedProtocols*) {#isProtocolInSupportedList}

Returns true if `protocol` is in the list of protocols returned by [supportedProtocols](kio-desktopexecparser.md#supportedProtocols)(). The only reason for this method is the special handling of "KIO".

### QStringList DesktopExecParser::resultingArguments() const {#resultingArguments}

Returns a list of arguments suitable for [QProcess](https://doc.qt.io/qt-6/qprocess.html). Returns an empty list on error, check [errorMessage](kio-desktopexecparser.md#errorMessage)() for details.

### void DesktopExecParser::setSuggestedFileName(const QString &*suggestedFileName*) {#setSuggestedFileName}

Sets the file name to use in the case of downloading the file to a tempfile in order to give to a non-url-aware application. Some apps rely on the extension to determine the MIME type of the file. Usually the file name comes from the URL, but in the case of the HTTP Content-Disposition header, we need to override the file name.

### void DesktopExecParser::setUrlsAreTempFiles(bool *tempFiles*) {#setUrlsAreTempFiles}

If `tempFiles` is set to true and the urls given to the constructor are local files, they will be deleted when the application exits.

### \[static\] QStringList DesktopExecParser::supportedProtocols(const KService &*service*) {#supportedProtocols}

Returns the list of protocols which the application `service` supports. This can be a list of actual protocol names, or just "KIO" for KIO-based apps.
