---
title: Comic plugins
description: Learn how to create a comic provider plugin.
source_url: https://develop.kde.org/docs/plasma/comic-plugin/
source_authors: [Alexander Lohnau, Andrea Marano, Carl Schwan, Kunda Ki, Marius P, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "applets/comic/engine in sonic-workspace-addons (comicproviderwrapper, comic_package). Read from code; no comic plugin was run, since that needs the sites online."
---

# Comic plugins

This tutorial describes how to create a plugin for the comic widget, part of `sonic-workspace-addons`. Plugins are written in JavaScript, evaluated by a QJSEngine.

## Types of comics

The comic widget supports three types of comics, which are the ways comics are identified:

1. Date
2. Number
3. String

For example, `garfield:2000-01-01` or `xkcd:100`. A string can be anything. If the site a comic is published on has no easy way to get a date or number for a strip, or those wouldn't help to reach it, use a string.

The type should be enough to get the comic. In `xkcd:100`, the first part says which plugin to load, and the last part tells your plugin which strip to load. Your plugin gets no more information from the engine than that.

## Package structure

Comic plugins are packages that can be uploaded to [the KDE Store](https://store.kde.org) and downloaded directly from the widget.

Create a folder to work in, with this structure:

```text
├── contents
│   └── code
│       └── main.js
├── icon.png
└── metadata.json
```

Later you zip the files into a `.comic` package, where `my_comic` is the name of your comic:

```bash
zip -r my_comic.comic contents/code/main.js metadata.json icon.png
```

## The metadata.json file

Every comic plugin needs a `metadata.json` file like this:

```json
{
    "KPlugin": {
        "Authors": [
            {
                "Email": "Your email address",
                "Name": "Your Name"
            }
        ],
        "Description": "My Comic",
        "Icon": "icon.png",
        "Id": "my_comic",
        "License": "GPLv2",
        "Name": "My Comic",
        "Version": "0.1",
        "Website": "https://example.org"
    },
    "X-KDE-PlasmaComicProvider-SuffixType": "Date"
}
```

The comic shows up in the comic list under `Name`. You can translate the name:

```json
"Name": "My Comic",
"Name[de]": "Mein Comic"
```

`Icon` is only needed if you have an icon for your comic, like a favicon.

`Id` is the internal name of your plugin, which the engine uses to identify which plugin to load. It can't contain white space.

`X-KDE-PlasmaComicProvider-SuffixType` is the type of the comic: `Date`, `Number` or `String`.

## The code

The next two sections describe the available functions and objects. You can skip them and use them only as a reference.

### Available functions

```js
function init()
comic.requestPage(url, id, metadata)
function pageRetrieved(id, data)
comic.combine(image, position)
```

There are also date functions similar to [QDate](https://doc.qt.io/qt-6/qdate.html). You can add other functions if you need them.

#### init()

The engine calls `init()`, so you need to include it. The engine only loads your plugin, and so calls `init()`, if the requested strip hasn't been cached.

#### comic.requestPage(url, id, metadata)

Asks the engine to download `url`. `id` says what type of download it is. Three are predefined:

- `comic.Page`
- `comic.User`
- `comic.Image`

`comic.Page`, `comic.User` and any integer that isn't `comic.Image` are for downloading web pages, so only text. `comic.Image` is for the actual comic image.

You can also specify `metadata`, such as the referrer. The [KIO documentation](https://github.com/Sonic-DE/sonic-frameworks-io/blob/master/docs/metadata.txt) lists what is supported.

```js
const infos = {
    accept: "text/html, image/jpeg, image/png, text/*, image/*, */*",
    referrer: "www.example.com/index.html",
}
comic.requestPage("www.example.com/image.jpg", comic.Image, infos);
comic.requestPage("www.example.com/image.jpg", comic.Image); // also works, but sends no metadata
```

If the download succeeds, the engine calls `pageRetrieved`.

#### pageRetrieved(id, data)

Only called if you asked the engine to download something.

What `data` is depends on `id`. If `id` is `comic.Image`, `data` is the image, and changes to it change the image the plugin displays. In all other cases, `data` is the downloaded data as a byte stream converted to Unicode (see `comic.textCodec` under [available objects](#available-objects)). You can convert it to a string if needed:

```js
const dataString = data.toString();
const begin = dataString.indexOf("test"); // wouldn't work without the conversion
```

Here you can search the data for the URL of the strip, the title, the author, the identifier of the next strip and so on. You only need this function if you want to find something in a web page or modify the image.

#### comic.combine(image, position)

The engine can't handle several pictures itself, so sometimes you have to combine them into one. `image` needs to be an image, and `position` is one of:

- `comic.Left`
- `comic.Top` (the default)
- `comic.Right`
- `comic.Bottom`

`image` is combined with the last downloaded image, and `position` says where `image` is placed. This code, with parts removed and pseudocode added, is taken from the Deo Ignito comic plugin:

```js
let firstImage = 0;
// the variable that temporarily stores the combined images,
// so this is the image all other pictures are combined with.
// For 4 pictures 1, 2, 3, 4:
// 1. 4
// 2. 3 and 4 --> 34
// 3. 2 and 34 --> 234
// 4. 1 and 234 --> 1234
// We use comic.Bottom here, as that works well with Array.pop()

const urlArray = [];
// stores the URLs of the pictures

function pageRetrieved(id, data) {
    if (id === comic.Page) {
        urlArray.push(url_1); // url_1 to url_4 are pseudocode: you need actual URLs
        urlArray.push(url_2);
        urlArray.push(url_3);
        urlArray.push(url_4);

        // download the last URL in the array
        comic.requestPage(urlArray.pop(), comic.Image);
    }
    if (id === comic.Image) {
        if (firstImage != 0) {
            // combines the most recently downloaded picture with firstImage,
            // placing firstImage at the bottom
            comic.combine(firstImage, comic.Bottom);
        }

        if (urlArray.length > 0) {
            // another image download overwrites the previous image,
            // so store the current combination before requesting one
            firstImage = comic.image();

            comic.requestPage(urlArray.pop(), comic.Image);
        }
    }
}
```

#### Date functions

The date object is designed to work like [QDate](https://doc.qt.io/qt-6/qdate.html), though there can be differences. The [source](https://github.com/Sonic-DE/sonic-workspace-addons/tree/master/applets/comic/engine) has the details. Two examples:

```js
comic.identifier = date.fromString("2008,03,07", "yyyy,MM,dd");
comic.websiteUrl += comic.identifier.toString("dd-MM-yyyy");
```

#### comic.requestRedirectedUrl(url, id, metadata)

Sometimes you only have a relative URL: next, for example, might be the current URL plus `/?relid=X&go=+1`. This function gets the real URL it points to, which helps when you don't know the next or previous identifier but it is embedded in the real URL.

`id` says what type the download is. Some are predefined, for convenience; you could use any integer:

- `comic.PreviousUrl`
- `comic.NextUrl`
- `comic.CurrentUrl`
- `comic.FirstUrl`
- `comic.LastUrl`
- `comic.UserUrl`

`metadata` is optional, as for `requestPage`.

This always calls `redirected(id, url)`. If there was no redirection, it is called with the original URL.

```js
function init() {
    // ... do something
    comic.requestRedirectedUrl("www.example.com/aComicId?go=-1", comic.PreviousUrl);
    // ... do something
}

function redirected(id, url) {
    if (id === comic.PreviousUrl) {
        comic.previousIdentifier = // ... transform the URL to an identifier
    }
}
```

#### redirected(id, url)

Only called after you called `comic.requestRedirectedUrl`. It has either the redirected URL or the original one.

### Available objects

These are the objects you can assign to. Only `comic.identifier` and, in special cases, some other identifiers have an initial value.

```js
comic.comicAuthor = "Randall Munroe";      // the author or authors of the strip
comic.websiteUrl = "https://xkcd.com/42";  // the address of the page where the strip is
comic.shopUrl = "https://store.xkcd.com/"; // if there is a shop for the comic
comic.title = "Geico";                     // the title of the strip; can also be the chapter etc.
comic.additionalText = "David did this";   // additional text, shown as a tooltip in the widget
comic.textCodec = "Windows-1251";          // only set this if the codec of the web content isn't recognized automatically. Test without it first.
comic.isLeftToRight = false;               // true is the default; only set this if the comic isn't left to right
comic.isTopToBottom = false;               // true is the default; only set this if the comic isn't top to bottom
```

#### Identifier

There are six identifier objects, which react differently depending on the type of comic.

```js
comic.identifier          // the identifier of the current strip
comic.firstIdentifier     // the first strip, e.g. number 1
comic.lastIdentifier      // the last (most recent) strip, e.g. number 42
comic.previousIdentifier  // the previous identifier of the current strip, e.g. number 40
comic.nextIdentifier      // the next identifier of the current strip, e.g. 41
comic.identifierSpecified // whether the engine specified an identifier (bool)
```

`comic.identifier` is the identifier the engine is being asked for, so it is already set, though you can assign something different.

If `comic.identifierSpecified` is false, you should download the most recent strip.

For some types, what *you* assign to `comic.identifier`, `comic.lastIdentifier` or `comic.firstIdentifier` is checked, and `comic.identifier` is changed to match.

If there is a `nextIdentifier`, the engine caches the strip, so it doesn't have to be downloaded again.

#### Date

`comic.identifier` is always a date that exists. If the engine specified no exact date, it is today.

```js
comic.firstIdentifier   // has to be specified manually
comic.lastIdentifier    // is today by default
```

If you assign to `comic.lastIdentifier`, `comic.identifier` is reassigned to that day, but only if it was after `comic.lastIdentifier`, or if `comic.identifierSpecified` is false:

```js
comic.identifier = date.fromString("2009-01-12");
print(comic.identifier);    // 2009-01-12
comic.lastIdentifier = date.fromString("2009-01-10");
print(comic.identifier);    // would be 2009-01-10 now

comic.lastIdentifier = date.fromString("2009-02-01");
print(comic.identifier);    // still 2009-01-10
```

In any case, `comic.identifier` stays in the range you defined.

`comic.previousIdentifier` and `comic.nextIdentifier` are also checked:

- If `comic.identifier` is `comic.firstIdentifier`, there is no `comic.previousIdentifier`.
- If `comic.identifier` is `comic.lastIdentifier`, there is no `comic.nextIdentifier`.

If you don't set both of them, they are set automatically:

- `comic.previousIdentifier` is `comic.identifier` minus 1 day, and never before `comic.firstIdentifier`.
- `comic.nextIdentifier` is `comic.identifier` plus 1 day, and never after `comic.lastIdentifier`.

Set the identifiers yourself if the comic isn't end to end, such as 2009-01-12, 2009-01-14, 2009-02-01. If you aren't sure, set them yourself.

#### Number

`comic.identifier` is a specific number, or if the engine specified none, `0`.

With `comic.identifierSpecified` (recommended!) you can have a comic identified by the number 0. Without it, you have to shift everything.

```js
comic.firstIdentifier   // is 1 by default
comic.lastIdentifier    // has to be specified manually
```

If `comic.identifier` is 0 and you assign to `comic.lastIdentifier`, `comic.identifier` is reassigned to that number:

```js
comic.identifier = 0;
print(comic.identifier);    // 0
comic.lastIdentifier = 42;
print(comic.identifier);    // would be 42 now

comic.lastIdentifier = 100;
print(comic.identifier);    // still 42
```

```js
print(comic.identifierSpecified);   // suppose that it is false
comic.lastIdentifier = 20;
print(comic.identifier);            // would be 20 now
```

In any case, `comic.identifier` stays in the specified range.

`comic.previousIdentifier` and `comic.nextIdentifier` are also checked:

- If `comic.identifier` is `comic.firstIdentifier`, there is no `comic.previousIdentifier`.
- If `comic.identifier` is `comic.lastIdentifier`, there is no `comic.nextIdentifier`.

If you don't set both of them, they are set automatically:

- `comic.previousIdentifier` is `comic.identifier` minus 1, and never smaller than `comic.firstIdentifier`.
- `comic.nextIdentifier` is `comic.identifier` plus 1, and never larger than `comic.lastIdentifier`.

Set the identifiers yourself if the comic isn't end to end, such as 1, 4, 5, 9. If you aren't sure, set them yourself.

#### String

Here you have to set nearly everything yourself. `comic.identifier` is a specific string, or if the engine specified none, an empty string.

```js
print(comic.identifierSpecified);   // suppose that it is false
comic.lastIdentifier = "muahaha";
print(comic.identifier);            // would be "muahaha" now
```

#### comic.image()

Gives access to the image object. This sets the last frame of an animation as the image. For it to work, data must already be set, for example with `comic.requestPage(url, comic.Image)`.

```js
const img = comic.image();
const count = img.imageCount(); // the number of frames if it's an animation, otherwise 0, or -1 on error
if (count >= 0) {
    let temp;
    for (let i = 0; i < count; i++) {
        temp = img.read(); // reads the next frame
    }
    img.image = temp; // sets the last frame as the image
}
```
