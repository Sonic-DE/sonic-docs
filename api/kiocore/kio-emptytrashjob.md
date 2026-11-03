---
title: "KIO::EmptyTrashJob Class"
description: "Network transparent access to files and data."
---

# KIO::EmptyTrashJob Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KIO/EmptyTrashJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::SimpleJob](kio-simplejob.md)

[List of all members, including inherited members](kio-emptytrashjob-members.md)

## Detailed Description {#details}

A KIO job for emptying the trash

*See also* [KIO::trash()](kio-index.md), [KIO::restoreFromTrash()](kio-index.md)

## Related Non-Members {#related-non-members}

### KIO::EmptyTrashJob \*emptyTrash() {#emptyTrash}

Empties the trash.

Returns a pointer to the job handling the operation.
