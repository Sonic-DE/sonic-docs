---
title: Configuration keys
description: Configuration keys of SonicDE's widgets, for use in scripts.
source_url: https://develop.kde.org/docs/plasma/scripting/keys/
source_authors: [Alexander Lohnau, Carl Schwan, Chris Holland, Felipe Peter, Marius P, Mikhail Zolotukhin, Phu Nguyen, Plata Hill, Thiago Sueto, Torstein Wilhelmsen Sandvik, Yifan Zhu, Zren (Chris Holland)]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "main.xml of every widget in the applets directories of sonic-desktop-interface, sonic-workspace and sonic-workspace-addons"
---

# Configuration keys

These are the configuration keys of SonicDE's widgets, to use with `writeConfig()`. Each list is under the widget's ID, with each key's type and default. Where a key is in a group other than `General`, use `currentConfigGroup` first:

```js
widget.currentConfigGroup = ["Appearance"];
widget.writeConfig("showDate", "true");
```

The list comes from each widget's `main.xml`, which is the place to look for the full default values and any widget not listed here.

## Application launchers

### org.kde.plasma.kickoff

- `icon` (String, `start-here-sonicde-symbolic`): icon of the compact representation
- `menuLabel` (String): text label for the panel button
- `appNameFormat` (Int, `2`): how application names are shown; `0` is the name only, `1` the generic name only
- `favorites` (StringList): general favorites, usually `.desktop` file names
- `systemFavorites` (StringList, `suspend,hibernate,reboot,shutdown`): system action favorites
- `primaryActions` (Int, `0`): actions in the footer; `0` power, `1` session, `2` custom
- `favoritesPortedToKAstats` (Bool, `false`): whether favorites have been ported to per-activity favorites
- `systemApplications` (StringList): applications at the top of the "Computer" tab
- `paneSwap` (Bool, `false`): swap the sidebar and content panes
- `favoritesDisplay` (Int, `0`): `0` grid, `1` list
- `applicationsDisplay` (Int, `1`): `0` grid, `1` list
- `alphaSort` (Bool, `false`): sort menu contents alphabetically
- `pin` (Bool, `false`): keep the popup open when another window is activated
- `showActionButtonCaptions` (Bool, `true`): show captions on the footer action buttons
- `compactMode` (Bool, `false`): compact list items
- `switchCategoryOnHover` (Bool, `false`): switch category on hover
- `highlightNewlyInstalledApps` (Bool, `true`): highlight newly installed applications

### org.kde.plasma.kicker

- `icon` (String, `start-here-sonicde-symbolic`): icon of the compact representation
- `useCustomButtonImage` (Bool, `false`): use a custom image instead of an icon
- `customButtonImage` (Url): URL of the custom image
- `appNameFormat` (Int, `0`): how application names are shown; `0` is the name only, `1` the generic name only
- `limitDepth` (Bool, `false`): flatten top-level menu categories to one level
- `alphaSort` (Bool, `false`): sort menu contents alphabetically
- `recentOrdering` (Int, `0`): `0` recent first, `1` popular first
- `favoriteApps` (StringList): general favorites
- `favoriteSystemActions` (StringList, `logout,reboot,shutdown`): system action favorites
- `favoritesPortedToKAstats` (Bool, `false`): whether favorites have been ported to per-activity favorites
- `hiddenApplications` (StringList): `.desktop` file names not to show in the menu
- `showRecentApps` (Bool, `true`): show the "Recent Applications" category
- `showRecentDocs` (Bool, `true`): show the "Recent Files" category
- `showRecentFolders` (Bool, `false`): show the "Recent Places" category
- `useExtraRunners` (Bool, `true`): use additional KRunner plugins in search
- `extraRunners` (StringList): plugin IDs of those KRunner plugins
- `alignResultsToBottom` (Bool, `true`): align search results to the bottom of the menu
- `showIconsRootLevel` (Bool, `false`): show icons on the root level
- `highlightNewlyInstalledApps` (Bool, `true`): highlight newly installed applications
- `forceDarkMode` (Bool, `true`): force dark mode for the dashboard
- `favoritesColumns` (Int, `3`): columns in the dashboard's favorites grid

### org.sonicde.sonicmenu

- `icon` (String, `menu_new-symbolic`): icon of the compact representation
- `useCustomButtonImage` (Bool, `false`): use a custom image instead of an icon
- `customButtonImage` (Url): URL of the custom image
- `showIcons` (Bool, `false`): show icons in the menu
- `menuWidth` (Int, `240`): width of the dropdown in pixels; `0` for the default
- `buttonHeight` (Int, `28`): height of each item in pixels; `0` for the default
- `menuJson` (String): JSON array defining the menu; items can have `name`, `icon` and `command`, among others

