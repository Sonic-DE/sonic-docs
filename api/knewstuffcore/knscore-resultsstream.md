---
title: "KNSCore::ResultsStream Class"
description: "The ResultsStream is returned by EngineBase::search. It is used to communicate the different entries in response to a request using the signal entriesFound. This class was introduced in Qt 6.0."
---

# KNSCore::ResultsStream Class

The [ResultsStream](knscore-resultsstream.md) is returned by EngineBase::search. It is used to communicate the different entries in response to a request using the signal `entriesFound`. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <ResultsStream>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](knscore-resultsstream-members.md)

## Detailed Description {#details}

Initially the stream will communicate the entries part of the page as specified in the request. Further pages can be requested using `fetchMore`.

Once we have reached the end of the requested stream, the object shall emit `finished` and delete itself.
