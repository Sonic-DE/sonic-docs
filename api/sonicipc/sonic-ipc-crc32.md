---
title: "Sonic::Ipc::Crc32 Namespace"
description: "The checksum of frame payloads."
---

# Sonic::Ipc::Crc32 Namespace

The checksum of frame payloads. [More...](#details)

- **Header:** `#include <Sonic/Ipc/Crc32>`
- **CMake:** `find_package(SonicIpc REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::Ipc)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### quint32 Crc32::compute(QByteArrayView *data*) {#compute}

The CRC-32 of `data` as in IEEE 802.3: reflected, polynomial 0xEDB88320, initial value and final XOR 0xFFFFFFFF. Qt's [qChecksum](https://doc.qt.io/qt-6/qbytearray.html#qChecksum) only offers CRC-16.
