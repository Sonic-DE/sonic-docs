---
title: "KXmlGui C++ Classes"
description: "KXmlGui is a collection of convenience classes and widgets to manage your own main QtWidgets window."
---

# KXmlGui C++ Classes

[KXmlGui](kxmlgui-module.md) is a collection of convenience classes and widgets to manage your own main [QtWidgets](https://doc.qt.io/qt-6/qtwidgets-module.html) window. [More...](#details)

## Namespaces {#namespaces}

- [KUndoActions](kundoactions.md): Provides functions that creates undo/redo actions for a QUndoStack with KDE's default icons and shortcuts.

## Classes {#classes}

- [KAboutApplicationDialog](kaboutapplicationdialog.md): Standard "About Application" dialog box.
- [KActionCategory](kactioncategory.md): Categorize actions for KShortcutsEditor.
- [KActionCollection](kactioncollection.md): A container for a set of QAction objects.
- [KBugReport](kbugreport.md): A dialog box for sending bug reports.
- [KEditToolBar](kedittoolbar.md): A dialog used to customize or configure toolbars.
- [KHelpMenu](khelpmenu.md): Standard KDE help menu with dialog boxes.
- [KKeySequenceWidget](kkeysequencewidget.md): A widget to input a QKeySequence.
- [KMainWindow](kmainwindow.md): KMainWindow represents a top-level main window.
- [KShortcutWidget](kshortcutwidget.md)
- [KShortcutsDialog](kshortcutsdialog.md): Dialog for configuration of KActionCollection and KGlobalAccel.
- [KShortcutsEditor](kshortcutseditor.md): Widget for configuration of KAccel and KGlobalAccel.
- [KToggleToolBarAction](ktoggletoolbaraction.md)
- [KToolBar](ktoolbar.md): Floatable toolbar with auto resize.
- [KToolBarEditor](ktoolbareditor.md): The toolbar editing of KEditToolBar, without widgets.
- [KToolTipHelper](ktooltiphelper.md): An event filter used to enhance tooltips.
- [KXMLGUIBuilder](kxmlguibuilder.md)
- [KXMLGUIClient](kxmlguiclient.md)
- [KXMLGUIFactory](kxmlguifactory.md)
- [KXmlGuiWindow](kxmlguiwindow.md): KMainWindow with convenience functions and integration with XmlGui files.

## Detailed Description {#details}

A window can be created using [KXmlGuiWindow](kxmlguiwindow.md) and [KMainWindow](kmainwindow.md).

Shortcuts can be centrally managed using [KActionCollection](kactioncollection.md).

The actions are configured through a XML description and hooks in the application code. The framework supports merging of multiple description for example for integrating actions from plugins.

KXMLGui makes use of the Kiosk authorization functionality of [KConfig](../kconfigcore/kconfig.md) (see the [KAuthorized](../kconfigcore/kauthorized.md) namespace in that framework). Notably, [QAction](https://doc.qt.io/qt-6/qaction.html) instances added to a [KActionCollection](kactioncollection.md) are disabled if [KAuthorized::authorizeAction](../kconfigcore/kauthorized.md#authorizeAction)() reports that they are not authorized. The items on the standard help menu ([KHelpMenu](khelpmenu.md)) can likewise be disabled based on Kiosk settings, and toolbar editing can be restricted.

See [KActionCollection](kactioncollection.md), [KHelpMenu](khelpmenu.md) and [KToolBar](ktoolbar.md) documentation for more information.
