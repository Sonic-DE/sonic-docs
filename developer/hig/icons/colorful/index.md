---
title: Colorful icons
description: Margins, anatomy, color, layers and shadows of colorful icons.
source_url: https://develop.kde.org/hig/icons/colorful/
source_authors: [Carl Schwan, Janet Blackquill, Johannes Zarl-Zierl, John Veness, Joshua Wug, Nate Graham, Tem PQD]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver-icons (size folders of apps, categories, preferences, mimetypes, places, devices and status)"
---

# Colorful icons

![A row of colorful icons](../../images/Sample_color_icons.png)

Colorful icons make full use of the Silver color palette. Colorful icons are not flat and incorporate elevation, shadows, and lighting.

![An icon with depth](../../images/anjuta-deep.png)

**Do:** Use a variety of techniques to give your icon depth.

![A flat icon](../../images/anjuta-flat.png)

**Don't:** Don't make your icon flat. This makes it visually bland.

There are a variety of colorful icon types:

- 32px: [Category, Preferences](category-preferences.md), [MIME type](mimetype.md), and [Places](places.md) icons
- 48px: [Application](application.md) icons
- 64px: [MIME type](mimetype.md), [Places](places.md), Devices, and a few Status icons

## Margins

### Vertical

Colorful icons have a top and bottom margin of 4 pixels. Icons should not put any details here whatsoever.

![Anjuta icon with 4px top and bottom margins. The icon does not enter the margins.](../../images/anjuta-margin-horiz.png)

### Horizontal

Colorful icons also have a left and right margin of 4 pixels. Minor details can extend here as necessary.

![Anjuta icon with 4px left and right margins. The circle's edges extend into the margin.](../../images/anjuta-margin-vert.png)

### 32px colorful icons

32px colorful icons have a 2px margin instead of 4px margins.

![A 32px icon with 2px margins](../../images/small-margin-do.png)

**Do:** Use 2px margins on 32px colorful icons.

![A 32px icon with 4px margins](../../images/small-margin-dont.png)

**Don't:** Don't use 4px margins on 32px colorful icons; this reduces the canvas size too much.

## Anatomy

All colorful icons share the same basic anatomy.

![An icon with its four parts numbered](../../images/anjuta-anatomy.png)

1. Foreground
2. Foreground shadow
3. Base
4. Base shadow

![The foreground alone](../../images/anjuta-foreground.png)

The foreground of an icon is the distinctive part that conveys the most branding.

![The foreground shadow alone](../../images/anjuta-foreground-shadow.png)

Foregrounds on a background have a 45° shadow to the bottom right that spans the entire background.

![The background alone](../../images/anjuta-background.png)

Icons can have a background to serve as a base for their foreground.

![The background shadow alone](../../images/anjuta-background-shadow.png)

The foreground, or the background if there is one, has a 1px hard shadow on the bottom.

## Elements

### Color

Icons can have a variety of shapes, which when combined with color, produce numerous unique arrangements.

![An icon with a colored area and no shadow on it](../../images/color-do.png)

**Do:** Color can be used to add variety to an otherwise bland surface.

![An icon with shadows cast by a colored area](../../images/color-dont.png)

**Don't:** Don't give color shadows; color is not shape and should not be treated as such.

### Layers

Icons are composed of layers that cast shadows.

![An icon with a few layers](../../images/layer-do.png)

**Do:** Give icons at most two or three major layers.

![An icon with many layers](../../images/layer-dont.png)

**Don't:** Don't give icons too many layers.

### Lighting and shadows

#### Ambient lighting

Icon fills should reflect ambient lighting, going from a lighter top to a darker bottom.

![A gradient that is lighter at the top](../../images/lighting-gradient-do.png)

**Do:** Have gradients behave like light is coming from above the icon.

![A gradient that is lighter at the bottom](../../images/lighting-gradient-dont.png)

**Don't:** Don't have gradients behave like light is coming from below the icon.

#### Hard shadow

Every icon should have a 1px solid hard shadow. A good baseline color to overlay is black (`#000000`) at 10% opacity.

![An icon with a hard shadow](../../images/hardshadow-do.png)

**Do:** Add a 1px hard shadow to give your icon depth.

![An icon without a hard shadow](../../images/hardshadow-dont.png)

**Don't:** Don't forget to add a hard shadow; this makes your icon seem flat.

#### 45° shadows

Foregrounds should have a 45° shadow to the bottom right.

![A shadow blocked by an object in its way](../../images/45shadow-do.png)

**Do:** Objects are solid, and block shadows from passing through.

![A shadow passing through an object](../../images/45shadow-dont.png)

**Don't:** Don't have shadows pass through objects; they are not glass.

![A shadow kept inside its parent shape](../../images/bound-do.png)

**Do:** 45° shadows are bounded to their parent elements.

![A shadow going past its parent shape](../../images/bound-dont.png)

**Don't:** 45° shadows should not exceed the bounds of their parents.

![A shadow fading out before the edge](../../images/gradient-do.png)

**Do:** 45° shadows have a gradient that fades out before they hit an edge.

![A solid shadow reaching the edge](../../images/gradient-dont.png)

**Don't:** 45° shadows are not solid and do not extend to the edge of their parents.
