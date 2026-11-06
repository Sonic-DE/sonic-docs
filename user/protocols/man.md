---
title: man
description: Read manual pages.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kioworker/man/index.docbook
source_authors: [Lauri Watts, Nicolas Goutte]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b2196 (man) and sonic-frameworks-io e3f55ceb (src/urifilters/shorturi); read from code, not clicked through"
---

# man

The man KIO worker lets you read the man pages installed on your system. It's easy to use:

- `man:`: See the sections of the manual, and click to find the rest.
- `man:/fopen`: See the man page of `fopen`.
- `man:/fopen(3)`: See the man page of `fopen` in section 3.
- `man:/(3)`: See the index of section 3.
- `man:/intro(3)`: See the introduction of section 3.

> [!NOTE]
> If more than one man page has the name you entered, you get a list where you can choose the one you want.

There's also a shortcut: `#fopen` has the same effect as above.

If you don't find all your man pages, adjust the configuration file `/etc/manpath.config`, or a file of a similar name depending on your distribution, or adjust the environment variables `MANPATH` and `MANSECT`.

As with any other KIO worker, you can enter a URL like `man:/socket` in applications that open URLs, and you'll see the man page in HTML format.
