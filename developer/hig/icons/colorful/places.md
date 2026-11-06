---
title: Colorful places icons
description: The anatomy and margins of large places icons.
source_url: https://develop.kde.org/hig/icons/colorful/places/
source_authors: [Carl Schwan, John Veness, Nate Graham, Phu Nguyen]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver-icons icons/places (size folders; ColorScheme-Accent in 32/folder.svg, 32/folder-documents.svg and 64/folder.svg)"
---

# Colorful places icons

Places icons are used to depict folders, network locations, and other places. They are mainly drawn at four sizes: 16px, 22px, 32px, and 64px. Places icons use the [monochrome style](../monochrome/index.md) for 16px and 22px sizes, and the [colorful style](index.md) for 32px and larger.

## Purpose

Places icons allow a user to quickly identify landmarks in their filesystems. They indicate places that a user will visit frequently, such as home, root, downloads, etc.

## Design

### Anatomy

Colorful places icons consist of two elements: the monochromatic counterpart of the colorful places icon overlaid on a folder background.

![A folder icon with its two parts numbered](../../images/place-anatomy.png)

1. Folder
2. Monochromatic foreground

![The folder alone](../../images/place-anatomy-base.png)

The base of a places icon indicates that it's a folder that can be navigated to.

![The foreground symbol on the folder](../../images/place-anatomy-fg.png)

The foreground of a places icon indicates the folder's landmark location.

### Base

The base of a places icon is always a folder. It's drawn with the `ColorScheme-Accent` style class so that it follows the user's accent color, which is blue in the examples here.

![An empty blue folder](../../images/place-blank.png)

### Foreground

The foreground of a places icon indicates the landmark location an icon represents. Its color is a darker variant of the base's color. For 32px icons, its size is 10×10px. For 64px icons, its size is 20×20px. It is always centered within the folder, and does not cast a shadow.

![A folder with a foreground symbol and no shadow](../../images/place-fg-do.png)

**Do:** The foreground of a places icon does not cast a shadow.

![A folder with a foreground symbol casting a shadow](../../images/place-fg-dont.png)

**Don't:** Don't have the foreground of a places icon cast a shadow.

### Margins

64px places icons have a top and bottom margin of 6 pixels, and 32px places icons have a top and bottom margin of 3 pixels.

![A 64px folder with its margins marked](../../images/place-margin-64.png)

64px icons should have a top and bottom margin of 6 pixels.

![A 32px folder with its margins marked](../../images/place-margin-32.png)

32px icons should have a top and bottom margin of 3 pixels.
