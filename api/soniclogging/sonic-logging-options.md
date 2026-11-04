---
title: "Sonic::Logging::Options Struct"
description: "What install() sets up."
---

# Sonic::Logging::Options Struct

What [install](sonic-logging.md#install)() sets up. [More...](#details)

- **Header:** `#include <Sonic/Logging/Logging>`
- **CMake:** `find_package(SonicLogging REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::Logging)`

[List of all members, including inherited members](sonic-logging-options-members.md)

## Detailed Description {#details}

Callers set only the members they change, for example `Sonic::Logging::install({.rotateOnStartup = true})`.

## Member Variable Documentation {#member-variable-documentation}

### QString Options::binaryName {#binaryName-var}

Empty: the name the program was started as, without directories, e.g. "soniclogin-helper".

### QStringList Options::dropDebugCategoryExact {#dropDebugCategoryExact-var}

Debug messages from exactly these categories are dropped; the empty string is the default category.

### QStringList Options::dropDebugCategoryPrefixes {#dropDebugCategoryPrefixes-var}

Debug messages from categories starting with any of these are dropped. SonicDE's own (org.sonicde.\*) debug messages are never dropped.

### QStringList Options::dropDebugMessageSubstrings {#dropDebugMessageSubstrings-var}

Debug messages containing any of these (case-insensitive) are dropped.

### bool Options::journald {#journald-var}

Also send to journald when it's running.

### bool Options::mirrorToStderr {#mirrorToStderr-var}

Mirror lines to stderr even when it isn't a terminal, for command-line tools whose stderr a build system or script reads. Ignored when a service manager captures the output (lines already go there) and when stderr is the journal.

### bool Options::mirrorToStderrWhenTty {#mirrorToStderrWhenTty-var}

Mirror lines to stderr when it is a terminal and not already the journal.

### bool Options::rotateOnStartup {#rotateOnStartup-var}

Rotate to \<file\>.last on every run instead of by size.

### bool Options::writeLogFile {#writeLogFile-var}

Write the program's own log file. Build tools that run inside package builds turn it off, so they never create /var/log/sonic or a file in the build user's home; lines then go to stderr (and journald).
