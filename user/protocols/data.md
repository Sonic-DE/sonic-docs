---
title: data
description: Include small document data in the address itself.
source_url: https://invent.kde.org/frameworks/kio/-/blob/master/docs/kioworker6/data/index.docbook
source_authors: [Leo Savernik]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io e3f55ceb (docs/kioworker6/data, src/core/dataprotocol.cpp); read from code, not clicked through"
---

# data

Data URLs let small document data be included in the URL itself. This is useful for very small HTML test cases, or other occasions that don't justify a document of their own.

`data:,foobar` (note the comma after the colon) delivers a text document that contains nothing but `foobar`.

That example delivered a text document. For HTML documents, you have to specify the MIME type `text/html`: `data:text/html,<title>Testcase</title><p>This is a testcase</p>`. This produces exactly the same output as if the content had been loaded from a document of its own.

You can also specify other character sets. Note that 8-bit characters have to be escaped by a percent sign and their two-digit hexadecimal codes: `data:;charset=iso-8859-1,Gr%FC%DFe aus Schl%E4gl` results in `Grüße aus Schlägl`, whereas omitting the charset attribute might lead to something like `Gr??e aus Schl?gl`.

[IETF RFC 2397](https://www.ietf.org/rfc/rfc2397.txt) has more information.
