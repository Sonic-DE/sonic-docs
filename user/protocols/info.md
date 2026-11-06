---
title: info
description: Read GNU Info documentation.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kioworker/info/index.docbook
source_authors: [Lauri Watts, Nicolas Goutte]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b2196 (info); read from code, not clicked through"
---

# info

Info is a type of documentation. The documents are in a file format called texinfo, and can be read on the command line with the `info` program.

The info KIO worker lets you read the info pages installed on your system from within [Ecco](../applications/ecco.md). It's very easy to use:

```text
info:gcc
```

This shows the top level node of the Info documentation for the `gcc` compiler.

Info is a GNU replacement for `man`, but isn't widely used outside of GNU software.

You can use the info KIO worker directly from Ecco and KRunner.
