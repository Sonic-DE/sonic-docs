---
title: bzip2
description: Read files compressed with bzip2.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kioworker/bzip2/index.docbook
source_authors: [Lauri Watts]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b2196 (filter); read from code, not clicked through"
---

# bzip2

`bzip2` is a compression program.

The bzip2 KIO worker isn't directly usable, and is intended for use as a filter. For example, the [tar](tar.md) KIO worker can filter a file through the bzip2 KIO worker, in order to display the contents of a `tar.bz2` file directly in an [Ecco](../applications/ecco.md) window.

If you click a file compressed with `.bz2` in Ecco, this KIO worker is used to uncompress it and display it as a normal, uncompressed file.

See the `bzip2` man page.

`bzip` is the ancestor of bzip2. It's rarely used today, having been replaced by bzip2, which offers much better compression.
