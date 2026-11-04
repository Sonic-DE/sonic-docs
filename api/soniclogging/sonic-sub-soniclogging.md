---
title: "Sonic Namespace"
description: "The SonicDE message handler and logging API."
---

# Sonic Namespace

The SonicDE message handler and logging API.

## Namespaces {#namespaces}

### namespace Sonic::Logging

Every executable writes its own log file: /var/log/sonic/\<binary\>.log when it runs as root, ~/.local/state/sonic/\<binary\>.log otherwise. Messages also go to journald when it is running. When a service manager already captures the program's output (systemd, runit, s6, OpenRC's supervise-daemon, dinit, or an X session's ~/.xsession-errors), lines go to that output instead and no file is written.

Each line reads "\<ISO timestamp with ms\> (DD\|II\|WW\|EE) \[\<source\>\] \<message\>", where \<source\> is the category for the executable's own messages, the library's ID for messages from a library, and the binary name for messages without a category.
