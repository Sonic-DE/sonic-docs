---
title: "DocBook2Markdown::Converter Class"
description: "Create documentation from DocBook."
---

# DocBook2Markdown::Converter Class

Create documentation from DocBook. [More...](#details)

- **Header:** `#include <Converter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DocTools)`  
  `target_link_libraries(mytarget PRIVATE KF6::DocTools)`

[List of all members, including inherited members](docbook2markdown-converter-members.md)

## Detailed Description {#details}

Converts QDoc's DocBook output (one article per page) into Markdown for the Winter docs plugin.

Class pages get the Qt reference layout: title, brief, requirements, summary sections rebuilt from the member documentation (QDoc's DocBook writer omits them), Detailed Description and member documentation, with explicit heading anchors. Deprecated members move to their own page.
