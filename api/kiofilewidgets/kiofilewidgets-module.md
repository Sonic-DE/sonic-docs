---
title: "KIO FileWidgets C++ Classes"
description: "Widgets for File Management."
---

# KIO FileWidgets C++ Classes

Widgets for File Management. [More...](#details)

## Classes {#classes}

- [KAbstractViewAdapter](kabstractviewadapter.md): Interface used by KFilePreviewGenerator to generate previews for files.
- [KDirOperator](kdiroperator.md): A widget for displaying files and browsing directories.
- [KDirSortFilterProxyModel](kdirsortfilterproxymodel.md): Acts as proxy model for KDirModel to sort and filter KFileItems.
- [KFileCopyToMenu](kfilecopytomenu.md): This class adds "Copy To" and "Move To" submenus to a popupmenu.
- [KFileCustomDialog](kfilecustomdialog.md): This class implement a custom file dialog.
- [KFileFilterCombo](kfilefiltercombo.md): File filter combo box.
- [KFilePlacesModel](kfileplacesmodel.md)
- [KFilePlacesView](kfileplacesview.md): This class allows to display a KFilePlacesModel.
- [KFilePreviewGenerator](kfilepreviewgenerator.md): Generates previews for files of an item view.
- [KFileWidget](kfilewidget.md): File selector widget.
- [KImageFilePreview](kimagefilepreview.md): Image preview widget for the file dialog.
- [KNameAndUrlInputDialog](knameandurlinputdialog.md): Dialog to ask for a name (e.g. filename) and a URL.
- [KNewFileMenu](knewfilemenu.md): The 'Create New' submenu, for creating files using templates (e.g. "new HTML file") and directories.
- [KPreviewWidgetBase](kpreviewwidgetbase.md): Abstract baseclass for all preview widgets.
- [KUrlNavigator](kurlnavigator.md): Widget that allows to navigate through the paths of an URL.

## Detailed Description {#details}

The [KIOFileWidgets](kiofilewidgets-module.md) library provides the file selection dialog and its components.

The file dialog is available to all KDE applications by using the [QFileDialog](https://doc.qt.io/qt-6/qfiledialog.html) class. The KDE QPA theme plugin uses a KFileDialog automatically.

The [KIOFileWidgets](kiofilewidgets-module.md) library provides [KFileWidget](kfilewidget.md), which is the main widget in the file dialog, as well as the [KDirOperator](kdiroperator.md) widget which contains the file views, and other components of the file dialog. Applications only need to link to [KIOFileWidgets](kiofilewidgets-module.md) if they need direct access to [KFileWidget](kfilewidget.md) or [KDirOperator](kdiroperator.md) or to the other widgets used by the file dialog, either in order to modify the behavior of the file dialog, or to reuse its components into the application itself.
