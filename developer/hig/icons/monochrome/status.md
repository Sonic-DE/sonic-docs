---
title: Status icons
description: Designing the icons that show the state of hardware and software.
source_url: https://develop.kde.org/hig/icons/monochrome/status/
source_authors: [Carl Schwan, Johannes Zarl-Zierl, John Veness, Nate Graham]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver-icons icons/status (size folders)"
---

# Status icons

Status icons are used to indicate the status of hardware and software. They are mainly drawn at 16px and 22px, and use the [monochrome style](index.md). A few status icons also exist at 32px and 64px.

## Purpose

Status icons allow a user to discern the current state of hardware and software at a glance. They reassure users that software is functional, and warn them when hardware is dysfunctional.

## Design

### Anatomy

#### Base

The base of a status icon indicates to the user what item the state of the icon represents.

![A microphone and a monitor icon](../../images/status-base-do.png)

**Do:** Use a simple and recognizable icon base that leaves room for additions to indicate state.

![A shapeless icon and an overly detailed icon](../../images/status-base-dont.png)

**Don't:** Don't use an overly simple base. This makes it hard for the user to identify what an icon represents. Additionally, don't use more details than you need to make something recognizable. This doesn't leave you room for indicating states.

#### Overlay

The overlay of a status icon indicates to the user what status the item the icon represents is in.

![A microphone icon with a red slash](../../images/status-overlay-do.png)

**Do:** Use a simple and recognizable overlay with appropriately used color to clue in the user to an icon's status.

![Play and stop symbols on their own](../../images/status-caution.png)

**Caution:** Some overlays can be hard to identify on their own. Provide appropriate context to allow a user to identify what a simple icon represents.

![A plain microphone icon next to a red one](../../images/status-overlay-dont-color.png)

**Don't:** Don't exclusively rely on color to indicate state. This is an accessibility problem and makes it hard to discern state.

![Monitor icons that differ only by a small dot](../../images/status-overlay-dont-detail.png)

**Don't:** Don't use too-generic details to represent state. This makes it hard for a user to identify what an icon's state represents.
