---
title: "KUserTimestamp Namespace"
description: "Access to the windowing system.."
---

# KUserTimestamp Namespace

Access to the windowing system.. [More...](#details)

- **Header:** `#include <KUserTimestamp>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### void KUserTimestamp::updateUserTimestamp(unsigned long *time* = 0) {#updateUserTimestamp}

Updates the last user action timestamp to the given time, or to the current time, if 0 is given. Do not use unless you're really sure what you're doing. Consult focus stealing prevention section in kdebase/kwin/README.

### unsigned long KUserTimestamp::userTimestamp() {#userTimestamp}

Returns the last user action timestamp or 0 if no user activity has taken place yet.

*See also* updateuserTimestamp
