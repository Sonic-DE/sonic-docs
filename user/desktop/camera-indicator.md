---
title: Camera Indicator
description: See in the system tray whether an application is using your camera.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (applets/cameraindicator: qml/main.qml, qml/FullRepresentation.qml, CMakeLists.txt); written from the code, not clicked through"
---

# Camera Indicator

The Camera Indicator shows you when an application is using a camera, such as your webcam. It sits in the [System Tray](system-tray.md) and only appears while a camera is being used or is ready to be used. Hover over its icon to see how many cameras are in use.

Click the icon to see more. With one camera, the pop-up says whether it's in use, for example "Integrated Camera is in use". With more than one, it lists each camera with its name and state:

- **Active:** An application is using the camera right now.
- **Idle:** The camera is ready, but nothing is being recorded.
- **Suspended**, **Creating** or **Error:** The camera is paused, being set up, or has a problem.

The Camera Indicator works with cameras handled by PipeWire. It's only included when SonicDE is built with PipeWire, so it may be missing on some systems.
