---
title: thumbnail
description: Generate file previews.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kioworker/thumbnail/index.docbook
source_authors: [Carsten Pfeiffer]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b2196 (thumbnail) and sonic-ecco e905af7d5 (src/views/dolphinviewactionhandler.cpp); read from code, not clicked through"
---

# thumbnail

SonicDE uses the thumbnail KIO worker for network transparent and persistent generation of thumbnails.

It uses plugins to generate the actual thumbnails. You can turn these thumbnails on and off with **View > Show Previews** in [Ecco](../applications/ecco.md).

The thumbnail KIO worker isn't directly useful to a user, but developers can use it in their own applications to create file previews. See the documentation in the [sources](https://github.com/Sonic-DE/sonic-frameworks-io-extras/tree/master/thumbnail) for more.
