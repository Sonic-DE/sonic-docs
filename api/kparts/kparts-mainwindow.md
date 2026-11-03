---
title: "KParts::MainWindow Class"
description: "A KPart-aware main window, whose user interface is described in XML."
---

# KParts::MainWindow Class

A KPart-aware main window, whose user interface is described in XML. [More...](#details)

- **Header:** `#include <KParts/MainWindow>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [KXmlGuiWindow](../kxmlgui/kxmlguiwindow.md) and [KParts::PartBase](kparts-partbase.md)

[List of all members, including inherited members](kparts-mainwindow-members.md)

## Public Functions

- [MainWindow(QWidget \*parent = nullptr, Qt::WindowFlags f = WindowFlags())](#MainWindow)

## Public Slots

- [void createGUI(KParts::Part \*part)](#createGUI)
- [void saveNewToolbarConfig()](#saveNewToolbarConfig)
- [void setWindowTitleHandling(bool enabled)](#setWindowTitleHandling)
- [void slotSetStatusBarText(const QString &)](#slotSetStatusBarText)

## Detailed Description {#details}

It implements all internal interfaces in the case of a [KMainWindow](../kxmlgui/kmainwindow.md) as host: the builder and servant interface (for menu merging).

Inherit your main window from this class and make sure to call [setXMLFile](../kxmlgui/kxmlguiclient.md#setXMLFile)() and [setupGUI](../kxmlgui/kxmlguiwindow.md#setupGUI)() before you call [createGUI](kparts-mainwindow.md#createGUI)() on the KPart.

For example:

```cpp
setCentralWidget(m_part->widget());
setXMLFile(QStringLiteral("appui.rc"));
setupGUI(ToolBar | Keys | StatusBar | Save); // Never Create flag here
createGUI(m_part);
```

> **Warning:** You should not pass the Default flag set to [setupGUI](../kxmlgui/kxmlguiwindow.md#setupGUI)(), since it contains the Create flag, which is not supposed to be used from this class.

*See also* [KXmlGuiWindow::Create](../kxmlgui/kxmlguiwindow.md#StandardWindowOption-enum), [setupGUI](../kxmlgui/kxmlguiwindow.md#setupGUI)(), [createGUI](kparts-mainwindow.md#createGUI)()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] MainWindow::MainWindow(QWidget \**parent* = nullptr, Qt::WindowFlags *f* = Qt::WindowFlags()) {#MainWindow}

Constructor, same signature as [KMainWindow](../kxmlgui/kmainwindow.md).

### \[protected slot\] void MainWindow::createGUI(KParts::Part \**part*) {#createGUI}

Create the GUI (by merging the host's and the active part's) You \_must\_ call this in order to see any GUI being created.

In a main window with multiple parts being shown (e.g. as in Konqueror) you need to connect this slot to the KPartManager::activePartChanged() signal

`part` The active part (set to 0L if no part).

### \[override virtual protected slot\] void MainWindow::saveNewToolbarConfig() {#saveNewToolbarConfig}

Reimplements: [KXmlGuiWindow::saveNewToolbarConfig()](../kxmlgui/kxmlguiwindow.md#saveNewToolbarConfig).

Rebuilds the GUI after [KEditToolBar](../kxmlgui/kedittoolbar.md) changed the toolbar layout.

*See also* [configureToolbars](../kxmlgui/kxmlguiwindow.md#configureToolbars)()

### \[protected slot\] void MainWindow::setWindowTitleHandling(bool *enabled*) {#setWindowTitleHandling}

Enable or disable the automatic setting of window titles by the part's document title. By default, a part always changes the window title when the document changes.

> **Note:** This value must be set before calling [createGUI](kparts-mainwindow.md#createGUI)().

`enabled` boolean to enable or disable the window title handling

### \[virtual protected slot\] void MainWindow::slotSetStatusBarText(*const QString &*) {#slotSetStatusBarText}

Called when the active part wants to change the statusbar message Reimplement if your mainwindow has a complex statusbar (with several items)
