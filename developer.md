---
title: Developer Documentation
description: Documentation for people building Sonic-DE from source or contributing to it.
---

# Developer Documentation

This tier is for people building Sonic-DE from source or contributing to it.

- [Building Sonic-DE](developer/building.md) explains how to fetch and build the whole
  desktop from source with sonicde-builder.
- [Dependencies](developer/dependencies.md) lists what a build host needs.
- [Troubleshooting](developer/troubleshooting.md) collects known build problems.
- [Kirigami tutorial](developer/kirigami/setup-cpp.md): build convergent applications with
  QML and Kirigami, from a first window to C++ models and Kirigami Addons.
- [Python with Kirigami](developer/python/app.md): write and package a Kirigami application
  with PySide, and use the frameworks' Python bindings.
- [Getting started with KXmlGui](developer/kxmlgui/index.md): a tutorial that builds a small
  text editor with SonicDE's libraries.
- [Common programming mistakes](developer/common-programming-mistakes.md) in C++ and Qt code.
- [SSH password prompt](developer/ssh-password-prompt.md): ask for SSH passphrases in a window
  with `ksshaskpass`, and save them in KDE Wallet.
- [Configuration](developer/configuration/introduction.md): storing settings with KConfig and
  KConfig XT, settings modules (KCMs) and configuration updates.
- [Libraries](developer/libraries/karchive.md): archives, idle time, notifications, hardware
  (Solid) and spell checking (Sonnet).
- [KAuth](developer/kauth/introduction.md): running privileged parts of your application.
- [Desktop integration](developer/additional/desktop-file.md): desktop files, icons, cursor
  themes and session management.
- [Themes and plugins](developer/plasma/index.md): desktop themes, widgets, desktop scripting,
  KRunner plugins, SonicWin scripts and effects, window decorations, task switchers,
  wallpapers and comic plugins.
- [Ecco](developer/ecco/index.md): add your own actions to the file manager's context menu.
- [Sensor faces](developer/sensor-faces.md): create new display styles for System Monitor.
- [System administration](developer/administration/index.md): lock down deployments with Kiosk,
  and set default favorites, About page branding and portal permissions.
- [Mobile interface](developer/mobile/index.md): the shell for phones, porting a device and the
  telephony stack.
- [D-Bus](developer/dbus/introduction.md): how to call and offer D-Bus interfaces from your
  own code. SonicDE is gradually moving its own communication between processes to
  [Sonic IPC](/docs/api/sonicipc/sonicipc-index).
- [Human Interface Guidelines](developer/hig/index.md): how to design applications and icons
  that feel at home on SonicDE.

To write applications or plugins against the Sonic-DE libraries, see the
[API Documentation](/docs/api).
