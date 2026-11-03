---
title: "Obsolete Members for KHelpMenu"
description: "Deprecated members of KHelpMenu."
parent: "kxmlgui/khelpmenu"
---

# Obsolete Members for KHelpMenu

**The following members of class [KHelpMenu](khelpmenu.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [KHelpMenu(QWidget \*parent, const QString &unused, bool showWhatsThis = true)](#KHelpMenu-2) (deprecated in 6.9)
- [KHelpMenu(QWidget \*parent, const KAboutData &aboutData, bool showWhatsThis)](#KHelpMenu-3) (since 6.9)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[explicit, deprecated in 6.9\] KHelpMenu::KHelpMenu(QWidget \**parent*, const QString &*unused*, bool *showWhatsThis* = true) {#KHelpMenu-2}

This function is deprecated since 6.9. We strongly advise against using it in new code.

Construct a new help menu dialog.

`parent` The parent of the dialog boxes. The boxes are modeless and will be centered with respect to the parent.

`aboutAppText` User definable string that is used in the default application dialog box.

`showWhatsThis` Decides whether a "What's this" entry will be added to the dialog.

Use one of the other constructors

### \[deprecated in since 6.9\] KHelpMenu::KHelpMenu(QWidget \**parent*, const KAboutData &*aboutData*, bool *showWhatsThis*) {#KHelpMenu-3}

This function is deprecated since since 6.9. We strongly advise against using it in new code.

Constructor.

This overload is mainly useful if you want to override the standard actions [aboutApplication](khelpmenu.md#aboutApplication)(), [aboutKDE](khelpmenu.md#aboutKDE)(), and [reportBug](khelpmenu.md#reportBug)().

`parent` The parent of the dialog boxes. The boxes are modeless and will be centered with respect to the parent.

`aboutData` User and app data used in the About app dialog.

`showWhatsThis` Decides whether a "What's this" entry will be added to the dialog.

Use one of the other constructors

This function overloads [KHelpMenu::KHelpMenu(QWidget \*parent, const QString &aboutAppText, bool showWhatsThis)](khelpmenu-obsolete.md#KHelpMenu-2).
