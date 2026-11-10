---
title: Embedding the terminal
description: Show Sonic Terminal inside your own program with its QML modules, and what terminal plugins need to know.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-terminal 342e7db0a (src/CMakeLists.txt, src/quick/TerminalHost.h, src/quick/TerminalHost.cpp, src/quick/PanelOpen.cpp, src/quick/WindowController.h, src/qml/TerminalArea.qml, src/qml/TerminalPanelArea.qml, src/plugins/QuickCommands, src/plugins/SSHManager, RELEASE-NOTES.md), sonic-ecco (src/panels/terminal/terminalpanel.cpp); written from the code, not clicked through"
---

# Embedding the terminal

Sonic Terminal's window is drawn with QML, and other programs can show the same terminal through two QML modules that `sonic-terminal` installs. Ecco's terminal panel and the Terminal Panel widget use them. They replace the old Konsole KPart for SonicDE programs.

## The QML modules

| Module | What it has |
| --- | --- |
| `org.sonicde.terminal.app` | The types a host uses: `TerminalArea`, `TerminalPanelArea` and `TerminalHost`. |
| `org.sonicde.terminal` | The terminal's own QML parts (panes, tab bar, dialogs). `org.sonicde.terminal.app` imports it; hosts don't need it directly. |

Both are installed under the QML directory (`org/sonicde/terminal` and `org/sonicde/terminal/app`). Add `sonicde/sonic-terminal` to your package manifest's `depends` so the modules are built and staged before your package.

### TerminalArea

`TerminalArea` is one terminal session, the way the KPart showed it: no tab bar and no toolbars. Use it for a terminal that belongs to something else in your program, such as Ecco's folder panel.

### TerminalPanelArea

`TerminalPanelArea` is the whole terminal as Sonic Terminal lays it out: toolbars, tabs, splits and the command bar. Only the text area draws a background, so the host can blur or tint the rest. It adds:

- `textArea`: where the terminals' text is, in the item's coordinates, so the host can leave its own background out of it.
- `toolBarContextMenuRequested(item, position)`: a right click on an empty part of a toolbar, for the host to show its own menu.

### TerminalHost

Both types are a `TerminalHost`, which has the API. Properties:

- `profile`: the name of the profile to start with; empty uses the default profile. Set it when the item is created.
- `fullTerminal`: tabs, splits, toolbars and menus instead of a single session. `TerminalPanelArea` sets it. Set it when the item is created.
- `toolBarsAtBottom`: puts the toolbars at the bottom.
- `servesNewTerminals`: when this is true, starting `konsole` without a command opens a tab in this item instead of a window. Only the first host that asks serves; for any other host, setting it has no effect.
- `blur` (read-only): the color scheme's blur setting, for the host to blur its window.
- `compatWindow` and `controller` (read-only): the terminal's internal window and its controller. The QML types use them; hosts usually don't.

Methods:

- `showShellInDir(dir)`, `sendInput(text)`
- `currentWorkingDirectory()`, `foregroundProcessId()`, `foregroundProcessName()`
- `setContextMenuAdditionalActions(actions)`: adds your `QAction`s to the terminal's context menu.
- `sessionActionCollection()`: the session's action collection, for your own Configure Shortcuts dialog. Call `saveShortcuts()` after that dialog closes so the changes are kept in `konsolerc`.
- `configureTerminal()`: opens the active session's Edit Profile dialog.
- `ownWindowOpen()`: true while one of the terminal's menus or dialogs has the focus.

Signals:

- `finished()`: the session ended and nothing of the terminal is left.
- `currentDirectoryChanged(dir)`
- `newTerminalOpened()`: a started `konsole` opened a tab here (see `servesNewTerminals`); show the terminal and give it the keyboard.
- `ownWindowsClosed(keepInput)`: the last of the terminal's menus and dialogs closed. `keepInput` is true when no other program took the focus in the meantime.
- `pressedInside()`: any mouse button was pressed anywhere in the item.

## Requirements in the host

- The host must be a `QApplication`, not just a `QGuiApplication`. Behind the item is an off-screen widget window with the session; without a `QApplication` the item logs a critical message and shows nothing.
- Set the Qt Quick style before the first QML is loaded. Ecco uses `org.kde.desktop` when no style is set.

## Example

A widgets program can show the terminal in a `QQuickWidget`, as Ecco does:

```cpp
auto *view = new QQuickWidget(parent);
view->setResizeMode(QQuickWidget::SizeRootObjectToView);
view->loadFromModule("org.sonicde.terminal.app", "TerminalArea");
if (view->status() == QQuickWidget::Ready && view->rootObject()) {
    QObject *terminal = view->rootObject();
    connect(terminal, SIGNAL(finished()), this, SLOT(terminalExited()));
    QMetaObject::invokeMethod(terminal, "showShellInDir", Q_ARG(QString, QDir::homePath()));
}
```

In QML:

```qml
import org.sonicde.terminal.app

TerminalArea {
    anchors.fill: parent
    onFinished: console.log("terminal closed")
}
```

## Terminal plugins and the command bar

Terminal plugins, such as Quick Commands and SSH Manager, still implement `Konsole::IKonsolePlugin` and are loaded as before. Plugins built for the old widget window also still load.

The command bar is now drawn in the QML window. A plugin that creates and shows a `KCommandBar` itself gets nothing on screen, because that widget would open in the hidden window behind the QML one. Pass the actions to the window's controller instead:

```cpp
if (auto *controller = Konsole::WindowController::controllerOf(mainWindow)) {
    controller->openCommandBar({KCommandBar::ActionGroup{i18n("Quick Commands"), actions}});
}
```

`WindowController` is part of the terminal's own sources, so this works for plugins built in the `sonic-terminal` tree.
