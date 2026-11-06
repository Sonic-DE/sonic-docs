---
title: Colorful MIME type icons
description: The margins, anatomy, base shapes and colors of large MIME type icons.
source_url: https://develop.kde.org/hig/icons/colorful/mimetype/
source_authors: [Carl Schwan, Johannes Zarl-Zierl, John Veness, Michael Howell, Nate Graham]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver-icons icons/mimetypes (size folders)"
---

# Colorful MIME type icons

MIME type icons are used to depict documents and files. They come in four sizes: 16px, 22px, 32px, and 64px. MIME type icons use the [monochrome style](../monochrome/index.md) for 16px and 22px sizes, and the [colorful style](index.md) for 32px and 64px sizes.

## Purpose

MIME type icons allow a user to quickly recognize the types of their files without needing to look at a file's extension or contents. They primarily appear in file listings in large amounts, and their design reflects a sense of unity among files in a user's system.

## Design

### Margins

64px MIME type icons have a top and bottom margin of 3 pixels, and 32px MIME type icons have a top and bottom margin of 2 pixels.

![A 64px icon with its margins marked](../../images/mime-margin-64.png)

64px icons should have a top and bottom margin of 3 pixels.

![A 32px icon with its margins marked](../../images/mime-margin-32.png)

32px icons should have a top and bottom margin of 2 pixels.

### Anatomy

Colorful MIME type icons consist of two elements: the monochromatic counterpart of the colorful MIME type icon overlaid on a background relating to the icon's type.

![A MIME type icon with its two parts numbered](../../images/mime-anatomy.png)

1. Monochromatic foreground
2. Base

![The foreground symbol alone](../../images/mime-monochromatic-layer.png)

The foreground of a MIME type icon indicates the specific type of file it is.

![The base alone](../../images/mime-base-layer.png)

The background of a MIME type icon indicates the general type of file it is.

### Base

The base of a MIME type icon serves to give files of a general type a shared and recognizable silhouette.

#### Archives

Archives, packages, compressed files, and disk images use a square with a zipper going halfway down.

![An archive base with a centered zipper](../../images/mime-archive.png)

For archive icons without a foreground, the zipper goes through the center.

![An archive base with an offset zipper and a foreground area](../../images/mime-archive-symbol.png)

For archive icons with a foreground, the zipper is offset to give the foreground some space.

#### Images

Images use a horizontal rectangle with the top right corner folded and casting a shadow.

![The base for image type icons.](../../images/mime-image.png)

#### Videos

Videos use a horizontal rectangle styled to look like a filmstrip.

![The base for video type icons.](../../images/mime-video.png)

#### Audio

Audio files use a CD sleeve with a partially visible CD sticking out.

![The base for audio type icons.](../../images/mime-audio.png)

#### Books

Book files use a vertical rectangle with a book spine.

![The base for book type icons.](../../images/mime-book.png)

#### Other

Documents and other icons use a rectangle with a fold in the top right corner casting a shadow.

![The base for document and other type icons.](../../images/mime-document.png)

### Foreground

The foreground of a MIME type icon serves to inform the user about the specific type of file an icon represents. The foreground should be the monochromatic icon of the MIME type.

![A foreground symbol with no shadow](../../images/mime-fg-do.png)

**Do:** The foreground decoration of a MIME type icon does not cast a shadow.

![A foreground symbol casting a shadow](../../images/mime-fg-dont.png)

**Don't:** Don't have the foreground decoration of a MIME type icon cast a shadow.

### Color

The color of a MIME type icon helps inform the user what kind of icon it is. Icons for MIME types associated with a brand identity should use the colors of that brand identity.

![A green Android package icon](../../images/mime-color-do.png)

**Do:** The usage of Android brand colors helps users identify the icon as that of an Android package.

![A pink Android package icon](../../images/mime-color-dont.png)

**Don't:** Don't use radically different brand colors. Users will not recognize the icon as one of a filetype from that brand.
