---
title: "KTextToHTML Namespace"
description: "Additions to Qt Core."
---

# KTextToHTML Namespace

Additions to Qt Core. [More...](#details)

- **Header:** `#include <KTextToHTML>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

## Detailed Description {#details}

## Type Documentation {#type-documentation}

### enum KTextToHTML::Option {#Option-enum}

**flags KTextToHTML::Options**

| Constant | Value | Description |
| --- | --- | --- |
| `KTextToHTML::PreserveSpaces` | `1 << 1` | Preserve white-space formatting of the text |
| `KTextToHTML::ReplaceSmileys` | `1 << 2` | Replace text emoticons smileys by emoticons images |
| `KTextToHTML::IgnoreUrls` | `1 << 3` | Don't parse and replace any URLs |
| `KTextToHTML::HighlightText` | `1 << 4` | Interpret text highlighting markup, like \*bold\*, \_underline\_ and /italic/, and wrap them in corresponding HTML entities |
| `KTextToHTML::ConvertPhoneNumbers (since Qt 5.56)` | `1 << 5` | Replace phone numbers with tel: links |

The `Options` type is a typedef for `QFlags<Option>. `It stores an OR combination of `Option` values.

## Function Documentation {#function-documentation}

### QString KTextToHTML::convertToHtml(const QString &*plainText*, const KTextToHTML::Options &*options*, int *maxUrlLen* = 4096, int *maxAddressLen* = 255) {#convertToHtml}

Converts plaintext into html. The following characters are converted to HTML entities: & " \< \>. Newlines are also preserved.

`plainText` The text to be converted into HTML.

`options` The options to use when processing `plainText`.

`maxUrlLen` The maximum length of permitted URLs. The reason for this limit is that there may be possible security implications in handling URLs of unlimited length.

`maxAddressLen` The maximum length of permitted email addresses. The reason for this limit is that there may be possible security implications in handling addresses of unlimited length.

Returns an HTML version of the text supplied in the 'plainText' parameter, suitable for inclusion in the BODY of an HTML document.
