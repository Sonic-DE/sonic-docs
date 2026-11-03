---
title: "KQuickIconProvider Class"
description: "Class which exposes the KIcon functioality to QML."
---

# KQuickIconProvider Class

Class which exposes the KIcon\* functioality to QML. [More...](#details)

- **Header:** `#include <KQuickIconProvider>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS IconThemes)`  
  `target_link_libraries(mytarget PRIVATE KF6::IconThemes)`

[List of all members, including inherited members](kquickiconprovider-members.md)

## Detailed Description {#details}

For dependency reasons, this is a header-only class.

This needs to be registered in the engine using the following code:

```cpp
engine->addImageProvider(QStringLiteral("icon"), new KQuickIconProvider);
```
