---
title: "KHelpMenu Class"
description: "Standard KDE help menu with dialog boxes."
---

# KHelpMenu Class

Standard KDE help menu with dialog boxes. [More...](#details)

- **Header:** `#include <KHelpMenu>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](khelpmenu-members.md)  
[Deprecated members](khelpmenu-obsolete.md)

## Public Types

- [enum KHelpMenu::MenuId](#MenuId-enum)

## Public Functions

- [KHelpMenu(QWidget \*parent = nullptr)](#KHelpMenu) (since 6.9)
- [KHelpMenu(QWidget \*parent, const KAboutData &aboutData)](#KHelpMenu-1) (since 6.9)
- [~KHelpMenu()](#dtor.KHelpMenu)
- [QAction \*action(KHelpMenu::MenuId id) const](#action)
- [QMenu \*menu()](#menu)
- [void setShowWhatsThis(bool showWhatsThis)](#setShowWhatsThis) (since 6.9)

## Public Slots

- [void aboutApplication()](#aboutApplication)
- [void aboutKDE()](#aboutKDE)
- [void appHelpActivated()](#appHelpActivated)
- [void contextHelpActivated()](#contextHelpActivated)
- [void donate()](#donate)
- [void reportBug()](#reportBug)
- [void switchApplicationLanguage()](#switchApplicationLanguage)

## Signals

- [void showAboutApplication()](#showAboutApplication)

## Detailed Description {#details}

This class provides the standard KDE help menu with the default "About" dialog boxes and help entry.

This class is used in [KMainWindow](kmainwindow.md) so normally you don't need to use this class yourself. However, if you need the help menu or any of its dialog boxes in your code that is not subclassed from [KMainWindow](kmainwindow.md) you should use this class.

The usage is simple:

```cpp
mHelpMenu = new KHelpMenu( this );
kmenubar->addMenu(mHelpMenu->menu() );
```

or if you just want to open a dialog box:

```cpp
mHelpMenu = new KHelpMenu( this );
connect(this, &ClassFoo::someSignal, mHelpMenu, &KHelpMenu::aboutKDE);
```

> **Warning:** The first time you use [KHelpMenu::menu](khelpmenu.md#menu)(), a [QMenu](https://doc.qt.io/qt-6/qmenu.html) object is allocated. Only one object is created by the class so if you call [KHelpMenu::menu](khelpmenu.md#menu)() twice or more, the same pointer is returned. The class will destroy the popupmenu in the destructor so do not delete this pointer yourself.

The [KHelpMenu](khelpmenu.md) object will be deleted when its parent is destroyed but you can delete it yourself if you want. The code below will always work.

```cpp
MyClass::~MyClass()
{
    delete mHelpMenu;
}
```

Using your own "About Application" dialog box:

The standard "About Application" dialog box is quite simple. If you need a dialog box with more functionality you must design that one yourself. When you want to display the dialog, you simply need to connect the help menu signal [showAboutApplication](khelpmenu.md#showAboutApplication)() to your slot.

```cpp
void MyClass::myFunc()
{
    // ...
    KHelpMenu *helpMenu = new KHelpMenu( this );
    connect(helpMenu, &KHelpMenu::showAboutApplication, this, &ClassFoo:myDialogSlot);
    // ...
}

void MyClass::myDialogSlot()
{
    <activate your custom dialog>
}
```

[KHelpMenu](khelpmenu.md) respects Kiosk settings (see the [KAuthorized](../kconfigcore/kauthorized.md) namespace in the [KConfig](../kconfigcore/kconfig.md) framework). In particular, system administrators can disable items on this menu using some subset of the following configuration:

```cpp
[KDE Action Restrictions][$i]
actions/help_contents=false
actions/help_whats_this=false
actions/help_report_bug=false
actions/switch_application_language=false
actions/help_about_app=false
actions/help_about_kde=false
```

## Member Type Documentation {#member-type-documentation}

### enum KHelpMenu::MenuId {#MenuId-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KHelpMenu::menuHelpContents` | `0` | Whether to show the Help contents. This usually consists of the handbook for the application. |
| `KHelpMenu::menuWhatsThis` | `1` | Whether to show the "What's This?" menu. When triggered, clicking anything with the mouse cursor should show information about the clicked component. |
| `KHelpMenu::menuAboutApp` | `2` | Whether to show the "About \<application\>" menu. This menu usually contains information about the application version, copyright, license, library components, authors and acknowledgements. |
| `KHelpMenu::menuAboutKDE` | `3` | Whether to show the "About KDE" menu. The contents of this menu is standardized, mentioning what KDE is, how to get support, contribute, and donate. |
| `KHelpMenu::menuReportBug` | `4` | Whether to show the "Report Bug..." menu. This provides a dialog to initiate the bug report wizard provided by KCrash. |
| `KHelpMenu::menuSwitchLanguage` | `5` | Whether to show the switch language menu. |
| `KHelpMenu::menuDonate` | `6` | Since 5.24, triggering this menu opens the donation page on a browser. |

## Member Function Documentation {#member-function-documentation}

### \[explicit, since 6.9\] KHelpMenu::KHelpMenu(QWidget \**parent* = nullptr) {#KHelpMenu}

Creates a [KHelpMenu](khelpmenu.md) with the default app data ([KAboutData::applicationData](../kcoreaddons/kaboutdata.md#applicationData)()).

`parent` The parent of the dialog boxes. The boxes are modeless and will be centered with respect to the parent.

This function was introduced in Qt 6.9.

### \[since 6.9\] KHelpMenu::KHelpMenu(QWidget \**parent*, const KAboutData &*aboutData*) {#KHelpMenu-1}

Creates a [KHelpMenu](khelpmenu.md) with app data `aboutData`.

This constructor is useful if you want to use the help menu with custom application data.

`parent` The parent of the dialog boxes. The boxes are modeless and will be centered with respect to the parent.

`aboutData` User and app data used in the About app dialog and for the actions in the help menu.

This function was introduced in Qt 6.9.

### \[override virtual noexcept\] KHelpMenu::~KHelpMenu() {#dtor.KHelpMenu}

Destroys the help menu dialogs and the menu pointer returned by the menu.

### \[slot\] void KHelpMenu::aboutApplication() {#aboutApplication}

Opens an application specific dialog box.

The method will try to open the about box using the following steps: - If the [showAboutApplication](khelpmenu.md#showAboutApplication)() signal is connected, then it will be emitted. This means there is an application defined aboutBox. - If the aboutData was set in the constructor a [KAboutApplicationDialog](kaboutapplicationdialog.md) will be created with this aboutData. - Else a [KAboutApplicationDialog](kaboutapplicationdialog.md) will be created using [KAboutData::applicationData](../kcoreaddons/kaboutdata.md#applicationData)().

### \[slot\] void KHelpMenu::aboutKDE() {#aboutKDE}

Opens the standard "About KDE" dialog box.

### QAction \*KHelpMenu::action(KHelpMenu::MenuId *id*) const {#action}

Returns the [QAction](https://doc.qt.io/qt-6/qaction.html) \* associated with the given parameter `id`.

Will return a nullptr if [menu](khelpmenu.md#menu)() has not been called.

### \[slot\] void KHelpMenu::appHelpActivated() {#appHelpActivated}

Opens the help page for the application.

The application name is used as a key to determine what to display and the system will attempt to open \<appName\>/index.html.

### \[slot\] void KHelpMenu::contextHelpActivated() {#contextHelpActivated}

Activates "What's This" help for the application.

### \[slot\] void KHelpMenu::donate() {#donate}

Opens the donate url on a browser.

### QMenu \*KHelpMenu::menu() {#menu}

Returns a popup menu you can use in the menu bar or where you need it.

The returned menu is configured with an icon, a title and menu entries. Therefore adding the returned pointer to your menu is enough to have access to the help menu.

Note: This method will only create one instance of the menu. If you call this method twice or more the same pointer is returned.

### \[slot\] void KHelpMenu::reportBug() {#reportBug}

Opens the standard "Report Bugs" dialog box.

### \[since 6.9\] void KHelpMenu::setShowWhatsThis(bool *showWhatsThis*) {#setShowWhatsThis}

Set whether to show the What's This menu entry in the help menu. The default is to show the menu entry (if Kiosk settings allow it).

This function was introduced in Qt 6.9.

### \[signal\] void KHelpMenu::showAboutApplication() {#showAboutApplication}

This signal is emitted from [aboutApplication](khelpmenu.md#aboutApplication)() if no "About \<application\>" string has been defined.

The standard application specific dialog box that is normally activated in [aboutApplication](khelpmenu.md#aboutApplication)() will not be displayed when this signal is emitted.

### \[slot\] void KHelpMenu::switchApplicationLanguage() {#switchApplicationLanguage}

Opens the changing default application language dialog box.
