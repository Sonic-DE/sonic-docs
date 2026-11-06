---
title: Layout and navigation
description: Positioning, standard sizes, responsive layouts, menus and navigation.
source_url: https://develop.kde.org/hig/layout_and_nav/
source_authors: [Darshan Phaldesai, Janet Blackquill, John Veness, Joshua Goins, Kristen McWilliam, Nate Graham, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-quick-ui units.cpp and tabletmodewatcher.cpp, sonic-desktop-interface kcms/workspaceoptions; Units, Settings.tabletMode, Settings.isMobile and -reverse run on the stage build"
---

# Layout and navigation

## Positioning

Convey importance, workflow, and grouping by placing items strategically.

People read layouts in the order they read words in their language; users will pay more attention to items near the top-leading position (i.e. top-left in a language like English, and top-right in a language like Arabic), and consider them to be the first items to focus on. Similarly, users will perceive items in the bottom-trailing position as being the final thing to do before moving on.

One exception is on a mobile phone, where the most commonly used tools live in a bottom toolbar. This improves acquisition speed by making them thumb-reachable without re-positioning the hand.

Group related items together by reducing the spacing between them, and increasing the spacing between groups. Make sure items that _look_ grouped are in fact logically related.

## Spacings and sizes

Use the Kirigami [standard units](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units) consistently:

| Item | Value to use |
| --- | --- |
| Spacing between title and subtitle text | 0 |
| Spacing between title/subtitle groups and other content below them | `smallSpacing` |
| Spacing between other directly related items, or controls sharing a logical group | `smallSpacing` |
| Spacing between groups of controls or text | `largeSpacing` |
| Spacing between items in a toolbar (e.g. buttons and text fields) | `mediumSpacing` |
| Padding between window/page edges and “frameless” container views | 0 |
| Padding between window/page edges and all other UI elements | `largeSpacing` |
| Corner radius for rounded UI elements | `cornerRadius` |
| Fixed-size UI elements, including default and minimum window sizes | `gridUnit` (18 px) multiplied as needed |
| Size of icons in menu items and raised buttons | `iconSizes.small` |
| Size of icons in flat/toolbar buttons and list items without subtitles | `iconSizes.smallMedium` |
| Size of icons in list items with subtitles | `iconSizes.medium` |

## Common layouts and responsiveness

SonicDE applications commonly consist of layout elements such as a main content area, a sidebar used for navigation, a toolbar displaying actions contextually relevant to what's shown in the content view, a menu of globally-scoped actions, and more.

These layout elements must adapt fluidly to diverse screen sizes and window shapes. Even on the desktop, users may resize your application's window to be small and narrow. Adapt the window content in sane and sensible ways when maximized, tiled, or otherwise used at a different size or shape than how it was originally designed.

Here are the ways that common layout elements, when present, should move or change in different circumstances:

| Item | Desktop/widescreen | Mobile/narrow |
| --- | --- | --- |
| Toolbar | Above the content area | Below the content area |
| Sidebar | Leading the content area | Visible on demand in the leading position, or the first page in a page stack |
| Contextual preview/tool view | Trailing the content area | Visible on demand in the trailing position |
| Menubar | Above the toolbar | Hamburger menu button on the toolbar |
| Navigation tab bar | Above the content area | Below the content area |
| Status bar | Below the content area | Omitted |

[Kirigami.GlobalDrawer](../kirigami/drawers.md) is a useful component for convergent applications. It looks like a standard sidebar, and can be made always visible in widescreen/desktop mode by setting `modal: false`. In narrow/mobile mode, users pull it out on demand. [Kirigami.ContextDrawer](../kirigami/drawers.md) is the same but for contextual actions relevant only for individual pages.

Desktop and laptop applications can be adapted to work on tablets and 2-in-1 laptops in tablet mode by enlarging small UI elements and hiding menubars. Phones (even large ones) need an optimized mobile UI; do not just scale down a desktop UI.

> **Note:** Detect that the application is running in tablet mode by reading [Kirigami.Settings.tabletMode](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-settings#tabletMode-prop). To test it, set “Enable Tablet Mode” to “Always enabled” on System Settings' General Behavior page, or run your application with the `KDE_KIRIGAMI_TABLET_MODE=1` environment variable.
>
> Detect that the application is running on a mobile phone by reading [Kirigami.Settings.isMobile](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-settings#isMobile-prop). Set the `QT_QUICK_CONTROLS_MOBILE=1` environment variable to test your application in a simulated mobile mode.

In addition, offer a good experience for laptop users by keeping these points in mind:

- Implement “pixel-by-pixel” scrolling for touchpad two-finger scroll gestures, instead of jumping a certain number of rows.
- Set shortcuts using modifier and alphanumeric keys; never just a function key, as these can be hard to access on laptops.

For QtWidgets applications, the [KXmlGui](../kxmlgui/index.md) GUI layout library is recommended. Sidebars can be implemented using [QDockWidget](https://doc.qt.io/qt-6/qdockwidget.html).

## Menus

Menus are drop-down lists of actions the user can perform.

Small or focused applications often need no menu structures at all, because all of their actions are visible on demand in contextual toolbars or inline on content items.

In small- and medium-sized applications, it's common for a curated set of globally-scoped actions to be visible in a “hamburger menu:” a menu that appears when clicking on a button located on the application's toolbar with the `application-menu` icon. Its contents are static and globally-scoped, with contextually irrelevant items disabled rather than being hidden.

Don't put standard application and window management actions like “Quit” and “Minimize” in a hamburger menu.

Only show a hamburger menu by default if its contents can be kept to about 15 items or fewer. If you are tempted to add more than this, a hamburger menu is the wrong UI element for your application; instead place a real menubar between the titlebar and toolbar. Like the hamburger menu, its contents are static and disabled when not relevant, rather than hidden. The major difference is that the menubar shows all possible actions in the application, so users can access any of them at any time.

In a QtWidgets application, use [KHamburgerMenu](/docs/api/kconfigwidgets/khamburgermenu) to give a medium-to-large application both a menu bar and a hamburger menu. Choose a curated list of the most important actions for the hamburger menu, which will appear when the menubar is hidden.

## Navigation

Strive to minimize navigation as a chore for users to succeed at before they can get to what they want. The best navigational flow is nonexistent, because everything is provided to the user as they need it.

Linear navigation works well for applications that have a step-by-step workflow with clear starting and ending points. Use the standard [page stack](../kirigami/page-row-and-page-stack.md) mechanism built into Kirigami for this navigation model, with breadcrumbs and back/forward buttons in the toolbar for navigation.

For applications with multiple destinations not arranged in a linear flow, implement a dedicated navigational control to let the user jump from one destination to another. With five or fewer destinations, use a [Kirigami.NavigationTabBar](/docs/api/kirigami/qml-org-kde-kirigami-navigationtabbar).

Otherwise, use a [Kirigami.GlobalDrawer](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer) to display the navigation destinations.

Regardless of which navigational control is used, ensure that the view your application shows at launch is represented as its first item so users can easily get there again.

## Tools and functionality

When a content view needs controls specific to it that for some reason cannot be provided by the main toolbar, place them in a secondary toolbar underneath the main toolbar.

Many applications also feature auxiliary “Contextual Toolviews.” These can show previews or information about what's displayed or selected in the main content area, or extra tools to interact with it.

Show these views in addition to the global-scope navigation UI; don't replace it. The only exception is when the navigation view is itself already contextual (e.g. a thumbnail view for the open document in a PDF reader application); in this case the contextual navigation can be integrated into a tabbed/multi-view sidebar that shows different contextual views for the visible content.

## Right-to-left languages

People using the software in right-to-left languages like Arabic and Hebrew expect for layouts to reverse direction.

This works automatically for items using anchor-based positioning or Qt Layout objects such as `RowLayout` and `ColumnLayout`, but it's important to check things yourself. Run your application with Qt's `-reverse` option to test it in right-to-left mode without changing its language.

In addition to layout objects reversing their horizontal positioning, make sure text alignment has reversed too.

Manually reverse any custom controls that show progress of directionality, for example star-rating widgets or sliders with custom visual styling.

When using icons that indicate directionality or depict layouts or textual elements, use the reversed versions that are suffixed with `-rtl`. Information on designing reversed icons can be found in the [Icon localization guidelines](icons/localization.md).

Don't mirror images.

For more information, see the [Qt documentation on right-to-left user interfaces](https://doc.qt.io/qt-6/qtquick-positioning-righttoleft.html).
