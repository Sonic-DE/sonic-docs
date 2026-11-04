---
title: SonicWin scripting API
description: The objects, properties, signals and functions available to SonicWin scripts and scripted effects.
source_url: https://develop.kde.org/docs/plasma/kwin/api/
source_authors: [Alexander Lohnau, Carl Schwan, Chris Holland, Denis Štogl, Emil Sonnenschein, Hynek Schlindenbuch, Ian Canino, Jade Lovelace, Kunda Ki, Marius Bosler, Marius P, Mikhail Zolotukhin, Sebastian Kügler, Shalok Shalom, Thiago Sueto, Vlad Zahorodnii, Zren (Chris Holland)]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "every name compared in both directions with the Q_PROPERTY, signal and method declarations in sonic-win/src headers; signatures that differ were read individually. Most Window and workspace members were not each called: a sample was exercised on sonic-win on a private Xvfb."
---

# SonicWin scripting API

This page describes the API of SonicWin scripts and scripted effects. Types keep the `KWin` namespace they inherited.

## Global

Methods and properties added to the global JavaScript object.

### Read-only properties

- `KWin::Options options`: all configuration values of the window manager core
- `KWin::Workspace workspace`: the core wrapper of the window manager
- `object KWin`: provides access to the enums defined in `KWin::WorkspaceWrapper`

### Functions

- `print(QVariant ... values)`: prints all provided values
- `QVariant readConfig(QString key, QVariant defaultValue = QVariant())`: reads the value of `key` in the script's configuration. Without a default and with no stored value, the result is undefined.
- `bool registerScreenEdge(ElectricBorder border, QJSValue callback)`: registers the callback for a screen edge, invoked when the mouse is pushed against the edge. Scripts can also add `X-KWin-Border-Activate` to their metadata to be listed in the screen edges settings. This writes a `BorderConfig=` entry in the script's configuration, with the edges the user selected.
- `bool unregisterScreenEdge(ElectricBorder border)`: disconnects all callbacks of this script from that edge
- `bool registerShortcut(QString title, QString text, QString keySequence, QJSValue callback)`: registers `keySequence` as a global shortcut, and calls the callback when it is used. `title` and `text` name the shortcut in the shortcut settings.
- `bool assert(bool value, QString message = QString())`: aborts the script if `value` isn't true, with the given message or a default one
- `bool assertTrue(bool value, QString message = QString())`: the same as `assert`
- `bool assertFalse(bool value, QString message = QString())`: aborts the script if `value` isn't false
- `bool assertEquals(QVariant expected, QVariant actual, QString message = QString())`: aborts the script if the values differ
- `bool assertNull(QVariant value, QString message = QString())`: aborts the script if `value` isn't null
- `bool assertNotNull(QVariant value, QString message = QString())`: aborts the script if `value` is null
- `callDBus(QString service, QString path, QString interface, QString method, QVariant arg..., QJSValue callback = QJSValue())`: calls a D-Bus method. Any number of arguments can be added. The call is always asynchronous, and the reply values go to the optional callback in the last position.
- `registerUserActionsMenu(QJSValue callback)`: registers a callback invoked when the window's actions menu (`Alt+F3`, or right-clicking the decoration) is about to be shown. It receives the window, and can return one menu entry or a submenu.

A menu entry:

```js
{
    title: "My Menu entry",
    checkable: true,
    checked: false,
    triggered: function (action) {
        // callback with the triggered QAction
    }
}
```

A submenu:

```js
{
    title: "My menu",
    items: [{...}, {...}, ...] // list of entries as above
}
```

## KWin::WorkspaceWrapper

### Enums

#### ClientAreaOption

`PlacementArea`, `MovementArea`, `MaximizeArea`, `MaximizeFullArea`, `FullScreenArea`, `WorkArea`, `FullArea`, `ScreenArea`

#### ElectricBorder

`ElectricTop`, `ElectricTopRight`, `ElectricRight`, `ElectricBottomRight`, `ElectricBottom`, `ElectricBottomLeft`, `ElectricLeft`, `ElectricTopLeft`, `ELECTRIC_COUNT`, `ElectricNone`

### Read-only properties

- `QList<KWin::VirtualDesktop *> desktops`
- `QSize desktopGridSize`
- `int desktopGridWidth`
- `int desktopGridHeight`
- `int workspaceWidth`
- `int workspaceHeight`
- `QSize workspaceSize`
- `KWin::Output *activeScreen`
- `QList<KWin::Output *> screens`
- `QList<KWin::Output *> screenOrder`
- `QStringList activities`
- `QSize virtualScreenSize`: the bounding size of all screens combined. Overlapping areas aren't counted more than once.
- `QRect virtualScreenGeometry`: the bounding geometry of all screens combined. It always starts at (0,0).
- `QList<KWin::Window *> stackingOrder`: the windows managed by SonicWin, ordered by visibility (later ones cover earlier ones)
- `QPoint cursorPos`: the current position of the cursor
- `QQmlListProperty<KWin::Window> windows`: the windows, in QML scripts only

### Read-write properties

- `KWin::VirtualDesktop *currentDesktop`: the current virtual desktop
- `KWin::Window *activeWindow`
- `QString currentActivity`

### Signals

