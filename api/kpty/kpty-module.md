---
title: "KPty C++ Classes"
description: "Interfacing with pseudo terminal devices."
---

# KPty C++ Classes

Interfacing with pseudo terminal devices. [More...](#details)

## Classes {#classes}

- [KPty](kpty.md): Provides primitives for opening & closing a pseudo TTY pair, assigning the controlling TTY, utmp registration and setting various terminal attributes.
- [KPtyDevice](kptydevice.md): Encapsulates KPty into a QIODevice, so it can be used with Q\*Stream, etc.
- [KPtyProcess](kptyprocess.md): This class extends KProcess by support for PTYs (pseudo TTYs).

## Detailed Description {#details}