## Task bar and window lists

### org.kde.plasma.taskmanager

- `showOnlyCurrentScreen` (Bool, `false`): only tasks on the widget's screen
- `showOnlyCurrentDesktop` (Bool, `true`): only tasks on the current virtual desktop
- `showOnlyCurrentActivity` (Bool, `true`): only tasks on the current activity
- `showOnlyMinimized` (Bool, `false`): only minimized tasks
- `unhideOnAttention` (Bool, `true`): unhide if a window wants attention
- `groupingStrategy` (Enum, `1`): `0` don't group, `1` by program name
- `groupedTaskVisualization` (Enum, `0`): what clicking a grouped task does; `0` cycles through the group
- `groupPopups` (Bool, `true`): reduce groups to one button that expands into a popup
- `onlyGroupWhenFull` (Bool, `true`): group only when out of space
- `groupingAppIdBlacklist` (StringList): application IDs not to group
- `groupingLauncherUrlBlacklist` (StringList): launcher URLs not to group
- `sortingStrategy` (Int, `1`): a value of `TaskManager::TasksModel::SortMode`
- `separateLaunchers` (Bool, `true`): sort launcher tasks separately at the start
- `hideLauncherOnStart` (Bool, `true`): hide a launcher task when its application starts
- `maxStripes` (Int, `1`): maximum rows, or columns on a vertical panel
- `forceStripes` (Bool, `false`): always use as many rows or columns as `maxStripes`
- `showToolTips` (Bool, `true`): show tooltips on hover
- `taskMaxWidth` (Enum, `1`): maximum width of task items
- `wheelEnabled` (Enum, `0`): whether the mouse wheel switches between tasks
- `wheelSkipMinimized` (Bool, `true`): skip minimized tasks when using the wheel
- `highlightWindows` (Bool, `false`): highlight windows when hovering their tooltips
- `launchers` (StringList): the launcher tasks, usually `.desktop` file or executable URLs
- `middleClickAction` (Enum, `2`): what middle-clicking a task does
- `indicateAudioStreams` (Bool, `true`): indicate applications playing audio
- `interactiveMute` (Bool, `true`): mute applications through the audio indicators
- `tooltipControls` (Bool, `true`): media and volume controls in the tooltip
- `fill` (Bool, `true`): occupy all available space
- `taskHoverEffect` (Bool, `true`): change a task's appearance on hover
- `maxTextLines` (Int, `0`): maximum text lines in a task button; `0` for no limit
- `minimizeActiveTaskOnClick` (Bool, `true`): minimize the active task when clicked
- `reverseMode` (Bool, `false`): grow tasks opposite to the system configuration
- `iconSpacing` (Int, `1`): multiplier for the spacing between icons

### org.kde.plasma.windowlist

- `showOnlyCurrentScreen` (Bool, `false`), `showOnlyCurrentDesktop` (Bool, `true`), `showOnlyCurrentActivity` (Bool, `true`), `showOnlyMinimized` (Bool, `false`): which windows to list
- `showText` (Bool, `true`): show the window title on a horizontal panel
- `showIcon` (Bool, `true`): show the icon on the panel button
- `openOnHover` (Bool, `false`): open the popup on hover
- `hoverOpenDelay` (Int, `300`): delay before that, in milliseconds
- `sortingStrategy` (Enum, `SortVirtualDesktop`): a value of `TaskManager::TasksModel::SortMode`

### org.kde.plasma.pager

- `displayedText` (Enum, `2`): text inside the desktop rectangles
- `showWindowOutlines` (Bool, `true`): show window outlines
- `showWindowIcons` (Bool, `false`): show window icons
- `showOnlyCurrentScreen` (Bool, `false`): limit to the widget's screen
- `wrapPage` (Bool, `false`): wrap when navigating
- `currentDesktopSelected` (Enum, `0`): what left-clicking a desktop does
- `pagerLayout` (Enum, `0`): layout style

### org.kde.plasma.showActivityManager

- `showActivityName` (Bool, `true`): show the current activity's name
- `showActivityIcon` (Bool, `true`): show its icon instead of the widget's

### org.kde.plasma.showdesktop

- `icon` (String, `user-desktop-symbolic`)

## System tray and status

### org.kde.plasma.systemtray