- `windowAdded(KWin::Window *window)`
- `windowRemoved(KWin::Window *window)`
- `windowActivated(KWin::Window *window)`
- `desktopsChanged()`: a virtual desktop was added or removed
- `desktopLayoutChanged()`: the layout of virtual desktops changed, so `desktopGridSize`, `desktopGridWidth` and `desktopGridHeight` have new values
- `screensChanged()`: the output list changed, for example when one is connected or removed
- `screenOrderChanged()`
- `currentActivityChanged(const QString &id)`: the current activity changed
- `activitiesChanged(const QString &id)`: the list of activities changed
- `activityAdded(const QString &id)`
- `activityRemoved(const QString &id)`
- `virtualScreenSizeChanged()`
- `virtualScreenGeometryChanged()`
- `currentDesktopChanged(KWin::VirtualDesktop *previous)`: the current virtual desktop changed
- `cursorPosChanged()`

### Functions

These act on the active window or the desktop, like the matching shortcuts:

- `slotSwitchDesktopNext()`, `slotSwitchDesktopPrevious()`, `slotSwitchDesktopRight()`, `slotSwitchDesktopLeft()`, `slotSwitchDesktopUp()`, `slotSwitchDesktopDown()`
- `slotSwitchToNextScreen()`, `slotSwitchToPrevScreen()`, `slotSwitchToRightScreen()`, `slotSwitchToLeftScreen()`, `slotSwitchToAboveScreen()`, `slotSwitchToBelowScreen()`
- `slotWindowToNextScreen()`, `slotWindowToPrevScreen()`, `slotWindowToRightScreen()`, `slotWindowToLeftScreen()`, `slotWindowToAboveScreen()`, `slotWindowToBelowScreen()`
- `slotToggleShowDesktop()`
- `slotWindowMaximize()`, `slotWindowMaximizeVertical()`, `slotWindowMaximizeHorizontal()`, `slotWindowMinimize()`, `slotWindowShade()`, `slotWindowRaise()`, `slotWindowLower()`, `slotWindowRaiseOrLower()`
- `slotActivateAttentionWindow()`
- `slotWindowMoveLeft()`, `slotWindowMoveRight()`, `slotWindowMoveUp()`, `slotWindowMoveDown()`
- `slotWindowExpandHorizontal()`, `slotWindowExpandVertical()`, `slotWindowShrinkHorizontal()`, `slotWindowShrinkVertical()`
- `slotWindowQuickTileLeft()`, `slotWindowQuickTileRight()`, `slotWindowQuickTileTop()`, `slotWindowQuickTileBottom()`, `slotWindowQuickTileTopLeft()`, `slotWindowQuickTileTopRight()`, `slotWindowQuickTileBottomLeft()`, `slotWindowQuickTileBottomRight()`
- `slotSwitchWindowUp()`, `slotSwitchWindowDown()`, `slotSwitchWindowRight()`, `slotSwitchWindowLeft()`
- `slotIncreaseWindowOpacity()`, `slotLowerWindowOpacity()`
- `slotWindowOperations()`, `slotWindowClose()`, `slotWindowMove()`, `slotWindowResize()`, `slotWindowAbove()`, `slotWindowBelow()`, `slotWindowOnAllDesktops()`, `slotWindowFullScreen()`, `slotWindowNoBorder()`
- `slotWindowToNextDesktop()`, `slotWindowToPreviousDesktop()`, `slotWindowToDesktopRight()`, `slotWindowToDesktopLeft()`, `slotWindowToDesktopUp()`, `slotWindowToDesktopDown()`

Others:

- `QList<KWin::Window *> windowList() const`: the windows, in JavaScript scripts only
- `sendClientToScreen(KWin::Window *client, KWin::Output *output)`: sends the window to the output
- `showOutline(const QRect &geometry)`: shows an outline at the geometry, or moves the current one there
- `showOutline(int x, int y, int width, int height)`: the same, for convenience
- `hideOutline()`: hides the outline
- `KWin::Output *screenAt(const QPointF &pos) const`
- `KWin::TileManager *tilingForScreen(const QString &screenName) const`
- `KWin::TileManager *tilingForScreen(KWin::Output *output) const`
- `QRectF clientArea(ClientAreaOption option, KWin::Output *output, KWin::VirtualDesktop *desktop) const`: the geometry a window can use with that option. Prefer this over other ways of finding screen sizes, as it takes constraints such as panels into account, and it is aware of multiple screens.
- `QRectF clientArea(ClientAreaOption option, KWin::Window *client) const`: the same for a window
- `createDesktop(int position, const QString &name) const`: creates a virtual desktop at a position from 0 to the current count. With an empty name, the default name is used.
- `removeDesktop(KWin::VirtualDesktop *desktop) const`
- `QString supportInformation() const`: support information about the running window manager
- `raiseWindow(KWin::Window *window)`: raises a window above all others
- `KWin::Window *getClient(qulonglong windowId)`: the window with the given ID, or null
- `QList<KWin::Window *> windowAt(const QPointF &pos, int count = 1) const`: up to `count` windows at a location, topmost first. A negative count returns all.
- `bool isEffectActive(const QString &pluginId) const`: whether an effect is loaded and currently active

## KWin::VirtualDesktop

