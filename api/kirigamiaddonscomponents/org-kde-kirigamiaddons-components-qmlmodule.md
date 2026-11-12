---
title: "Kirigami Addons Components QML Types"
description: "Reusable controls and visual components for Kirigami applications."
---

# Kirigami Addons Components QML Types

Reusable controls and visual components for Kirigami applications.

Use [Avatar](qml-org-kde-kirigamiaddons-components-avatar.md) to represent a person with a profile image, initials, or an icon. [ConvergentContextMenu](qml-org-kde-kirigamiaddons-components-convergentcontextmenu.md) presents actions as a menu on desktop and as a bottom drawer on mobile. [MessageDialog](qml-org-kde-kirigamiaddons-components-templates-messagedialog.md) displays success, warning, error, and information messages, with an optional "Don't show again" choice. [FloatingToolBar](qml-org-kde-kirigamiaddons-components-templates-floatingtoolbar.md) places tools over content, while [FloatingButton](qml-org-kde-kirigamiaddons-components-templates-floatingbutton.md) and [DoubleFloatingButton](qml-org-kde-kirigamiaddons-components-templates-doublefloatingbutton.md) provide prominent page actions.

Import the module in the QML files that use these components:

```qml
import org.kde.kirigamiaddons.components as Components

Components.Avatar {
    name: i18nc("@info:person", "Alex Doe")
}
```

- [Avatar](qml-org-kde-kirigamiaddons-components-avatar.md): An element that represents a user, either with initials, an icon, or a profile image.
- [AvatarButton](qml-org-kde-kirigamiaddons-components-avatarbutton.md): An button that represents a user, either with initials, an icon, or a profile image.
- [BottomDrawer](qml-org-kde-kirigamiaddons-components-bottomdrawer.md): A bottom drawer component with a drag indicator.
- [ConvergentContextMenu](qml-org-kde-kirigamiaddons-components-convergentcontextmenu.md): A context menu that can appear as a standard menu, bottom drawer, or dialog.
- [DialogRoundedBackground](qml-org-kde-kirigamiaddons-components-dialogroundedbackground.md): Stylish background for dialogs.
- [DoubleFloatingButton](qml-org-kde-kirigamiaddons-components-doublefloatingbutton.md): This component allows one to display two buttons at the bottom of a page.
- [FloatingButton](qml-org-kde-kirigamiaddons-components-floatingbutton.md): This component is a button that can be displayed at the bottom of a page.
- [FloatingToolBar](qml-org-kde-kirigamiaddons-components-floatingtoolbar.md): A floating toolbar to use for example in a canvas.
- [MessageDialog](qml-org-kde-kirigamiaddons-components-messagedialog.md): A message dialog with success, warning, error, and information styles.
- [RadioSelector](qml-org-kde-kirigamiaddons-components-radioselector.md): A Component that allows switching between multiple options.
- [SegmentedButton](qml-org-kde-kirigamiaddons-components-segmentedbutton.md): Segmented button component.
