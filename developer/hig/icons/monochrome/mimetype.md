---
title: Monochrome MIME type icons
description: Designing the small icons that depict documents and files.
source_url: https://develop.kde.org/hig/icons/monochrome/mimetype/
source_authors: [Carl Schwan, Johannes Zarl-Zierl, John Veness, Nate Graham]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver-icons icons/mimetypes (size folders)"
---

# Monochrome MIME type icons

MIME type icons are used to depict documents and files. They come in four sizes: 16px, 22px, 32px, and 64px. MIME type icons use the [monochrome style](index.md) for 16px and 22px sizes, and the [colorful style](../colorful/index.md) for 32px and 64px sizes.

Unlike most monochromatic icons, MIME type icons use the primary color of their colorful counterpart.

## Purpose

MIME type icons allow a user to quickly recognize the types of their files without needing to look at a file's extension or contents. They primarily appear in file listings in large amounts, and their design reflects a sense of unity among files in a user's system.

## Design

### Iconography

MIME type icons use bold and recognizable symbols that allow a user to determine the filetype at a glance.

![A green spreadsheet icon](../../images/mono-mime-do.png)

**Do:** Use a bold and recognizable icon.

![An empty green square](../../images/mono-mime-dont.png)

**Don't:** Don't use an overly generic icon. This makes it hard for users to determine filetype.

MIME types associated with a brand identity use elements of their brand to make it easier for users to connect the icon to its filetype.

![The RSS symbol](../../images/mono-mimebrand-rss.png)

The usage of the RSS icon allows users to recognize the RSS feed MIME type.

![The Debian logo](../../images/mono-mimebrand-deb.png)

The usage of the Debian logo allows users to recognize the deb package MIME type.
