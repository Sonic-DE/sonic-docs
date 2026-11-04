---
title: "KSafeStringError Namespace"
description: "Thread-safe variants of strerror that return different string types. This namespace was introduced in Qt 6.31."
---

# KSafeStringError Namespace

Thread-safe variants of strerror that return different string types. This namespace was introduced in Qt 6.31. [More...](#details)

- **Header:** `#include <KSafeStringError>`
- **Since:** Qt 6.31
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

## Detailed Description {#details}

The POSIX strerror is not thread-safe. strerror\_r has varying semantics. These wrappers provide a stable and thread-safe interface to the strerror functionality.

Whenever you get an errno-like value you can feed it into these functions and get a somewhat descriptive string back. Do not use the output as sole log message, it is fairly generic.

```cpp
auto fd = open("somefile", O_RDONLY | O_CLOEXEC);
if (::close(fd) == -1) {
    auto error = errno;
    qWarning() << "Failed to close file descriptor for somefile:" << KSafeStringError::strerror(error);
}
```

If output would be too long it gets truncated!

> **Warning:** This class is not available on Windows.

## Function Documentation {#function-documentation}

### const char \*KSafeStringError::strerror(int *error*) {#strerror}

Thread-safe variant of strerror that returns a cstring.

The memory is owned by the function and remains valid until the next call.

### QString KSafeStringError::strerrorQString(int *error*) {#strerrorQString}

Thread-safe variant of strerror that returns a [QString](https://doc.qt.io/qt-6/qstring.html)
