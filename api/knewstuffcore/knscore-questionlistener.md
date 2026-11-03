---
title: "KNSCore::QuestionListener Class"
description: "Implementation-side handler class for questions sent from KNewStuffCore."
---

# KNSCore::QuestionListener Class

Implementation-side handler class for questions sent from [KNewStuffCore](knewstuffcore-module.md). [More...](#details)

- **Header:** `#include <QuestionListener>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](knscore-questionlistener-members.md)

## Detailed Description {#details}

When implementing anything on top of [KNewStuffCore](knewstuffcore-module.md), you will need to be able to react to questions asked from inside the framework. This is done by creating an instance of a [QuestionListener](knscore-questionlistener.md), and reacting to any calls to the askQuestion slot, which you must extend and implement. Two examples of this exist, in the form of the KNS3::WidgetQuestionListener and KNewStuffQuick::QuickQuestionListener and should you need to create your own, take inspiration from them.
