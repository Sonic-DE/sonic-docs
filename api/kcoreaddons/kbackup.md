---
title: "KBackup Namespace"
description: "Provides utility functions for backup of files."
---

# KBackup Namespace

Provides utility functions for backup of files. [More...](#details)

- **Header:** `#include <KBackup>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### bool KBackup::numberedBackupFile(const QString &*filename*, const QString &*backupDir* = QString(), const QString &*backupExtension* = QStringLiteral("~"), const uint *maxBackups* = 10) {#numberedBackupFile}

Function to create a backup file for a given filename.

This function creates a series of numbered backup files from the given filename.

The backup file names will be of the form: \<name\>.\<number\>\<extension\> for instance

```cpp
chat.3.log
```

The new backup file will be have the backup number 1. Each existing backup file will have its number incremented by 1. Any backup files with numbers greater than the maximum number permitted (`maxBackups`) will be removed. You can use this method even if you don't use KSaveFile.

`filename` the file to backup

`backupDir` optional directory where to save the backup file in. If empty (the default), the backup will be in the same directory as `filename`.

`backupExtension` the extension to append to `filename`, which is "~" by default. Do not use an extension containing digits.

`maxBackups` the maximum number of backup files permitted. For best performance a small number (10) is recommended.

Returns `true` if successful, or false if an error has occurred.

### bool KBackup::simpleBackupFile(const QString &*filename*, const QString &*backupDir* = QString(), const QString &*backupExtension* = QStringLiteral("~")) {#simpleBackupFile}

Function to create a backup file for a given filename.

This function creates a backup file from the given filename. You can use this method even if you don't use KSaveFile.

`filename` the file to backup

`backupDir` optional directory where to save the backup file in. If empty (the default), the backup will be in the same directory as `filename`.

`backupExtension` the extension to append to `filename`, "~" by default.

Returns true if successful, or false if an error has occurred.
