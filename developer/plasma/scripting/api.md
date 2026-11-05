---
title: Scripting API
description: The API desktop scripts can use.
source_url: https://develop.kde.org/docs/plasma/scripting/api/
source_authors: [Alexander Lohnau, Carl Schwan, Chris Holland, Felipe Peter, Marius P, Mikhail Zolotukhin, Phu Nguyen, Plata Hill, Thiago Sueto, Torstein Wilhelmsen Sandvik, Yifan Zhu, Zren (Chris Holland)]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "shell/scripting in sonic-workspace (appinterface, applet, containment, panel, widget, configgroup, scriptengine_v1); most entries called on a sonicshell on a private Xvfb and D-Bus; QRectF members, screenForConnector with a real connector, showConfigurationInterface, loadSerializedLayout and the effect of globalShortcut read from code only"
---

# Scripting API

Besides the normal JavaScript API provided by [QJSEngine](https://doc.qt.io/qt-6/qjsengine.html), scripts can use the API below. Anything not listed as part of a type is in the global namespace.

## Version numbers

Read-only properties:

- `string applicationVersion`: the version of the shell
- `number scriptingVersion`: the version of the scripting API

## Activities

Activities are similar to virtual desktops, except that each can have its own wallpaper and desktop widgets. All activities share the same panels.

For scripting, what matters is that each activity has a different desktop for each screen, and that each desktop can have its own wallpaper and widgets:

```text
sonicshell
├── All activities
│   └── Panel for screen 0
│       └── Widgets
├── Activity "Default"
│   ├── Desktop for screen 0, with its wallpaper and widgets
│   └── Desktop for screen 1
└── Activity "Gaming"
    ├── Desktop for screen 0
    └── Desktop for screen 1
```

Create activities with `createActivity()`. It returns a string ID; there is no `Activity` type.

```js
const activityId = createActivity("Activity Name");
const desktop = desktopsForActivity(activityId)[0];
desktop.wallpaperPlugin = "org.kde.image";
desktop.currentConfigGroup = ["Wallpaper", "org.kde.image", "General"];
desktop.writeConfig("Image", "file:///path/to/image.png");
```

Read-only properties:

- `array<number> activityIds`: the numeric IDs of the desktops of all activities
- `array<string> knownActivityTypes`: the containment types an activity's desktop can have

Functions:

- `array<string> activities()`: the IDs of all activities
- `string activityName(string activityId)`: the name of an activity
- `setActivityName(string activityId, string name)`: sets the name of an activity
- `string currentActivity()`: the ID of the current activity
- `setCurrentActivity(string activityId)`: switches to an activity
- `string createActivity(string name[, string plugin])`: creates an activity. `plugin` is the containment type of its desktops, one of `knownActivityTypes`. Without it, the default type is used.

## Desktops

Every screen has a desktop in each activity. A desktop is a [containment](#containments) that can have widgets and a wallpaper.

```js
const desktop = desktops()[0];
desktop.wallpaperPlugin = "org.kde.image";
desktop.currentConfigGroup = ["Wallpaper", "org.kde.image", "General"];
desktop.writeConfig("Image", "file:///path/to/image.png");
```

Global functions:

- `array<Desktop> desktops()`: all desktops
- `array<Desktop> desktopsForActivity(string id)`: the desktops of an activity, one per screen
- `Desktop desktopById(number id)`: the desktop with the given ID
- `Desktop desktopForScreen(number screen)`: the desktop currently on a screen

Read-write properties, as well as those of containments:

- `string wallpaperPlugin`: the wallpaper plugin. List the installed ones with:

  ```bash
  kpackagetool6 --type=Plasma/Wallpaper --list
  ```

- `string wallpaperMode`: the wallpaper plugin's mode. It has no use currently.

## Panels

Panels can be created, listed, changed and removed. A panel object combines a containment with the view around it, so you control where it appears on the screen and how it hides.

```js
const panel = new Panel;
```

`new Panel` takes an optional containment type, such as `new Panel("org.kde.panel")`.

Global properties:

- `array<number> panelIds`: the IDs of all panels
- `array<string> knownPanelTypes`: the panel types that can be created

Global functions:

- `Panel panelById(number id)`: the panel with the given ID
- `array<Panel> panels()`: all panels

Read-write properties, as well as those of containments:

- `string location`: `top`, `bottom`, `left` or `right`
- `string alignment`: `left`, `center` or `right`. On a vertical panel, `left` is the top and `right` the bottom.
- `number offset`: how far the panel is moved from its alignment point
- `string lengthMode`: `fill`, `fit` or `custom`. `fill` takes the available length and `fit` follows the content.
- `number length`: the number of pixels used along the screen edge
- `number minimumLength`: the minimum of that length
- `number maximumLength`: the maximum of that length
- `number height`: the height of the panel, or the width of a vertical panel
- `string hiding`: `none`, `autohide`, `dodgewindows` or `windowsgobelow`. Any other value means `none`. The property reads back `none` for `windowsgobelow`.
- `bool floating`: whether the panel floats away from the screen edge
- `string opacity`: `adaptive`, `opaque` or `translucent`

## Containments

Desktops and panels are both containments. Containments have everything [applets](#applets) have, and more.

Read-only properties:

- `string formFactor`: `planar` for desktops, `horizontal` or `vertical` for panels
- `array<number> widgetIds`: the IDs of all widgets in this containment

Read-write properties:

- `number screen`: the screen this containment is on, or `-1` for none
- `bool locked`: whether it is locked

Functions:

- `Widget addWidget(string name)`: adds a new widget by its ID
- `Widget addWidget(string name, number x, number y, number w, number h)`: adds a new widget at a position
- `Widget addWidget(Widget widget)`: moves an existing widget to this containment
- `Widget widgetById(number id)`: the widget with the given ID
- `array<Widget> widgets([string type])`: all widgets in the containment, or only those of one type

## Widgets

Get widgets from a containment with `widgets()` or `widgetById()`, and create them with `addWidget()`.

Check whether a widget is installed with the global `knownWidgetTypes`, which lists all widget types including containments such as `org.kde.panel`:

```js
if (knownWidgetTypes.includes("someWidgetId")) {
    print("It is installed on this system!");
} else {
    print("It is not installed :(");
}
```

A widget has everything [applets](#applets) have, and these read-write properties:

- `object geometry`: the geometry of the widget, as a [QRectF](#qrectf)
- `string globalShortcut`: the shortcut associated with this widget, in the format of [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html), such as `Alt+F1`
- `number index`: the position of the widget in its layout. In a panel this is the order the widgets appear in.
- `string userBackgroundHints`: the kind of background to use, if the widget lets the user configure it (see [its background hints](../widget/properties.md))
- `bool locked`: whether it is locked

## Applets

Applet is the base of widgets and containments. The current groups let you reach nested configuration:

```js
widget.currentConfigGroup = ["topGroup", "subGroupOfTopGroup"];
```

Read-only properties:

- `number id`: the ID of this instance
- `string type`: the plugin ID
- `string version`: the version from its metadata
- `array<string> configKeys`: the keys set in the current configuration group
- `array<string> configGroups`: the groups in the current configuration group
- `array<string> globalConfigKeys`: the keys set in the current global configuration group
- `array<string> globalConfigGroups`: the groups in the current global configuration group

Read-write properties:

- `array<string> currentConfigGroup`: the current configuration group, each entry a sub-group. An empty array means the top level.
- `array<string> currentGlobalConfigGroup`: the same for the global configuration, which all instances of the same type share

Functions:

- `remove()`: deletes it, and for a containment all the widgets in it
- `showConfigurationInterface()`: shows its configuration window
- `readConfig(string key[, any default])`: reads a value
- `writeConfig(string key, any value)`: sets a value
- `readGlobalConfig(string key[, any default])`: reads a value from the global configuration
- `writeGlobalConfig(string key, any value)`: sets a value in the global configuration
- `reloadConfig()`: makes it reload its configuration. Changes usually take effect when the script ends; this applies them earlier for one widget.

## Screens

- `number screenCount`: the number of screens
- `QRectF screenGeometry(number screen)`: the geometry of a screen
- `number screenForConnector(string connector)`: the screen on a connector, or `-1`
- `number gridUnit`: the size of the grid unit, for sizing panels

## Wallpaper plugins

- `object knownWallpaperPlugins()`: an object with one key for each installed wallpaper plugin. The keys are the plugins' display names, such as `Image`, not their IDs. Use `Object.keys()` to list them.

## Applications and paths

- `bool applicationExists(string name)`: searches the `PATH`, then the application menu by `.desktop` file name, then by `Name=` and `GenericName=`
- `defaultApplication(string kind[, bool storageId = false])`: the executable of the default application, or with `storageId` its `.desktop` file name. `kind` is `browser`, `mailer`, `filemanager`, `terminal` or `windowmanager`, or a MIME type such as `application/pdf`. Returns `false` on failure.
- `string applicationPath(string name)`: the full path of an application or `.desktop` file, if it exists
- `bool fileExists(string path)`: whether a file exists
- `string userDataPath([string type, string path])`: with no arguments, the home directory. `type` selects a standard directory, one of `desktop`, `documents`, `music`, `video`, `downloads`, `pictures` or `config`; any other value means the data directory. `path` is looked up inside that directory.

```js
const executable = "firefox";
if (applicationExists(executable)) {
    print(`${executable} exists with this path: ${applicationPath(executable)}`);
    print(`Its .desktop file is here: ${applicationPath("firefox.desktop")}`);
} else {
    print(`${executable} does not exist`);
}
```

## External configuration files

`ConfigFile` gives access to configuration files other than the shell's own:

- `ConfigFile(string file[, string group])`: opens a file, optionally at a group
- `ConfigFile(ConfigFile parent[, string group])`: a new object whose groups are child groups of `parent`

Functions:

- `writeEntry(string key, any value)`: writes a value in the current group
- `readEntry(string key)`: reads a value from the current group
- `deleteEntry(string key)`: deletes a key in the current group

Read-write properties:

- `file`: the name of the file, an absolute path or a file name to find in the configuration directories
- `group`: the current group. To reach child groups, create a new `ConfigFile` with this one as its parent.

Read-only properties:

- `keyList`: all keys in the current group
- `groupList`: all child groups in the current group

```js
// open the kickoffrc file
const config = ConfigFile("kickoffrc");
// switch to the RecentlyUsed group
config.group = "RecentlyUsed";
// write an entry into it
config.writeEntry("MaxApplications", 25);

// now put Yes=20 into RecentlyUsed/Test
const config2 = ConfigFile(config, "Test");
config2.writeEntry("Yes", 20);
```

## Other properties and functions

Read-write properties:

- `bool locked`: whether the desktop shell and widgets are locked
- `string theme`: the name of the desktop theme

Read-only properties:

- `bool hasBattery`: whether the system can run on battery power
- `string locale`: the current locale, such as `en_AU`
- `string language`: the current language's name
- `string languageId`: the current language's code
- `bool multihead`: always `false`; kept for older scripts
- `number multiheadScreen`: kept for older scripts

Functions:

- `print(any value)`: adds to the script's output, without a line break
- `sleep(number ms)`: pauses the script
- `string immutability()`: `mutable`, `userImmutable` or `systemImmutable`
- `setImmutability(string immutability)`: sets it
- `bool loadTemplate(string id)`: runs a [panel template](templates.md)
- `loadSerializedLayout(object data)`: restores a layout from the data of `dumpCurrentLayoutJS`, a method of the shell's D-Bus interface

## QRectF

A rectangle type, used for widget and screen geometry.

Read-only properties:

- `bool empty`: true if the width or height is 0 or less. An empty rectangle is also invalid.
- `bool null`: true if the width and height are both 0. A null rectangle is also empty and invalid.
- `bool valid`: true if the width and height are both greater than 0

Read-write properties:

- `number left`, `top`, `right`, `bottom`
- `number x`, `y`, `width`, `height`

Constructors:

- `QRectF`
- `QRectF(number x, number y, number width, number height)`

Functions:

- `adjust(number dx1, number dy1, number dx2, number dy2)`: adds to the existing coordinates
- `QRectF adjusted(number dx1, number dy1, number dx2, number dy2)`: returns a new rectangle with those added
- `translate(number dx, number dy)`: moves the rectangle by that much
- `setCoords(number x1, number y1, number x2, number y2)`: sets the top-left and bottom-right corners
- `setRect(number x, number y, number width, number height)`: sets the top-left corner and size
- `bool contains(number x, number y)`: whether the rectangle contains the point
- `moveTo(number x, number y)`: moves the top left to the point
- `moveLeft(number delta)`, `moveRight(number delta)`, `moveTop(number delta)`, `moveBottom(number delta)`: move that edge
