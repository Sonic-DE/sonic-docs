---
title: Dependencies
description: What a build host needs before building Sonic-DE.
---

# Dependencies

Every build host needs:

- Python 3 with PyYAML.
- Qt 6, supplied by the operating system.
- CMake 3.28 or newer.

sonicde-builder validates system libraries through `pkg-config` before it builds anything.
To list the operating-system packages the current build needs, run:

```sh
./install-deps
```

## Platforms

Package lists for individual distributions are added here once a full build has succeeded on
that platform. Gentoo and Arch Linux come first; Debian testing and FreeBSD follow after a
verified build.
