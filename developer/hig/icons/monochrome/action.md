---
title: Action icons
description: Designing the icons that depict actions.
source_url: https://develop.kde.org/hig/icons/monochrome/action/
source_authors: [Carl Schwan, Damy Metzke, Johannes Zarl-Zierl, John Veness, Nate Graham]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver-icons icons/actions (size folders, ColorScheme-Text in list-add.svg, #da4453 in edit-delete.svg)"
---

# Action icons

Action icons are used to depict actions. They are mainly drawn at two sizes, 16px and 22px, and always use the [monochrome style](index.md).

## Purpose

Action icons indicate actions that a user is able to take on on-screen elements. They allow a user to intuit the behavior of controls.

## Design

### Color

Action icons should use a base color of Shade Black. Additional colors can indicate information about an action to a user.

![A black folder icon with a plus emblem](../../images/action-colour-do.png)

**Do:** Use Shade Black as your icon's base. This color is neutral and has the most contrast against a white background.

![An entirely orange icon](../../images/action-colour-dont.png)

**Don't:** Don't use a bright color for your icon's base. This distracts the user without adding extra information to your icon.

![A red trash can icon](../../images/action-colour-destructive-do.png)

**Do:** Use red to indicate destructive actions.

![A red emblem on a non-destructive action](../../images/action-colour-destructive-dont.png)

**Don't:** Don't use red to indicate other types of actions. This will confuse the user as to what the actions do.

![A folder icon that is black on a light background and white on a dark one](../../images/action-colour-adaptable.png)

Action icons are able to dynamically change their color based on context.

Implementation details can be found in the [Icon Workflow Tips](https://community.kde.org/Guidelines_and_HOWTOs/Icon_Workflow_Tips#Embedding_stylesheets_in_SVGs).

### Metaphor

Appropriate and consistent metaphors should be used to inform a user about the action an icon represents.

![Icons with fitting metaphors](../../images/action-metaphor-do.png)

**Do:** Use appropriate metaphors to indicate what an action does.

![Icons with conflicting metaphors](../../images/action-metaphor-dont.png)

**Don't:** Don't use inaccurate or conflicting metaphors. This will mislead your user and lead to frustration.

## Accessibility

When using action icons to indicate an action, a textual name and description of the action should be provided for accessibility purposes. Screen readers can take advantage of this information to allow more people to use your application. Your local jurisdiction may also require that your application meet accessibility standards. Care should also be taken to reinforce information conveyed by an icon in multiple ways, as not everyone is able to distinguish between all colors.

![A trash can described as Delete: deletes the selected item](../../images/action-accessibility-do.png)

**Do:** Provide a name and description that describe what an icon's action does.

![A trash can described as Trash Can: the trash can has a lid](../../images/action-accessibility-dont.png)

**Don't:** Don't describe the icon's appearance. This is useless information that will make your application harder to use.

![Folder icons that differ by shape as well as color](../../images/action-accessibility-color-do.png)

**Do:** Reinforce information in multiple ways to allow users with conditions such as colorblindness to get the message.

![Folder icons that differ only by color](../../images/action-accessibility-color-dont.png)

**Don't:** Don't only rely on color to convey information. This makes it harder for users with colorblindness to distinguish two like icons apart.
