---
title: Comic plugin examples
description: Working comic plugins, one for each type of comic.
source_url: https://develop.kde.org/docs/plasma/comic-plugin/example/
source_authors: [Alexander Lohnau, Andrea Marano, Carl Schwan, Kunda Ki, Marius P, Matthias Fuchs, Thiago Sueto, Tobias Koenig]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "API names compared with applets/comic/engine in sonic-workspace-addons. The scripts were not run: they depend on third-party sites, whose pages may have changed since they were written."
---

# Comic plugin examples

These examples, one for each type of comic, show what comic plugins look like. You can see others by installing comics with the "Get New Comics…" dialog: their code is in `~/.local/share/plasma/comics/`.

These plugins parse third-party sites, which change over time, so read them as examples of the technique.

## Date

This is the plugin for Jesus and Mo.

It also shows a special case, where a page for a date doesn't lead to the image itself but to a smaller version. The plugin has to follow the link there to get the image, as well as the next and previous identifiers. Some other comic sites use the same structure.

```js
// SPDX-FileCopyrightText: 2009 Matthias Fuchs <mat69 AT YOU KNOW DELETE THAT gmx.net>
// SPDX-License-Identifier: LGPL-2.0-or-later

let findNewDate = false;
const mainPage = "https://www.jesusandmo.net/";

function init() {
    comic.comicAuthor = "\"Mohammed Jones\"";
    comic.firstIdentifier = "2005-11-24";
    comic.shopUrl = "https://www.jesusandmo.net/the-shop/";

    const today = date.currentDate();
    findNewDate = (comic.identifier.date >= today.date);
    let url = mainPage;

    if (!findNewDate) {
        url += comic.identifier.toString("yyyy/MM/dd/");
    }

    comic.requestPage(url, comic.User);
}

function pageRetrieved(id, data) {
    // find the URL of the comic's page
    if (id === comic.User) {
        // find the most recent date
        if (findNewDate) {
            const re = new RegExp("(http://www.jesusandmo.net/(\\d{4}/\\d{2}/\\d{2}/)[^/]+/)#comments\"");
            const match = re.exec(data);
            if (match !== null) {
                comic.identifier = date.fromString(match[2], "yyyy/MM/dd");
                comic.websiteUrl = match[1];
            } else {
                comic.error();
                return;
            }
        } else {
            const re = new RegExp("<a href=\"(" + mainPage + comic.identifier.toString("yyyy/MM/dd/") + "[^\"]+)\"><img");
            const match = re.exec(data);
            if (match !== null) {
                comic.websiteUrl = match[1];
            } else {
                comic.error();
                return;
            }
        }

        comic.requestPage(comic.websiteUrl, comic.Page);
    }
    if (id === comic.Page) {
        const stripsUrl = `${mainPage}strips/`;
        let re = new RegExp(`<img src="(${stripsUrl + comic.identifier.toString(date.ISODate)}[^"]+)" alt="([^"]+)"`);
        let match = re.exec(data);
        if (match !== null) {
            comic.title = match[2];
            comic.requestPage(match[1], comic.Image);
        } else {
            comic.error();
        }

        re = new RegExp("<a href=\"" + mainPage + "(\\d{4}/\\d{2}/\\d{2}/)[^\"]+\"><span class=\"prev\">");
        match = re.exec(data);
        if (match !== null) {
            comic.previousIdentifier = date.fromString(match[1], "yyyy/MM/dd/");
        }

        re = new RegExp("<a href=\"" + mainPage + "(\\d{4}/\\d{2}/\\d{2}/)[^\"]+\"><span class=\"next\">");
        match = re.exec(data);
        if (match !== null) {
            comic.nextIdentifier = date.fromString(match[1], "yyyy/MM/dd/");
        }
    }
}
```

## Number

This is the plugin for xkcd.

```js
// SPDX-FileCopyrightText: 2007 Tobias Koenig <tokoe AT YOU KNOW DELETE THAT kde.org>
// SPDX-FileCopyrightText: 2009 Matthias Fuchs <mat69 AT YOU KNOW DELETE THAT gmx.net>
// SPDX-License-Identifier: LGPL-2.0-or-later

function init() {
    comic.comicAuthor = "Randall Munroe";
    comic.websiteUrl = "https://xkcd.com/";
    comic.shopUrl = "https://store.xkcd.com/";

    comic.requestPage(comic.websiteUrl, comic.User);
}

function pageRetrieved(id, data) {
    // find the most recent strip
    if (id === comic.User) {
        const re = new RegExp("Permanent link to this comic: http://xkcd.com/(\\d+)/");
        const match = re.exec(data);
        if (match !== null) {
            comic.lastIdentifier = match[1];
            comic.websiteUrl += comic.identifier + "/";
            comic.requestPage(comic.websiteUrl, comic.Page);
        } else {
            comic.error();
        }
    }
    if (id === comic.Page) {
        let re = new RegExp(`<img src="(http://imgs.xkcd.com/comics/[^"]+)"`);
        let match = re.exec(data);
        if (match !== null) {
            comic.requestPage(match[1], comic.Image);
        } else {
            comic.error();
            return;
        }

        // find the tooltip and the title of the strip
        re = new RegExp(`src="http://imgs.xkcd.com/comics/.+" title="([^"]+)" alt="([^"]+)"`);
        match = re.exec(data);
        if (match !== null) {
            comic.additionalText = match[1];
            comic.title = match[2];
        }
    }
}
```

## String

This is the plugin for Help Desk.

```js
// SPDX-FileCopyrightText: 2008 Matthias Fuchs <mat69 AT YOU KNOW DELETE THAT gmx.net>
// SPDX-License-Identifier: GPL-2.0-or-later

