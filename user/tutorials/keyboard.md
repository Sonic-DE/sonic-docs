---
title: Keyboard actions
description: Find out what a key sends, and assign it an action such as muting the audio.
source_url: https://userbase.kde.org/Tutorials/Keyboard
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (kcms/keys); read from code, not clicked through"
---

# Keyboard actions

Keyboard actions are actions the system triggers when you press a key. Most should be set by default the way you want them. This page helps you with your own settings. The most prominent examples are the "raise audio volume" key and its siblings, "lower audio volume" and "mute audio", on some multimedia keyboards.

## Background

When you press a key, an electronic signal goes over the USB or PS/2 port to the computer. There it's received by the Linux kernel and forwarded to the X Window System. The X Window System receives the *scancodes* of the keys being pressed and maps them to key events, for example `XF86AudioMute`. To change this mapping, use the `xmodmap` command. To see what a key press causes, use the `xev` command.

## Example: the Audio Mute button

If your keyboard's Audio Mute button doesn't work, first find out whether it really triggers the right X Window System event. [Open a console](open-a-console.md) and enter:

```sh
xev
```

Move your mouse into the window that opens. Keep your console in view and press the key. You'll see output like this on your console:

```text
KeyRelease event, serial 35, synthetic NO, window 0x4000001,
    root 0x15a, subw 0x4000002, time 63106815, (43,37), root:(1279,877),
    state 0x10, keycode 121 (keysym 0x1008ff12, XF86AudioMute), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```

This means your key triggers the event `XF86AudioMute`. Now open the [Shortcuts](../settings/shortcuts.md) module in System Settings. Find the audio mute action, click **Add New**, and press the key you want to use to mute your audio.