Read-only properties:

- `QString id`
- `uint x11DesktopNumber`

Read-write properties:

- `QString name`

Signals:

- `nameChanged()`
- `x11DesktopNumberChanged()`
- `aboutToBeDestroyed()`: emitted just before the desktop is destroyed

## KWin::Output

### Enums

- `DpmsMode`: `On`, `Standby`, `Suspend`, `Off`
- `Capability`: `Dpms`, `Overscan`, `Vrr`, `RgbRange`, `HighDynamicRange`, `WideColorGamut`, `AutoRotation`, `IccProfile`, `Tearing`
- `SubPixel`: `Unknown`, `None`, `Horizontal_RGB`, `Horizontal_BGR`, `Vertical_RGB`, `Vertical_BGR`
- `RgbRange`: `Automatic`, `Full`, `Limited`
- `AutoRotationPolicy`: `Never`, `InTabletMode`, `Always`

### Read-only properties

- `QRect geometry`
- `qreal devicePixelRatio`
- `QString name`
- `QString manufacturer`
- `QString model`
- `QString serialNumber`

### Signals

- `geometryChanged()`
- `enabledChanged()`: the output was enabled or disabled
- `scaleChanged()`: the device pixel ratio changed
- `aboutToTurnOff(std::chrono::milliseconds time)`: the display will be dimmed in `time` milliseconds, so that effects can plan for it
- `wakeUp()`: the output was turned on
- `aboutToChange(OutputChangeSet *changeSet)`: the output is about to change configuration through user interaction. Only for effects.
- `changed()`: the output changed through user interaction. Only for effects.
- `currentModeChanged()`, `modesChanged()`, `outputChange(const QRegion &damagedRegion)`, `transformChanged()`, `dpmsModeChanged()`, `capabilitiesChanged()`, `overscanChanged()`, `vrrPolicyChanged()`, `rgbRangeChanged()`, `wideColorGamutChanged()`, `highDynamicRangeChanged()`, `autoRotationPolicyChanged()`, `iccProfileChanged()`, `iccProfilePathChanged()`, `brightnessMetadataChanged()`, `sdrGamutWidenessChanged()`, `colorDescriptionChanged()`, `referenceLuminanceChanged()`, `colorProfileSourceChanged()`, `brightnessChanged()`, `colorPowerTradeoffChanged()`, `dimmingChanged()`

### Functions

- `QPointF mapToGlobal(const QPointF &pos) const`
- `QPointF mapFromGlobal(const QPointF &pos) const`

## KWin::Window

### Enums

- `SizeMode`: `SizeModeAny`, `SizeModeFixedW`, `SizeModeFixedH`, `SizeModeMax`
- `SameApplicationCheck`: `RelaxedForActive`, `AllowCrossProcesses`

### Read-only properties

Geometry:

- `QRectF bufferGeometry`: the rectangle the window's pixmap or buffer occupies on the screen, including invisible portions such as client-side drop shadows
- `QRectF clientGeometry`: the geometry without frame borders
- `QPointF pos`, `QSizeF size`, `qreal x`, `qreal y`, `qreal width`, `qreal height`: the position and size of the frame geometry
- `QRectF rect`
- `KWin::Output *output`: the output the window's center is on
- `QRectF iconGeometry`: the optional geometry representing the minimized window, for example in a taskbar (`_NET_WM_ICON_GEOMETRY`)
- `QSizeF minSize`, `QSizeF maxSize`: the sizes given in `WM_NORMAL_HINTS`

Identity:

- `QString resourceName`, `QString resourceClass`, `QString windowRole`
- `QUuid internalId`: a unique ID for this window
- `int pid`: the process owning the window
- `QString caption`: the caption, from `WM_NAME` with a suffix for hostname and shortcut
- `QString captionNormal`: the caption without that suffix
- `QIcon icon`
- `QString desktopFileName`: the desktop file name of the application, normally the base name, such as `org.example.foo`, or a full path if it isn't in a standard location
- `QString colorScheme`: the requested color scheme, as an absolute path or a name in the user's config directory. An empty string means the default palette. It might differ from the applied theme if the scheme can't be found.

