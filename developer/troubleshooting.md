---
title: Troubleshooting
description: Known problems when building Sonic-DE, and how to fix them.
---

# Troubleshooting

## Stale debug CMake exports

Old debug installations can leave `KF6*Targets-debug.cmake` fragments that refer to libraries
which no longer exist, and CMake then fails to configure later packages. Preview them with:

```sh
./cleanup-stale-cmake-debug
```

Remove the confirmed stale fragments with `--apply`. Use `--prefix PATH` (repeatable) to
inspect an installation outside `/usr`, such as `state/install-stage/usr`. The command is never
run automatically by `build-all`.
