---
title: Application menus in window decorations
description: How a window decoration theme shows an application's menus in its titlebar with KDecoration3::TitleBarMenu.
checked_against: "sonic-decoration src/titlebarmenu (titlebarmenu.h, titlebarmenufactory.h, titlebarmenuitem.h) and sonic-silver kdecoration (breezedecoration.cpp, breezetitlebarmenuitem.cpp, breezebutton.cpp), run in a private SonicWin session"
---

# Application menus in window decorations

A window decoration can show the application's menus (File, Edit, View…) in its titlebar, at the
place of the **Application menu** button. SonicDE's `KDecoration3::TitleBarMenu` library does the
work: it imports the menu the application exports over D-Bus, lays out one label per menu, opens
the popups, moves between them with the keyboard and the pointer, and offers a search. The theme
draws the labels in its own style and gives them room in its layout. Silver uses it.

The user chooses how the menus appear in **Window Decorations → Configure Titlebar…**. The setting
reaches the decoration as `DecorationSettings::applicationMenuStyle()` (`SingleButton`,
`AlwaysShown` or `ShownOnHover`) and `DecorationSettings::isApplicationMenuSearchEnabled()`.
`TitleBarMenu` follows both.

## Declaring support

Add `"X-SonicDE-TitleBarMenu": true` at the top level of the plugin's metadata JSON, next to
`"KPlugin"`. Without it, the settings page greys the options out for your style.

Link the library in CMake:

```cmake
find_package(KDecoration3 REQUIRED)
target_link_libraries(mydecoration PRIVATE KDecoration3::KDecoration KDecoration3::TitleBarMenu)
```

The library is GPL-2.0-or-later, so the decoration plugin must be GPL-compatible.

## Creating the menu

Create one `TitleBarMenu` per decoration, after your button groups, and anchor it to the
`ApplicationMenu` button:

```cpp
#include <KDecoration3/TitleBarMenu>

m_titleBarMenu = new KDecoration3::TitleBarMenu(this, std::make_unique<MyTitleBarMenuFactory>());
connect(settings().get(), &KDecoration3::DecorationSettings::decorationButtonsLeftChanged, this, &MyDecoration::updateAnchor);
connect(settings().get(), &KDecoration3::DecorationSettings::decorationButtonsRightChanged, this, &MyDecoration::updateAnchor);
updateAnchor(); // finds the ApplicationMenu button in either group and calls m_titleBarMenu->setAnchor()
```

Make those connections after creating the groups: groups made from the settings delete and
recreate their buttons when the layout changes, so the new button must be looked up again.
`setAnchor()` disables the anchor, so the decoration sends it no clicks and the old single-button
popup never opens; the anchor stays in its group as a placeholder. With no anchor, or a hidden one
(the window has no menu), the menu has no buttons.

`TitleBarMenu` also takes over `Decoration::showApplicationMenu()` (the application asking to
open its menu from the keyboard) through `Decoration::setApplicationMenuHandler()` while it has an
anchor.

## Drawing the buttons

The `TitleBarMenuFactory` you pass creates the buttons:

- `createItem()` returns a `TitleBarMenuItem`, one label per top-level menu. Subclass it and
  override `paint()`; `text()`, `isHovered()`, `isPressed()`, `isChecked()` (its popup is open)
  and `isDimmed()` (another label's popup is open) tell you what to draw. While a popup holds the
  pointer, hover states go stale, so ignore hover when `isDimmed()` is true.
  `horizontalPadding()` sets the space around the text.
- `createOverflowButton()` and `createSearchButton()` may return any `DecorationButton` of type
  `DecorationButtonType::Custom`, created with `menu->decoration()` and `menu` as its parent, so you
  can reuse your own button class. Silver returns its own `Button` drawn like its Application menu
  button.

The default factory draws plain text and the `application-menu` and `edit-find` icons.

## Layout

In your button layout code:

1. Size the anchor as you'd size any button, remember that size for the menu's icon buttons, and
   set the anchor's width to 0.
2. Place your groups as usual.
3. Work out the room for the menu: the space between the groups, minus a minimum width for the
   title. Call `m_titleBarMenu->updateItemsGeometry(QRectF(anchorX, anchorY, room, anchorHeight),
   iconButtonSize)`. A null rectangle hides everything, for example when the titlebar is hidden.
4. Set the anchor's width to `visibleItemsWidth()`; its group lays the other buttons out again. If
   the anchor is in a group positioned from its right edge, place that group again.
5. Move the menu onto the anchor with `m_titleBarMenu->setPos()`.

Lay out again when `visibleItemsWidthChanged()` or `itemsChanged()` fires, and when the two
settings change (the settings preview changes them without emitting `reconfigured()`).

In Silver, see `Decoration::updateButtonsGeometry()` in `breezedecoration.cpp`.

## Painting and events

- Paint the menu after your groups: `m_titleBarMenu->paint(painter, repaintRegion)`. It applies its
  own opacity, which is below 1 only in `ShownOnHover`.
- In `ShownOnHover`, the title fades out as the menu fades in: draw the caption with
  `1 - m_titleBarMenu->opacity()` and repaint on `opacityChanged()`.
- Report whether the pointer is over the titlebar with `setHovered()`, from `hoverMoveEvent()` and
  `hoverLeaveEvent()`.
- The decoration already sends hover, press and release events to the menu's buttons. To let users
  move the window by dragging on the menu, and to keep middle and right clicks for the titlebar,
  un-accept those presses in `mousePressEvent()` and call `releaseAllItems()` once a left press
  turns into a drag. Leave wheel events over the menu unaccepted so the titlebar's wheel action
  applies.

## Testing

`sonic-decoration/autotests/titlebarmenutest.cpp` drives a `TitleBarMenu` with mock windows and an
in-process menu (`model()->setLocalMenu()`); `titlebarmenudbustest.cpp` imports a real menu from a
fake application on a private D-Bus session.
