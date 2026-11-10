---
title: Clocks
description: The clock widgets available for your desktop and panels.
source_url: https://userbase.kde.org/Plasma/Clocks
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (applets/digital-clock, analog-clock, calendar, plasmacalendarintegration), sonic-workspace-addons (applets/binary-clock, fuzzy-clock, plasmacalendarplugins); read from code, not clicked through"
---

# Clocks

Several widgets let you display the time on your desktop or in a panel.

![The Analog Clock on the desktop and the Digital Clock in the panel, in an older version](images/clocks.png)

See [Widgets](overview.md#widgets) for how to add a widget to the desktop or a panel, and how to move it or change its size.

All the clock widgets display the system time unless you tell them to use another time zone. To change the system time, use the [Date & Time](../settings/date-time.md) module. Click any clock widget and a calendar pops up. Click anywhere outside the calendar to make it disappear.

By default, there is one clock widget on the right of the panel. This page concentrates on that clock, but everything here also applies to clock widgets on the desktop.

Right-click for a context menu. **Show Alternatives…** lets you pick another clock widget, and **Configure** lets you configure the current one.

![The alternative clock widgets](images/clock-alternatives.png)

You can choose between an analog clock, a binary clock, a digital clock, a calendar and a fuzzy clock.

**Analog clock:** A classic clock with hands. Its settings can add a second hand and show the time zone.

**Binary clock:** Shows the time in binary, by lighting up LEDs. On its **Appearance** page, **Show:** has two check boxes: **Inactive lights** also draws the LEDs that are off, and **Seconds** adds two columns for the seconds. Under **Use custom color for:**, **Active lights** and **Inactive lights** each have their own check box and color button, so you can color the lit and the unlit LEDs separately.

**Digital clock:** Shows the time as on a digital watch. It has more settings than the others, described in [Digital clock settings](#digital-clock-settings) below.

**Fuzzy clock:** Shows the time as a spoken expression, like "Twenty to six". Its settings can make the font bold or italic and adjust the fuzziness. At maximum accuracy it changes every five minutes, and as fuzziness increases the changes get further apart. At maximum fuzziness it may only say "Weekend".

**Calendar:** Doesn't display a clock, but a calendar view instead. Its settings can show week numbers. When it sits in a panel as an icon, **Compact version:** chooses what the icon shows: **Show day of the month** or **Show week number**.

## Digital clock settings

The Digital Clock's settings have three tabs: **Appearance**, **Calendar** and **Time Zones**.

### Appearance

- **Information:** **Show date** adds the date. In a horizontal panel, the list next to it chooses where the date goes: **Adaptive location**, **Always beside time** or **Always below time**.
- **Show seconds:** **Never**, **Only in the tooltip** (the seconds appear only when you hover over the clock) or **Always**.
- **Show time zone:** **Only when different from local time zone** or **Always**.
- **Display time zone as:** **Code**, **City** or **Offset from UTC time**. **Switch Time Zone…** opens the [Date & Time](../settings/date-time.md) module, where you change the time zone of the whole system.
- **Time display:** **12-Hour**, **Use region defaults** or **24-Hour**. **Change Regional Settings…** opens the [Region & Language](../settings/region-language.md) module, which sets the region defaults.
- **Date format:** **Long date**, **Short date**, **ISO date** (year-month-day) or **Custom**. With **Custom**, type your own format; the **Time Format Documentation** link explains the codes you can use. A preview shows today's date in the chosen format.
- **Text display:** **Automatic** follows the system font and makes the text fill the space the clock has. **Manual** lets you pick a font and size with **Choose Style…**. The size may be reduced if the panel isn't thick enough.

### Calendar

This tab sets up the calendar that pops up when you click the clock.

- **General:** **Show week numbers** adds the week numbers to the calendar.
- **First day of week:** Picks the day the weeks start on, or **Use region defaults**.
- **Available Add-Ons:** Check an add-on to show more information in the calendar. Each add-on you turn on gets its own tab in the settings. SonicDE comes with these:
  - **Holidays:** Check the regions whose public holidays you want to see. A search field at the top helps you find a region.
  - **Astronomical Events:** Under **Show:**, choose **Lunar phases**, **Astronomical seasons (solstices and equinoxes)**, or both.
  - **Alternate Calendar:** **Calendar system:** shows each day's date in a second calendar as well, for example the Chinese Lunar Calendar, the Hebrew Calendar, the Indian National Calendar, an Islamic calendar or the Julian calendar. For the Islamic calendars, **Date offset:** moves the date up to 10 days earlier or later, to match local observation.

### Time Zones

The clock always knows the time zone of your system, listed under **Systemwide Time Zone**. You can add more under **Additional Time Zones**: their times are then shown in the clock's pop-up as well.

- **Add Time Zone…** opens the **Choose Time Zone** page. Pick a time zone and click **Add Selected Time Zone**, or **Cancel** to go back.
- **Switch Systemwide Time Zone…**, on the system's own entry, opens the [Date & Time](../settings/date-time.md) module.
- The remove button on an added time zone (**Remove this time zone**) takes it out of the list again.
- Select an entry to make the clock in the panel show that time zone. The entry then reads "Clock is currently using this time zone".
- **Switch displayed time zone by scrolling over clock applet** lets you go through the listed time zones by scrolling the mouse wheel over the clock. This doesn't change the time zone of the system; when you travel, change the systemwide time zone instead.

A tip in the settings suggests adding your home time zone: you then see the time at home while you travel, and it isn't shown twice while you're at home.
