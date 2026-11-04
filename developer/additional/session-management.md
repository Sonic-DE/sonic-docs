---
title: Session management
description: Make your application restore its state when the user logs in again.
source_url: https://develop.kde.org/docs/features/additional-features/session-management/
source_authors: [Matthias Ettrich, Carl Schwan, Chris Holland, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto, Tobias Fella, ivan tkachenko]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-xml-gui (src/kmainwindow.h, kmainwindow.cpp), sonic-frameworks-settings (KConfigGui::sessionConfig), sonic-workspace d0b84fd142 (ksmserver, startkde, plasma-session), sonic-win 71cc168eef (sm.cpp)
---

# Session management

## SonicDE and X11 session management

SonicDE supports the old X11R4 and ICCCM session management protocols: when a session is restored, it restarts legacy applications that set the `WM_COMMAND` property or support the `WM_SAVE_YOURSELF` protocol, with the command they gave, and restores their window geometry as well as it can.

SonicDE also supports and uses the standard X11R6 session management protocol, XSMP, described in the [X Session Management Protocol specification](https://www.x.org/releases/current/doc/libSM/xsmp.html). Unlike the old protocols, it lets applications save their own settings when the user logs out: a text editor, for instance, saves the names of the open files and opens them again at the next login. It also gives a clean and safe logout even when the user doesn't want to restore the session: applications can ask the user when data would be lost, and can cancel the logout if needed.

### Further reading

Qt's [QSessionManager](https://doc.qt.io/qt-6/qsessionmanager.html) documentation gives an overview of session management and Qt's API for it.

In SonicDE's libraries, [KConfigGui](/docs/api/kconfiggui/kconfiggui) and [KMainWindow](/docs/api/kxmlgui/kmainwindow) hide the details. KConfigGui manages a KConfig object for you, returned by [KConfigGui::sessionConfig()](/docs/api/kconfiggui/kconfiggui#sessionConfig), in which your application stores its session data.

Read the class documentation, especially [KMainWindow](/docs/api/kxmlgui/kmainwindow)'s, for the details. With KMainWindow, a few lines are enough for even a multi-window application to keep its state between sessions.

## Adding session management to your application

Here is a short overview; the class documentation has the details.

If your main window inherits KMainWindow, you have two things to do:

- Reimplement some virtual functions of [KMainWindow](/docs/api/kxmlgui/kmainwindow).
- Add session restoring to your `main()` function.

That's all.

### Reimplementing KMainWindow's virtual functions

KMainWindow saves its position and size and the positions of its toolbars and menu bar when you log out, and restores them at the next start.

Anything else your application needs to restore a session, you save and restore yourself, but KMainWindow makes it easy. Reimplement these functions:

- [saveProperties()](/docs/api/kxmlgui/kmainwindow#saveProperties) is called when the session manager asks your application to save its state, not when the user closes the application. Save the data you need to restore the session here (for a text editor, the list of open files). No user interaction is allowed in this function: you may not, for example, show a dialog.
- [readProperties()](/docs/api/kxmlgui/kmainwindow#readProperties) reads the data again at the next login.

[queryClose()](/docs/api/kxmlgui/kmainwindow#queryClose) may also interest you. It is called before the window is closed, whether by the user or by the session manager. (It is not called for [QCoreApplication::quit()](https://doc.qt.io/qt-6/qcoreapplication.html#quit), which leaves the event loop without closing the main windows, and doesn't even destroy them.) Here you typically warn the user about unsaved data, for example with a dialog offering "Save changes" and "Discard changes". Returning `false` cancels closing, and during a logout it cancels the logout. Avoid user interaction here when you can, since it gets in the way of the session manager. Don't close the document in `queryClose()`: the session may not have been saved yet, and the logout may still be cancelled. It isn't defined whether `saveProperties()` is called before or after `queryClose()`.

> **Note:** For application-wide data (needed once per application, not for each main window), reimplement [saveGlobalProperties()](/docs/api/kxmlgui/kmainwindow#saveGlobalProperties) and [readGlobalProperties()](/docs/api/kxmlgui/kmainwindow#readGlobalProperties); they are only called for the first main window. You usually don't need them.

## Adding session restoring to main()

`saveProperties()` (and `queryClose()`) are called automatically, but `readProperties()` isn't: your `main()` function must restore the session:

```cpp
QApplication app(argc, argv);
if (app.isSessionRestored()) {
  kRestoreMainWindows<MyWindow>();
} else {
  // create default application as usual
  // example:
  MyWindow * window = new MyWindow();
  // The function will replace '#' with numbers that are
  // unique within the application:
  window->setObjectName("MyWindow#");
  window->show();
}
return app.exec();
```

`kRestoreMainWindows<>()` creates (on the heap) as many main windows as the last session had, and calls [KMainWindow::restore()](/docs/api/kxmlgui/kmainwindow#restore) with the right arguments. It also calls `QWidget::show()` for them.

About `setObjectName("MyWindow#")`: for session and window management to work properly, every main window of the application needs a different name. KMainWindow makes up a unique name if you don't set one, but it is better to give a name that also says what kind of window it is. If there can be several windows of the same kind, end the name with `#`, and KMainWindow replaces it with a number to make the names unique. A mail client with one main window for folders and messages and any number of composer windows, for example, would name the first `mainwindow` and the others `composer#`.

That restores all your application's top-level windows.

An application can also restore different kinds of top-level windows (each derived from KMainWindow), up to three kinds. Say you have three main window classes, `ChildMW1`, `ChildMW2` and `ChildMW3`:

```cpp
QApplication app(argc, argv);
if ( app.isSessionRestored() ) {
  kRestoreMainWindows< ChildMW1, ChildMW2, ChildMW3 >();
} else {
  // create default application as usual
  // example:
  ChildMW1* window1 = new ChildMW1();
  ChildMW2* window2 = new ChildMW2();
  ChildMW3* window3 = new ChildMW3();
  // The function will replace '#' with numbers that are
  // unique within the application:
  window1->setObjectName("type1mainWindow#");
  window2->setObjectName("type2mainWindow#");
  window3->setObjectName("type3mainWindow#");
  window1->show();
  window2->show();
  window3->show();
}
return app.exec();
```

### Appendix: how SonicDE's session manager works

SonicDE's session manager is `ksmserver`, part of `sonic-workspace`. It works with the window manager, SonicWin, to save and restore window geometries, and handles the legacy session management protocols itself. At login, `startplasma-x11` starts `plasma_session`, which starts `ksmserver` and then asks it to restore the session.