- `extraItems` (StringList): widgets explicitly enabled in the tray, by ID
- `disabledStatusNotifiers` (StringList): status notifier items that shouldn't be visible
- `hiddenItems` (StringList): items always in the popup
- `shownItems` (StringList): items always shown
- `showAllItems` (bool, `false`): keep all entries in the main area
- `knownItems` (StringList)
- `reverseIconOrder` (bool, `false`): reverse the order of icons in the panel
- `scaleIconsToFit` (bool, `false`): scale icons to the panel's thickness
- `iconSpacing` (int, `2`): multiplier of `Kirigami.Units.smallSpacing` between icons
- `pin` (Bool, `false`): keep the popup open when another window is activated

### org.kde.plasma.keyboardlayout

- `displayStyle` (Enum, `0`): text or a flag on the compact representation

### org.kde.plasma.keyboardindicator

- `key` (StringList, `Caps Lock`)

### org.kde.plasma.kimpanel, group Appearance

- `vertical_lookup_table` (Bool, `false`)
- `use_default_font` (Bool, `true`)
- `font` (Font)
- `hiddenList` (StringList)
- `scaleIconsToFit` (bool, `false`): scale icons to the panel's thickness

### org.kde.plasma.devicenotifier

- `removableDevices` (Bool, `true`): list removable devices, such as USB drives
- `nonRemovableDevices` (Bool, `false`): list non-removable devices
- `allDevices` (Bool, `false`): list all devices. Use only one of these three.
- `popupOnNewDevice` (Bool, `true`): open when a new device is inserted

### org.kde.plasma.clipboard

- `barcodeType` (String, `QRCode`)

### org.kde.plasma.lock_logout

- `actionsOrder` (StringList): order of the actions
- `show_lockScreen` (Bool, `true`), `show_requestLogoutScreen` (Bool, `true`), `show_requestShutDown`, `show_requestReboot`, `show_requestLogout`, `show_switchUser`, `show_suspendToDisk`, `show_suspendToRam` (Bool, `false`): which actions to show

### org.kde.plasma.userswitcher

- `showFace` (Bool, `false`), `showName` (Bool, `true`), `showFullName` (Bool, `true`), `showTechnicalInfo` (Bool, `false`)

## Clocks and calendars

### org.kde.plasma.digitalclock, group Appearance

- `showLocalTimezone` (Bool, `false`): show the zone when showing local time
- `showSeconds` (Enum, `1`): how seconds are shown
- `showDate` (Bool, `true`): show the date next to the clock
- `dateFormat` (string, `shortDate`): `shortDate`, `longDate`, `isoDate` or `custom`
- `customDateFormat` (string, `ddd d`): custom date format
- `autoFontAndSize` (Bool, `true`): use the default font and find the size automatically
- `fontFamily` (string), `boldText` (Bool, `false`), `italicText` (Bool, `false`), `fontWeight` (Int, `50`), `fontStyleName` (string), `fontSize` (Int, `10`): the font when not automatic
- `timeFormat` (string, `default`)
- `selectedTimeZones` (StringList, `Local`): time zones, such as `Europe/London`; `Local` is the local zone
- `lastSelectedTimezone` (String, `Local`): the zone shown on restore
- `wheelChangesTimezone` (Bool, `false`): the wheel switches between zones
- `displayTimezoneFormat` (Enum, `0`): the zone as a code, text or UTC offset
- `showWeekNumbers` (Bool, `false`): week numbers in the calendar
- `use24hFormat` (UInt, `1`): force 12 or 24 hour time
- `firstDayOfWeek` (Int, `-1`): first day of the week; `-1` follows the locale
- `enabledCalendarPlugins` (StringList): plugins for additional calendar events
- `pin` (Bool, `false`): keep the popup open when another window is activated
- `dateDisplayFormat` (Enum, `0`): the date below or beside the time

### org.kde.plasma.analogclock

- `showSecondHand` (Bool, `false`), `showTimezoneString` (Bool, `false`)

### org.kde.plasma.binaryclock

- `showOffLeds` (Bool, `true`), `showSeconds` (Bool, `true`)
- `useCustomColorForActive` (Bool, `false`), `customColorForActive` (Color, `green`)
- `useCustomColorForInactive` (Bool, `false`), `customColorForInactive` (Color, `red`)
- `useCustomColorForGrid` (Bool, `false`), `customColorForGrid` (Color, `blue`)

### org.kde.plasma.fuzzyclock, group Appearance

- `fuzzyness` (Int, `1`), `boldText` (Bool, `false`), `italicText` (Bool, `false`)