Window type. These follow the [`_NET_WM_WINDOW_TYPE` values](https://specifications.freedesktop.org/wm-spec/wm-spec-latest.html) unless noted:

- `bool desktopWindow`: a desktop background window, the one with the wallpaper
- `bool dock`: a panel
- `bool toolbar`: a standalone (detached) toolbar window
- `bool menu`: a torn-off menu
- `bool normalWindow`: an application or other window that no specialized type fits
- `bool dialog`
- `bool splash`: a splash screen. Many older applications don't mark theirs.
- `bool utility`: for example a tool window
- `bool dropdownMenu`: a popup opened directly or indirectly from the application's menu bar
- `bool popupMenu`: a popup menu that isn't torn off or dropdown
- `bool tooltip`
- `bool notification`
- `bool criticalNotification`: a window with a critical notification (non-standard type)
- `bool appletPopup`: an applet popup (non-standard type)
- `bool onScreenDisplay`: an on-screen display (non-standard type)
- `bool comboBox`: a combo box popup
- `bool dndIcon`: a drag and drop icon
- `int windowType`: the NETWM window type
- `bool specialWindow`: any special type (desktop, dock, splash and so on), usually without a frame or window management

State:

- `bool managed`: whether SonicWin manages this window, controlling its placement and more, as opposed to override-redirect windows
- `bool deleted`: an already deleted window, kept for the compositor's animations
- `bool popupWindow`: whether the window is a popup
- `bool outline`: whether this is the outline
- `int stackingOrder`: the window's position in the stack
- `bool active`: whether the window is active
- `bool transient`: whether the window is a transient of another
- `KWin::Window *transientFor`: the window it is a transient of, if any
- `bool modal`
- `bool move`, `bool resize`: whether the user is currently moving or resizing it
- `KWin::MaximizeMode maximizeMode`: `0` restored, `1` maximized vertically, `2` horizontally, `3` fully
- `bool decorationHasAlpha`: whether the decoration currently uses an alpha channel
- `bool providesContextHelp`: mostly for decorations, to decide whether to show the help button
- `bool hasApplicationMenu`: whether an application menu is available
- `bool applicationMenuActive`: whether the application menu is open
- `bool unresponsive`: whether the application failed to answer a ping in time, usually because it froze or crashed
- `KWin::Layer layer`
- `bool hidden`: usually true of auto-hiding panels
- `bool inputMethod`: whether it is an input method window

Abilities. These are evaluated each time they are read, so they have no notify signal:

- `bool fullScreenable`, `bool closeable`, `bool shadeable`, `bool minimizable`, `bool maximizable`, `bool resizeable`
- `bool moveable`: a window that isn't movable might still be movable to another screen
- `bool moveableAcrossScreens`
- `bool wantsInput`: whether it can accept keyboard focus

### Read-write properties

- `qreal opacity`
- `bool skipsCloseAnimation`: the window doesn't want to be animated on close. A screenshot application, for example, may not want its window captured.
- `bool fullScreen`: to be sure the state changed, connect to the notify signal
- `QList<KWin::VirtualDesktop *> desktops`: the desktops the window is on. Empty means all desktops.
- `bool onAllDesktops`
- `QStringList activities`: the activities the window is on. Empty means all activities.
- `bool skipTaskbar`, `bool skipPager`, `bool skipSwitcher`: exclude it from taskbars, pagers and window switching
- `bool keepAbove`, `bool keepBelow`
- `bool shade`, `bool minimized`
- `bool demandsAttention`: whether `_NET_WM_STATE_DEMANDS_ATTENTION` is set, meaning something happened in or with the window
- `QRectF frameGeometry`: the geometry of the window. Depending on the resize mode, `frameGeometryChanged` might be emitted at each step or only at the end.
- `bool noBorder`: whether the window has no decoration. Whether it has a border is the window manager's decision, not the application's.
- `KWin::Tile *tile`: the tile this window is associated with, if any

### Signals

- `stackingOrderChanged()`, `shadeChanged()`, `opacityChanged(KWin::Window *window, qreal oldOpacity)`, `damaged(KWin::Window *window)`, `inputTransformationChanged()`, `closed()`
- `outputChanged()`: the window's screen changed, because a screen was added or removed or the geometry changed
- `skipCloseAnimationChanged()`, `windowRoleChanged()`, `windowClassChanged()`, `surfaceChanged()`, `shadowChanged()`
- `bufferGeometryChanged(const QRectF &oldGeometry)`, `frameGeometryChanged(const QRectF &oldGeometry)`, `clientGeometryChanged(const QRectF &oldGeometry)`
- `frameGeometryAboutToChange()`: the new geometry isn't known yet
- `visibleGeometryChanged()`
- `tileChanged(KWin::Tile *tile)`: the associated tile changed, including from and to none
- `requestedTileChanged()`, `offscreenRenderingChanged()`, `targetScaleChanged()`, `nextTargetScaleChanged()`, `noBorderChanged()`, `borderRadiusChanged()`
- `fullScreenChanged()`, `skipTaskbarChanged()`, `skipPagerChanged()`, `skipSwitcherChanged()`, `iconChanged()`, `activeChanged()`
- `keepAboveChanged(bool)`, `keepBelowChanged(bool)`, `demandsAttentionChanged()`, `desktopsChanged()`, `activitiesChanged()`, `minimizedChanged()`
- `paletteChanged(const QPalette &p)`, `colorSchemeChanged()`, `captionChanged()`, `captionNormalChanged()`
- `maximizedAboutToChange(MaximizeMode mode)`, `maximizedChanged()`
- `transientChanged()`, `modalChanged()`, `quickTileModeChanged()`, `moveResizedChanged()`, `moveResizeCursorChanged(CursorShape)`
- `interactiveMoveResizeStarted()`, `interactiveMoveResizeStepped(const QRectF &geometry)`, `interactiveMoveResizeFinished()`
- `closeableChanged(bool)`, `minimizeableChanged(bool)`, `shadeableChanged(bool)`, `maximizeableChanged(bool)`
- `desktopFileNameChanged()`, `applicationMenuChanged()`, `hasApplicationMenuChanged(bool)`, `applicationMenuActiveChanged(bool)`
- `unresponsiveChanged(bool)`, `decorationChanged()`, `hiddenChanged()`, `hiddenByShowDesktopChanged()`, `lockScreenOverlayChanged()`, `readyForPaintingChanged()`, `maximizeGeometryRestoreChanged()`, `fullscreenGeometryRestoreChanged()`

### Functions

- `closeWindow()`
- `setMaximize(bool vertically, bool horizontally)`: sets the maximization

## KWin::TileManager

- `KWin::Tile *rootTile` (read-only)
- `TileModel *model` (read-only)
- `tileRemoved(KWin::Tile *tile)` (signal)
- `KWin::Tile *bestTileForPosition(qreal x, qreal y)`

## KWin::Tile

`LayoutDirection` is `Floating`, `Horizontal` or `Vertical`.

Read-only properties:

- `QRectF absoluteGeometry`, `QRectF absoluteGeometryInScreen`
- `int positionInLayout`
- `Tile *parent`
- `QList<KWin::Tile *> tiles`
- `QList<KWin::Window *> windows`
- `bool isLayout`, `bool canBeRemoved`

Read-write properties:

- `QRectF relativeGeometry`
- `qreal padding`

Signals: `relativeGeometryChanged()`, `absoluteGeometryChanged()`, `windowGeometryChanged()`, `paddingChanged(qreal padding)`, `rowChanged(int row)`, `isLayoutChanged(bool isLayout)`, `childTilesChanged()`, `windowAdded(Window *window)`, `windowRemoved(Window *window)`, `windowsChanged()`

Functions:

- `resizeByPixels(qreal delta, Qt::Edge edge)`

## Global in scripted effects

Methods and properties added to the global JavaScript object of [scripted effects](../kwineffect/index.md).

### Read-only properties

- `KWin::EffectsHandler effects`: the core wrapper of the effects system
- `KWin::ScriptedEffect effect`: the actual effect
- `object Effect`: access to the enums of `KWin::AnimationEffect` and `KWin::ScriptedEffect`
- `object KWin`: access to the enums of `KWin::WorkspaceWrapper`
- `object QEasingCurve`: access to the enums of `QEasingCurve`

### Functions

- `QList<quint64> animate(settings)`: schedules one or many animations for one window. The settings object declares them, as shown below. At least one animation or attribute setter must be given, in the top-level properties or in `animations`.
- `QList<quint64> set(settings)`: like `animate`, except that the change doesn't end with the animation. The attribute stays at the target value until you cancel it.
- `bool cancel(QList<quint64>)`: cancels animations returned by `animate` or `set`. A single value also works.
- `print(QVariant ... values)`: prints all provided values
- `int animationTime(int duration)`: adjusts a duration by the global animation time factor
- `int displayWidth()`, `int displayHeight()`: the size of the complete display, all screens together
- `bool registerScreenEdge(ElectricBorder border, QJSValue callback)`: registers the callback for a screen edge
- `bool registerShortcut(QString title, QString text, QString keySequence, QJSValue callback)`: registers a global shortcut
- `uint addFragmentShader(ShaderTrait traits, QString fragmentShaderFile)`: creates a shader and returns an ID usable in `animate` or `set`. The source must be in the `shaders` subdirectory of the package's `contents` directory, with the extension `frag`. The vertex shader is generated from the `ShaderTrait` flags.
- `uint setUniform(uint shaderId, QString name, QJSValue value)`: updates a uniform of a shader. The value can be a float (integer uniforms aren't supported), an array of 2, 3 or 4 numbers, a color string or a color as returned by `readConfig`.

The settings object:

```js
{
    window: EffectWindow,      // the window to animate, required
    duration: int,             // duration in ms, required
    curve: QEasingCurve.Type,  // global easing curve, optional
    type: Effect.Attribute,    // for the first animation, optional
    from: FPx2,                // for the first animation, optional
    to: FPx2,                  // for the first animation, optional
    delay: int,                // for the first animation, optional
    shader: int,               // for the first animation, optional
    animations: [              // additional animations, optional
        {
            curve: QEasingCurve.Type, // overrides the global one
            type: Effect.Attribute,
            from: FPx2,
            to: FPx2,
            delay: int,
            shader: int
        }
    ]
}
```

## KWin::EffectsHandler

The manager class that handles all the effects.

`OnScreenMessageHideFlag`: `SkipsCloseAnimation` means the on-screen message should skip the close animation.

### Read-only properties

- `QStringList activeEffects`, `QStringList loadedEffects`, `QStringList listOfEffects`
- `QString currentActivity`
- `QSize desktopGridSize`, `int desktopGridWidth`, `int desktopGridHeight`, `int workspaceWidth`, `int workspaceHeight`
- `QList<KWin::VirtualDesktop *> desktops`
- `bool optionRollOverDesktops`
- `KWin::Output *activeScreen`
- `qreal animationTimeFactor`: the factor to multiply animation speed by. Get the actual value with `animationTime()`. It can be 0, so make sure your code copes with a time of 0 ms if used manually.
- `QList<EffectWindow *> stackingOrder`
- `bool decorationsHaveAlpha`: whether decorations use the alpha channel
- `CompositingType compositingType`
- `QPointF cursorPos`
- `QSize virtualScreenSize`, `QRect virtualScreenGeometry`
- `bool hasActiveFullScreenEffect`
- `KWin::SessionState sessionState`: the state of the session, for example whether the user is logging out
- `bool colorPickerActive`

### Read-write properties

- `KWin::VirtualDesktop *currentDesktop`
- `KWin::EffectWindow *activeWindow`

### Signals

- `screenAdded(KWin::Output *screen)`, `screenRemoved(KWin::Output *screen)`
- `desktopChanged(KWin::VirtualDesktop *oldDesktop, KWin::VirtualDesktop *newDesktop, KWin::EffectWindow *with)`: the current desktop changed. `with` is the window taken over to the new desktop, and can be null.
- `desktopChanging(KWin::VirtualDesktop *currentDesktop, QPointF offset, KWin::EffectWindow *with)`: emitted during the animation. `offset` is the current offset: an `x` of 0.6 means 60% of the way to the desktop to the right. Positive values mean up and right.
- `desktopChangingCancelled()`, `desktopAdded(KWin::VirtualDesktop *desktop)`, `desktopRemoved(KWin::VirtualDesktop *desktop)`
- `desktopGridSizeChanged(const QSize &size)`, `desktopGridWidthChanged(int width)`, `desktopGridHeightChanged(int height)`
- `showingDesktopChanged(bool)`: the show desktop state changed. The desktop rises to the keep-above layer, so you may want to elevate windows.
- `windowAdded(KWin::EffectWindow *w)`: a new window was added
- `windowClosed(KWin::EffectWindow *w)`: a window is being removed. An effect that animates closing should connect to this and reference the window.
- `windowActivated(KWin::EffectWindow *w)`: a window was activated, or null if there is no active window
- `windowDeleted(KWin::EffectWindow *w)`: a closed window is no longer referenced. Effects keeping track of closed windows should clean up here.
- `tabBoxAdded(int mode)`: a task switcher was added. An effect replacing it should reference it.
- `tabBoxClosed()`: the switcher was closed
- `tabBoxUpdated()`: the selected window or the list changed
- `tabBoxKeyEvent(QKeyEvent *event)`: a key not handled by the switcher was pressed while it was active
- `mouseChanged(const QPointF &pos, const QPointF &oldpos, Qt::MouseButtons buttons, Qt::MouseButtons oldbuttons, Qt::KeyboardModifiers modifiers, Qt::KeyboardModifiers oldmodifiers)`: the mouse changed. An effect needing updated positions must first call `startMousePolling`.
- `cursorShapeChanged()`: the cursor shape changed. This connection is tracked, so disconnect when you no longer need it to stop cursor event filtering.
- `propertyNotify(KWin::EffectWindow *w, long atom)`: receives events registered with `registerPropertyType`. Use `readProperty()` for the data. The property may already be set on the window, so doing the same from `windowAdded` is usually needed. `w` is null for a property of the root window.
- `currentActivityAboutToChange()`, `currentActivityChanged(const QString &id)`, `activityAdded(const QString &id)`, `activityRemoved(const QString &id)`
- `screenLockingChanged(bool locked)`: the screen was locked or unlocked
- `screenAboutToLock()`: emitted just before the screen locker grabs keys. Effects should release any grabs immediately.
- `stackingOrderChanged()`: a window was raised or lowered
- `screenEdgeApproaching(ElectricBorder border, qreal factor, const QRect &geometry)`: the mouse is approaching an edge. `factor` runs from 0.0, when first entered and on leaving, to 1.0 at the edge, which suits animations.
- `virtualScreenSizeChanged()`, `virtualScreenGeometryChanged()`
- `windowDataChanged(KWin::EffectWindow *w, int role)`: the data on a window for a role changed. An effect that doesn't work on windows grabbed by another effect can, for example, cancel its animation when a grab is added.
- `xcbConnectionChanged()`: the xcb connection was created or destroyed. Effects can use this to refetch properties. The root window also becomes invalid.
- `activeFullScreenEffectChanged()`, `hasActiveFullScreenEffectChanged()`, `sessionStateChanged()`, `colorPickerActiveChanged()`
- `startupAdded(const QString &id, const QIcon &icon)`, `startupChanged(const QString &id, const QIcon &icon)`, `startupRemoved(const QString &id)`

### Functions

- `reconfigureEffect(const QString &name)`, `bool loadEffect(const QString &name)`, `toggleEffect(const QString &name)`, `unloadEffect(const QString &name)`
- `bool isEffectLoaded(const QString &name) const`, `bool isEffectSupported(const QString &name)`, `QList<bool> areEffectsSupported(const QStringList &names)`
- `QString supportInformation(const QString &name) const`, `QString debug(const QString &name, const QString &parameter = QString()) const`
- `moveWindow(KWin::EffectWindow *w, const QPoint &pos, bool snap = false, double snapAdjust = 1.0)`
- `windowToDesktops(KWin::EffectWindow *w, const QList<KWin::VirtualDesktop *> &desktops)`: moves a window to the given desktops; it ends up on the last in the list, and an empty list means all desktops
- `windowToScreen(KWin::EffectWindow *w, Output *screen)`
- `KWin::VirtualDesktop *desktopAbove(KWin::VirtualDesktop *desktop = nullptr, bool wrap = true) const`, and likewise `desktopToRight`, `desktopBelow` and `desktopToLeft`: the neighboring desktop, wrapping around if `wrap` is set, starting from the current desktop if none is given
- `QString desktopName(KWin::VirtualDesktop *desktop) const`
- `KWin::EffectWindow *findWindow(WId id) const`
- `KWin::EffectWindow *findWindow(QWindow *w) const`: finds the window for an internal window
- `KWin::EffectWindow *findWindow(const QUuid &id) const`: finds a window by its internal ID
- `setElevatedWindow(KWin::EffectWindow *w, bool set)`
- `addRepaintFull()`: schedules the whole workspace to be repainted next time. During painting, it doesn't affect the current paint.
- `addRepaint(const QRectF &r)`, `addRepaint(const QRect &r)`, `addRepaint(const QRegion &r)`, `addRepaint(int x, int y, int w, int h)`

## KWin::EffectWindow

Represents a window used by effects.

Paint flags: `PAINT_DISABLED`, `PAINT_DISABLED_BY_DESKTOP`, `PAINT_DISABLED_BY_MINIMIZE`, `PAINT_DISABLED_BY_ACTIVITY`

### Read-only properties

- `QRectF geometry`, `QRectF expandedGeometry`, `QRectF rect`, `QPointF pos`, `QSizeF size`, `qreal x`, `qreal y`, `qreal width`, `qreal height`
- `qreal opacity`
- `KWin::Output *screen`
- `QList<KWin::VirtualDesktop *> desktops`, `bool onAllDesktops`, `bool onCurrentDesktop`
- `QString windowClass`, `QString windowRole`, `QString caption`, `QIcon icon`
- `bool desktopWindow`, `bool dock`, `bool toolbar`, `bool menu`, `bool normalWindow`, `bool dialog`, `bool splash`, `bool utility`, `bool dropdownMenu`, `bool popupMenu`, `bool tooltip`, `bool notification`, `bool criticalNotification`, `bool onScreenDisplay`, `bool comboBox`, `bool dndIcon`: the window types, as for [Window](#kwinwindow)
- `int windowType`
- `bool specialWindow`
- `bool deleted`: an already deleted window, kept for animations
- `bool keepAbove`, `bool keepBelow`, `bool modal`, `bool fullScreen`, `bool unresponsive`
- `bool moveable`, `bool moveableAcrossScreens`, `bool move`, `bool resize`
- `QSizeF basicUnit`: how much the window wishes to grow or shrink at least. For information only; don't rely on it.
- `QRectF iconGeometry`
- `bool skipSwitcher`
- `QRectF contentsRect`: the geometry of the window's contents inside the whole window
- `bool hasDecoration`, `bool decorationHasAlpha`
- `QStringList activities`, `bool onCurrentActivity`, `bool onAllActivities`
- `bool visible`: not minimized, and on the current desktop and activity
- `bool skipsCloseAnimation`: an animation on close isn't useful, as the window won't be visible
- `bool x11Client`: whether this is an X11 client
- `bool popupWindow`
- `QWindow *internalWindow`: the internal window, or null
- `bool outline`
- `pid_t pid`: the process the window belongs to
- `bool lockScreen`: whether this is the screen locker's greeter
- `bool hiddenByShowDesktop`

### Read-write properties

- `bool minimized`

### Signals

- `windowStartUserMovedResized(KWin::EffectWindow *w)`: the user began moving or resizing. Only one window can be moved or resized at a time.
- `windowStepUserMovedResized(KWin::EffectWindow *w, const QRectF &geometry)`: the geometry changed during that. The window's geometry might not match `geometry` until the end, depending on the mode.
- `windowFinishUserMovedResized(KWin::EffectWindow *w)`: the user finished
- `windowMaximizedStateChanged(KWin::EffectWindow *w, bool horizontal, bool vertical)`: the maximized state changed
- `windowMaximizedStateAboutToChange(KWin::EffectWindow *w, bool horizontal, bool vertical)`: emitted before any change, useful for grabbing an image of the window first
- `windowFrameGeometryChanged(KWin::EffectWindow *window, const QRectF &oldGeometry)`
- `windowFrameGeometryAboutToChange(KWin::EffectWindow *window)`: the new geometry isn't known yet
- `windowOpacityChanged(KWin::EffectWindow *w, qreal oldOpacity, qreal newOpacity)`
- `minimizedChanged(KWin::EffectWindow *w)`
- `windowModalityChanged(KWin::EffectWindow *w)`
- `windowUnresponsiveChanged(KWin::EffectWindow *w, bool unresponsive)`
- `windowDamaged(KWin::EffectWindow *w)`: an area is scheduled for repainting
- `windowKeepAboveChanged(KWin::EffectWindow *w)`, `windowKeepBelowChanged(KWin::EffectWindow *w)`, `windowFullScreenChanged(KWin::EffectWindow *w)`, `windowDecorationChanged(KWin::EffectWindow *window)`
- `windowExpandedGeometryChanged(KWin::EffectWindow *window)`: the visible geometry changed
- `windowDesktopsChanged(KWin::EffectWindow *window)`: the window entered or left a virtual desktop
- `windowHiddenChanged()`

### Functions

- `addRepaint(const QRect &r)`, `addRepaint(int x, int y, int w, int h)`, `addRepaintFull()`, `addLayerRepaint(const QRect &r)`, `addLayerRepaint(int x, int y, int w, int h)`
- `bool isOnActivity(const QString &id) const`, `bool isOnDesktop(KWin::VirtualDesktop *desktop) const`
- `KWin::EffectWindow *findModal()`, `KWin::EffectWindow *transientFor()`, `QList<KWin::EffectWindow *> mainWindows() const`
- `closeWindow()`
- `setData(int role, const QVariant &data)`: stores arbitrary data, and emits `windowDataChanged`
- `QVariant data(int role) const`

## KWin::AnimationEffect

- `Anchor`: `Left`, `Top`, `Right`, `Bottom`, `Horizontal`, `Vertical`, `Mouse`
- `Attribute`: `Opacity`, `Brightness`, `Saturation`, `Scale`, `Rotation`, `Position`, `Size`, `Translation`, `Clip`, `Generic`, `CrossFadePrevious`, `Shader`, `ShaderUniform`, `NonFloatBase`
  - `Shader` animates with a provided shader, whose float uniform `animationProgress` is the animation's progress.
  - `ShaderUniform` also animates a float uniform passed to the shader, whose location is given as metadata.
- `MetaType`: `SourceAnchor`, `TargetAnchor`, `RelativeSourceX`, `RelativeSourceY`, `RelativeTargetX`, `RelativeTargetY`, `Axis`
- `Direction`: `Forward`, `Backward`
- `TerminationFlag`:
  - `DontTerminate`: don't end when reaching the source or target position
  - `TerminateAtSource`: end at the source position, which the animation can reach if its direction was changed to backward
  - `TerminateAtTarget`: end at the target position. Without this flag, the animation is persistent.

## KWin::ScriptedEffect

### Enums

- `DataRole`: `WindowAddedGrabRole`, `WindowClosedGrabRole`, `WindowMinimizedGrabRole`, `WindowUnminimizedGrabRole`, `WindowForceBlurRole`, `WindowForceBackgroundContrastRole`
- `EasingCurve`: `GaussianCurve`
- `ShaderTrait`: `MapTexture`, `UniformColor`, `Modulate`, `AdjustSaturation`

### Read-only properties

- `QString pluginId`: the effect's plugin ID
- `bool isActiveFullScreenEffect`: whether this is the active fullscreen effect

### Signals

- `configChanged()`: the effect's configuration changed
- `animationEnded(KWin::EffectWindow *w, quint64 animationId)`
- `isActiveFullScreenEffectChanged()`

### Functions

- `bool borderActivated(ElectricBorder border)`
- `bool isGrabbed(KWin::EffectWindow *w, DataRole grabRole)`: whether another effect has grabbed the window with that role
- `bool grab(KWin::EffectWindow *w, DataRole grabRole, bool force = false)`: grabs the window. Unless `force` is true, a window grabbed by another effect isn't grabbed. Returns whether it succeeded.
- `bool ungrab(KWin::EffectWindow *w, DataRole grabRole)`: ungrabs the window. Returns whether it succeeded.
- `QJSValue readConfig(const QString &key, const QJSValue &defaultValue = QJSValue())`: reads a configuration value
- `int displayWidth() const`, `int displayHeight() const`, `int animationTime(int defaultTime) const`
- `registerShortcut(const QString &objectName, const QString &text, const QString &keySequence, const QJSValue &callback)`
- `bool registerScreenEdge(int edge, const QJSValue &callback)`, `bool registerRealtimeScreenEdge(int edge, const QJSValue &callback)`, `bool unregisterScreenEdge(int edge)`
- `bool registerTouchScreenEdge(int edge, const QJSValue &callback)`, `bool unregisterTouchScreenEdge(int edge)`, `QList<int> touchEdgesForAction(const QString &action) const`
- `quint64 animate(KWin::EffectWindow *window, Attribute attribute, int ms, const QJSValue &to, const QJSValue &from = QJSValue(), uint metaData = 0, int curve = QEasingCurve::Linear, int delay = 0, bool fullScreen = false, bool keepAlive = true, uint shaderId = 0)`
- `QJSValue animate(const QJSValue &object)`
- `quint64 set(KWin::EffectWindow *window, Attribute attribute, int ms, const QJSValue &to, const QJSValue &from = QJSValue(), uint metaData = 0, int curve = QEasingCurve::Linear, int delay = 0, bool fullScreen = false, bool keepAlive = true, uint shaderId = 0)`
- `QJSValue set(const QJSValue &object)`
- `bool retarget(quint64 animationId, const QJSValue &newTarget, int newRemainingTime = -1)`, and the same with `const QList<quint64> &animationIds`
- `bool freezeInTime(quint64 animationId, qint64 frozenTime)`, and the same with a list
- `bool redirect(quint64 animationId, Direction direction, TerminationFlags terminationFlags = TerminateAtSource)`, and the same with a list
- `bool complete(quint64 animationId)`, and the same with a list
- `bool cancel(quint64 animationId)`, and the same with a list
- `uint addFragmentShader(ShaderTrait traits, const QString &fragmentShaderFile = {})`
- `setUniform(uint shaderId, const QString &name, const QJSValue &value)`