function init() {
    comic.comicAuthor = "Christopher Wright";
    comic.firstIdentifier = "1996/03/alex-loss-words";
    comic.websiteUrl = "http://www.ubersoft.net/comic/hd/";
    comic.shopUrl = "http://www.cafepress.com/evisceratistore";

    // check whether comic.identifier is empty; there are other ways too, like checking its length
    if (comic.identifier.length > 0) {
        comic.websiteUrl += comic.identifier;
        comic.requestPage(comic.websiteUrl, comic.Page);
    } else {
        comic.requestPage(comic.websiteUrl + comic.firstIdentifier, comic.User);
    }
}

function pageRetrieved(id, data) {
    // find the most recent comic
    if (id === comic.User) {
        const re = new RegExp(`<a href="/comic/hd/([^"]+)">last`);
        const match = re.exec(data);
        if (match !== null) {
            comic.lastIdentifier = match[1];
            comic.identifier = comic.lastIdentifier;
            comic.websiteUrl += comic.identifier;
            comic.requestPage(comic.websiteUrl, comic.Page);
        } else {
            comic.error();
        }
    }
    // get the comic image and all other available information
    if (id === comic.Page) {
        // here the title of the strip is spread across two places on the page
        let re = new RegExp("<a href=\"/comic/hd/storyline/[^\"]+\" rel=\"tag\" title=\"\">([^<]+)</a>");
        let match = re.exec(data);
        if (match !== null) {
            comic.title = match[1];
        }

        // get the image and the second part of the title
        re = new RegExp("<img src=\"(http://www\\.ubersoft\\.net/files/comics/hd/[^\"]+)\" alt=\"[^\"]*\" title=\"([^\"]*)");
        match = re.exec(data);
        if (match !== null) {
            comic.title += (comic.title.length && match[2].length) ? ": " + match[2] : match[2];
            comic.requestPage(match[1], comic.Image);
        } else {
            comic.error();
            return;
        }

        // get the previous identifier
        re = new RegExp("<a href=\"/comic/hd/([^\"]+)\">. previous</a>");
        match = re.exec(data);
        if (match !== null) {
            comic.previousIdentifier = match[1];
        }

        // get the next identifier
        re = new RegExp("<a href=\"/comic/hd/([^\"]+)\">next .</a>");
        match = re.exec(data);
        if (match !== null) {
            comic.nextIdentifier = match[1];
        }
    }
}
```
