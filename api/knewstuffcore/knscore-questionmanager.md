---
title: "KNSCore::QuestionManager Class"
description: "The central class handling Question redirection."
---

# KNSCore::QuestionManager Class

The central class handling Question redirection. [More...](#details)

- **Header:** `#include <QuestionManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](knscore-questionmanager-members.md)

## Detailed Description {#details}

This class is used to ensure that [KNSCore::Question](knscore-question.md) instances get redirected to the appropriate [KNSCore::QuestionListener](knscore-questionlistener.md) instances. It is a very dumb class which only ensures the listeners have somewhere to listen to, and the questions have somewhere to ask to be asked.
