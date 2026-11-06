---
title: zstd
description: Read files compressed with zstd.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kioworker/zstd/index.docbook
source_authors: [Friedrich W. H. Kossebau]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b2196 (filter); read from code, not clicked through"
---

# zstd

`zstd` is a compression program.

The zstd KIO worker isn't directly usable, and is intended for use as a filter. For example, the [tar](tar.md) KIO worker can filter a file through the zstd KIO worker, in order to display the contents of a `tar.zst` file directly in an [Ecco](../applications/ecco.md) window.

If you click a file compressed with a `zst` extension in Ecco, this KIO worker is used to uncompress it and display it as a normal, uncompressed file.

See the `zstd` man page.
