---
title: System Monitor Sensor widget
description: Show charts of processor, memory, disk and network use on your desktop or panel.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (applets/systemmonitor), sonic-system-monitor-library (faces/ConfigAppearance.qml, faces/ConfigSensors.qml); written from the code, not clicked through"
---

# System Monitor Sensor widget

The System Monitor Sensor widget shows a chart or a number for any value your system measures, such as how busy the processor is or how full a disk is. You can put it on the desktop or in a panel.

**Add Widgets** offers it as **System Monitor Sensor**, which starts empty so you can choose what it shows, and as ready-made versions:

- **Individual Core Usage:** The load of each processor core.
- **Total CPU Use:** The load of the whole processor.
- **Hard Disk Activity:** How much is read from and written to the disks.
- **Disk Usage:** How full the root partition is.
- **Memory Usage:** How much physical memory is in use.
- **Network Speed:** How fast data is downloaded and uploaded.

All of them are the same widget with different settings, so you can change any of them into something else.

## Settings

The widget's settings have three pages:

- **Appearance:**
  - **Presets:** **Load Preset...** loads saved settings; you can also get new presets from the Internet, and **Save Settings As Preset** saves the current ones for later.
  - **Title:** The text shown above the chart. **Show Title** turns it on or off.
  - **Display Style:** How the values are drawn: **Line Chart**, **Bar Chart**, **Horizontal Bars**, **Pie Chart**, **Grid**, **Color Grid** or **Text Only**. **Get New Display Styles...** finds more.
  - **Minimum Time Between Updates:** How often the widget refreshes, or **No Limit**.
- A details page for the display style, named after it, for example **Line Chart Details**. It holds the options of that style.
- **Sensors Details:** Choose the values to show. **Sensors** are drawn in the chart. Depending on the display style, there are also **Total Sensors**, shown as a summary, and **Text-Only Sensors**, listed as text without a chart.
