---
title: "kconf_update Tool"
description: "Persistent platform-independent application settings."
---

# kconf\_update Tool

Persistent platform-independent application settings.

kconf\_update is a tool designed to update config files. Over time applications sometimes need to rearrange the way configuration options are stored. Since such an update shouldn't influence the configuration options that the user has selected, the application must take care that the options stored in the old way will still be honored.

What used to happen is that the application looks up both the old and the new configuration option and then decides which one to use. This method has several drawbacks:

- The application may need to read more configuration files than strictly needed, resulting in a slower startup.
- The application becomes bigger with code that will only be used once.

kconf\_update addresses these problems by offering a framework to update configuration files without adding code to the application itself.

See the [Wiki](https://techbase.kde.org/Development/Tools/Using_kconf_update) for more information.
