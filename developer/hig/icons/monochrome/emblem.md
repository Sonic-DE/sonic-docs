---
title: Emblem icons
description: Designing the small icons overlaid on other icons to show state.
source_url: https://develop.kde.org/hig/icons/monochrome/emblem/
source_authors: [Carl Schwan, Chris Holland, Johannes Zarl-Zierl, John Veness, Kunda Ki, Nate Graham, Tem PQD]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver-icons icons/emblems (8, 16 and 22 folders; 0.6 outline opacity in the 16 and 22 emblem-checked.svg, none at 8)"
---

# Emblem icons

Emblem icons are used to indicate state. They come in three sizes: 8px, 16px, and 22px, and always use the [monochrome style](index.md). They are typically overlaid on icons. Unlike most monochromatic icons, emblem icons use bright colors to remain recognizable, even at small sizes.

## Purpose

Emblem icons are used alongside a base icon to form compound icons that convey additional information on top of the base icon, indicating its status, such as missing, deleted, etc.

## Design

### Anatomy

Emblem icons always use the entire canvas area. Pixel alignment is especially important for emblem icons as they are rendered at very small sizes, making the consequences of pixel misalignment more noticeable than at other sizes.

![A pixel-aligned emblem filling its canvas](../../images/8px-emblem-do.png)

**Do:** Pixel-align your icon and use the entire canvas.

![A misaligned emblem with margins](../../images/8px-emblem-dont.png)

**Don't:** Don't misalign your icon or use margins.

16px and 22px emblem icons get a 60% opacity text color outline to ensure contrast against various backgrounds. 8px emblems do not receive an outline because of their limited canvas size.

![A 22px emblem with an outline](../../images/22-emblem-outline.png)

16px and 22px emblem icons get an outline to increase visibility on various backgrounds.

![An 8px emblem without an outline](../../images/8-emblem-outline.png)

8px emblem icons need to rely on bold shapes and bright colors for visibility, as they don't have room for an outline.
