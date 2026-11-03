---
title: "KCommandBar Class"
description: "A hud style menu which allows listing and executing actions."
---

# KCommandBar Class

A hud style menu which allows listing and executing actions. [More...](#details)

- **Header:** `#include <KCommandBar>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`
- **Inherits:** [QFrame](https://doc.qt.io/qt-6/qframe.html)

[List of all members, including inherited members](kcommandbar-members.md)

## Public Functions

- [KCommandBar(QWidget \*parent)](#KCommandBar)
- [void setActions(const QList\<KCommandBar::ActionGroup\> &actions)](#setActions)

## Public Slots

- [void show()](#show)

## Detailed Description {#details}

[KCommandBar](kcommandbar.md) takes as input a list of QActions and then shows them in a "list-like-view" with a filter line edit. This allows quickly executing an action.

Usage is simple. Just create a [KCommandBar](kcommandbar.md) instance when you need it and throw it away once the user is done with it. You can store it as a class member as well but there is little benefit in that. Example:

```cpp
void slotOpenCommandBar()
{
     // `this` is important, you must pass a parent widget
     // here. Ideally it will be your mainWindow
    KCommandBar *bar = new KCommandBar(this);

    // Load actions into the command bar
    // These actions can be from your menus / toolbars etc
    QList<ActionGroup> actionGroups = ...;
    bar->setActions(actionGroups);

    // Show
    bar->show();
}
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCommandBar::KCommandBar(QWidget \**parent*) {#KCommandBar}

Constructor

`parent` is used to determine position and size of the command bar. It \*must\* not be `nullptr`.

### void KCommandBar::setActions(const QList\<KCommandBar::ActionGroup\> &*actions*) {#setActions}

`actions` is a list of {GroupName, [QAction](https://doc.qt.io/qt-6/qaction.html)}. Group name can be the name of the component/menu where a [QAction](https://doc.qt.io/qt-6/qaction.html) lives, for example in a menu "File -\> Open File", "File" should be the GroupName.

### \[slot\] void KCommandBar::show() {#show}
