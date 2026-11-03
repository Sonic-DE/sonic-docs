---
title: "Syndication::DataRetriever Class"
description: "Abstract baseclass for all data retriever classes."
---

# Syndication::DataRetriever Class

Abstract baseclass for all data retriever classes. [More...](#details)

- **Header:** `#include <Syndication/DataRetriever>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](syndication-dataretriever-members.md)

## Public Functions

- [DataRetriever()](#DataRetriever)
- [void abort()](#abort)
- [int errorCode() const](#errorCode)
- [void retrieveData(const QUrl &url)](#retrieveData)

## Signals

- [void dataRetrieved(const QByteArray &data, bool success)](#dataRetrieved)

## Detailed Description {#details}

Subclass this to add a new retrieval algorithm which can then be plugged into the RSS loader.

*See also* [Loader](syndication-loader.md)

## Member Function Documentation {#member-function-documentation}

### DataRetriever::DataRetriever() {#DataRetriever}

Default constructor.

### \[pure virtual\] void DataRetriever::abort() {#abort}

aborts the retrieval process.

### \[signal\] void DataRetriever::dataRetrieved(const QByteArray &*data*, bool *success*) {#dataRetrieved}

Emit this signal to tell the Loader class that the retrieval process was finished.

`data` Should contain the retrieved data and will get parsed by the Loader class.

`success` Indicates whether there were any problems during the retrieval process. Pass 'true' to indicate that everything went seamlessy, 'false' to tell the Loader that something went wrong and that the data parameter might contain no or invalid data.

### \[pure virtual\] int DataRetriever::errorCode() const {#errorCode}

Returns an error code which might give a more precise information about what went wrong in case the 'success' flag returned with the [dataRetrieved](syndication-dataretriever.md#dataRetrieved)() signal was 'false'.

Note that the meaning of the returned integer depends on the actual data retriever.

### \[pure virtual\] void DataRetriever::retrieveData(const QUrl &*url*) {#retrieveData}

Retrieve data from the given URL.

This method is supposed to get reimplemented by subclasses. It will be called by the Loader class in case it needs to retrieve the data.

`url` the URL to retrieve data from

*See also* [Loader::loadFrom](syndication-loader.md#loadFrom)()
