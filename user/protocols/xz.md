---
title: xz and lzma
description: Read files compressed with xz or lzma.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kioworker/xz/index.docbook
source_authors: [Per Øyvind Karlsen]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b2196 (filter); read from code, not clicked through"
---

# xz and lzma

Xz is a compression program.

The xz KIO worker isn't directly usable, and is intended for use as a filter. For example, the [tar](tar.md) KIO worker can filter a file through the xz KIO worker, in order to display the contents of a `tar.lzma` or `tar.xz` file directly in an [Ecco](../applications/ecco.md) window.

If you click a file compressed with `.lzma` or `.xz` in Ecco, this KIO worker is used to uncompress it and display it as a normal, uncompressed file.

See the `xz` man page.
