---
title: "KCursor Class"
description: "The KCursor class provides a set of static convenience methods for auto-hiding cursors on widgets."
---

# KCursor Class

The [KCursor](kcursor.md) class provides a set of static convenience methods for auto-hiding cursors on widgets. [More...](#details)

- **Header:** `#include <KCursor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

[List of all members, including inherited members](kcursor-members.md)

## Static Public Members

- [void autoHideEventFilter(QObject \*, QEvent \*)](#autoHideEventFilter)
- [int hideCursorDelay()](#hideCursorDelay)
- [void setAutoHideCursor(QWidget \*w, bool enable, bool customEventFilter = false)](#setAutoHideCursor)
- [void setHideCursorDelay(int ms)](#setHideCursorDelay)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[static\] void KCursor::autoHideEventFilter(*QObject \**, *QEvent \**) {#autoHideEventFilter}

[KCursor](kcursor.md) has to install an eventFilter over the widget you want to auto-hide. If you have an own eventFilter() on that widget and stop some events by returning true, you might break auto-hiding, because [KCursor](kcursor.md) doesn't get those events.

In this case, you need to call [setAutoHideCursor](kcursor.md#setAutoHideCursor)( widget, true, true ); to tell [KCursor](kcursor.md) not to install an eventFilter. Then you call this method from the beginning of your eventFilter, for example:

```cpp
edit = new KEdit( this, "some edit widget" );
edit->installEventFilter( this );
KCursor::setAutoHideCursor( edit, true, true );

[...]

bool YourClass::eventFilter( QObject *o, QEvent *e )
{
    if ( o == edit ) // only that widget where you enabled auto-hide!
        KCursor::autoHideEventFilter( o, e );

    // now you can do your own event-processing
    [...]
}
```

Note that you must not call KCursor::autoHideEventFilter() when you didn't enable or after disabling auto-hiding.

### \[static\] int KCursor::hideCursorDelay() {#hideCursorDelay}

Returns the current auto-hide delay time.

Default is 5000, i.e. 5 seconds.

*See also* [setHideCursorDelay](kcursor.md#setHideCursorDelay)()

### \[static\] void KCursor::setAutoHideCursor(QWidget \**w*, bool *enable*, bool *customEventFilter* = false) {#setAutoHideCursor}

Sets auto-hiding the cursor for widget `w`. Enabling it will result in the cursor being hidden when

- a key-event happens
- there are no key-events for a configured time-frame (see [setHideCursorDelay](kcursor.md#setHideCursorDelay)())

The cursor will be shown again when the focus is lost or a mouse-event happens.

Side effect: when enabling auto-hide, mouseTracking is enabled for the specified widget, because it's needed to get mouse-move-events. So don't disable mouseTracking for a widget while using auto-hide for it.

When disabling auto-hide, mouseTracking will be disabled, so if you need mouseTracking after disabling auto-hide, you have to re-enable mouseTracking.

If you want to use auto-hiding for widgets that don't take focus, e.g. a QCanvasView, then you have to pass all key-events that should trigger auto-hiding to [autoHideEventFilter](kcursor.md#autoHideEventFilter)().

### \[static\] void KCursor::setHideCursorDelay(int *ms*) {#setHideCursorDelay}

Sets the delay time in milliseconds for auto-hiding. When no keyboard events arrive for that time-frame, the cursor will be hidden.

Default is 5000, i.e. 5 seconds.

*See also* [hideCursorDelay](kcursor.md#hideCursorDelay)()