### org.kde.plasma.calendar, group Agenda

- `startOfWorkingDay` (int, `9`), `endOfWorkingDay` (int, `17`), `showWeekNumbers` (Bool, `false`), `compactDisplay` (String, `d`)

### org.kde.plasma.timer

- `predefinedTimers` (StringList): timers in seconds
- `running` (int, `0`), `seconds` (int, `0`), `savedAt` (DateTime)
- `showTitle` (Bool, `false`), `title` (String, `Timer`)
- `showRemainingTime` (Bool, `true`), `showSeconds` (Bool, `true`), `showTimerToggle` (Bool, `true`), `showProgressBar` (Bool, `false`)
- `showNotification` (Bool, `true`), `notificationText` (String, `Timer finished`)
- `runCommand` (Bool, `false`), `command` (String)

## Panel items

### org.kde.plasma.panelspacer

- `expanding` (bool, `true`): take all available space
- `length` (Int, `-1`): length in pixels, when not expanding

### org.kde.plasma.marginsseparator

- `icon` (String, `user-desktop`)

### org.kde.plasma.appmenu, group Appearance

- `compactView` (Bool, `false`): show only a button for the menu
- `allScreens` (Bool, `true`): show menus for applications on all screens

### org.kde.plasma.icon

- `url` (String), `localPath` (String)

### org.kde.plasma.quicklaunch

- `maxSectionCount` (Int, `1`), `showLauncherNames` (Bool, `false`), `enablePopup` (Bool, `false`), `title` (String), `launcherUrls` (StringList), `popupUrls` (StringList)

## Other widgets

### org.kde.plasma.colorpicker

- `history` (StringList), `autoClipboard` (Bool, `true`), `defaultFormat` (String, `#RRGGBB`), `pickOnActivate` (Bool, `true`), `compactPreviewCount` (Int, `1`)

### org.kde.plasma.comic, no group

- `comic` (string): the current comic tab
- `showComicUrl`, `showComicAuthor`, `showComicTitle`, `showComicIdentifier` (Bool, `false`): what to show in metadata rows
- `arrowsOnHover` (Bool, `true`): navigation arrows only on hover
- `middleClick` (Bool, `true`): middle-clicking opens a full view
- `tabIdentifier` (StringList): enabled comic plugins
- `checkNewComicStripsIntervall` (Int, `180`): minutes between checks for new strips
- `maxComicLimit` (Int, `29`): strips to cache per comic
- `savingDir` (String): folder of the last saved image

### org.kde.plasma_applet_dict

- `dictionary` (String, `all`)

### org.kde.plasma.fifteenpuzzle, group Appearance

- `imagePath` (String), `useImage` (Bool, `false`), `showNumerals` (Bool, `true`), `boardColor` (Color, `#333333`), `numberColor` (Color, `#ffffff`), `boardSize` (Int, `4`)

### org.kde.plasma.mediaframe

- `interval` (Double, `10.0`), `randomize` (Bool, `true`), `pauseOnMouseOver` (Bool, `true`), `leftClickOpenImage` (Bool, `true`), `showCountdown` (Bool, `true`), `fillMode` (int, `1`)
- In group Paths: `pathList` (StringList)

### org.kde.plasma.notes

- `color` (String, `yellow`), `fontSize` (int), `noteId` (String), `scrollX` (Double, `0`), `scrollY` (Double, `0`), `cursorPosition` (Int, `-1`), `pinOpen` (Bool, `false`)

### org.kde.plasma.weather

- In group WeatherStation: `updateInterval` (int, `30`), `placeDisplayName`, `provider`, `placeInfo`, `source` (string)
- In group Appearance: `showTemperatureInCompactMode` (bool, `false`), `showTemperatureInBadge` (bool, `false`), `showTemperatureInTooltip` (bool, `true`), `showWindInTooltip` (bool, `true`), `showPressureInTooltip` (bool, `false`), `showHumidityInTooltip` (bool, `true`)
- In group Units: `temperatureUnit`, `pressureUnit`, `speedUnit`, `visibilityUnit` (int)

### org.kde.plasma.webbrowser

- `useDefaultUrl` (Bool, `false`), `defaultUrl` (String), `url` (String), `pin` (Bool, `false`)
- `useMinViewWidth` (Bool, `true`), `minViewWidth` (Int, `600`), `constantZoomFactor` (Int, `100`)
- `icon` (String), `favIcon` (String), `useFavIcon` (Bool, `true`)
- `enableNavigationBar` (Bool, `true`), `privateBrowsing` (Bool, `true`)
