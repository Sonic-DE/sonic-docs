---
title: UVC Viewer
description: Watch a games console, set-top box or camera on your screen through a USB capture device.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-tv-interface b54d2264 (uvcviewer/README.md, uvcviewer/src/Main.qml, uvcviewer/src/CameraHomePage.qml, uvcviewer/src/UvcViewer.qml, uvcviewer/org.kde.plasma.bigscreen.uvcviewer.desktop); written from the code, not clicked through"
---

# UVC Viewer

UVC Viewer shows the picture from a USB video device, such as an HDMI capture card or a webcam. It's made for the [TV interface](../tv.md): connect a set-top box or games console to a capture card, and watch it on the TV. It works in the other SonicDE sessions too.

Open it from the application launcher, as **UVC Viewer**, or by running `plasma-bigscreen-uvcviewer`.

## Watching a device

1. Connect the capture device.
2. On **Select Media Device**, choose it from the list with the mouse, or with the arrow keys and Enter on a remote or keyboard. If nothing is connected, the page says “No video devices found”.
3. The picture fills the window. It's cropped to fill the screen if its shape differs.

Press the back button on your remote, or Esc, to return to the list.

UVC Viewer only shows the picture; it doesn't play the device's sound.
