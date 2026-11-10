---
title: More widgets
description: The smaller widgets that come with SonicDE, from Sticky Note and Timer to Media Frame, Dictionary and the Fifteen Puzzle.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace-addons (applets/calculator, comic, dict, diskquota, fifteenPuzzle, grouping, katesessions, keyboardindicator, konsoleprofiles, mediaframe, notes, quicklaunch, timer, userswitcher, webbrowser, profiles/); written from the code, not clicked through"
---

# More widgets

SonicDE comes with a set of smaller widgets for the desktop and panels. To add one, right-click the desktop or a panel, choose **Enter Edit Mode**, open **Add Widgets…** and drag it into place. To change a widget's settings, right-click it and choose **Configure** followed by the widget's name.

The larger widgets have pages of their own: see [Widgets](widgets.md), [Clocks](clocks.md), [Color Picker](color-picker.md) and [Application Dashboard](application-dashboard.md).

## Calculator

A small calculator for simple sums, with the usual number keys, **+**, **-**, **×**, **÷** and **=**. **C** clears the current entry and **AC** clears everything. Dividing by zero shows **undef**. It has no settings.

## Comic Strip

Shows comic strips from the Internet, with buttons to go to the previous and next strip. Until you choose a comic it says **No comics configured** and offers **Choose comic…**.

The right-click menu has **Next Tab with a New Strip**, **Jump to First Strip**, **Jump to Current Strip**, **Jump to Strip…**, **Visit the Website**, **Visit the Shop Website** (when the comic has one), **Save Comic As…**, **Actual Size** and **Store Current Position**.

Its settings have two pages:

- **Comics:** Choose which comics to show. Each one you choose gets its own tab. **Get New…** downloads more comic sources; when none are installed, the page says **No comics installed** and offers **Get Comics…**. **Check for new comics every:** sets how often, in minutes, the widget looks for new strips. **Keep local archive:** sets how many images per comic are kept on your computer.
- **Behavior:** **Show above image:** adds the **Title** and **Author**. **Show below image:** adds the **Identifier** and the **Website**. **Navigation buttons:** are either **Always visible at the edges** or **Appear centrally when hovering**. **Middle-clicking image:** **Opens full-size view** when checked.

## Dictionary

Looks up the meaning of words. Type a word into **Enter word to define here…** and the definition appears below. On the **Dictionaries** page of its settings, **Add More…** chooses which dictionaries the widget asks; the page lists the ones in use.

The Dictionary widget is only there if Qt WebEngine was installed when SonicDE was built.

## Disk Quota

Shows how much of your disk quota you're using, on systems that limit how much each user can store. If there are no limits for you, it says **No quota restrictions found**. It needs the `quota` tool: without it, the widget says **Quota tool not found** and **Please install 'quota'**. It has no settings.

## Fifteen Puzzle

The classic sliding puzzle: click tiles next to the gap to slide them until they're in order. **Shuffle** starts a new game, and the widget counts your moves and the time. When you're done it says **Solved! Try again.**

On the **Appearance** page of its settings:

- **Grid size:** How many tiles per side, from 2 to 99. The default is 4.
- **Background:** Either a **Color:** or an **Image:**, chosen with **Choose image…**. With an image, each tile shows its part of the picture.
- **Tile labels:** The **Color:** of the numbers, and **Hide on image backgrounds**, which leaves the numbers off when you use an image.

## Grouping Plasmoid

A container for other widgets, so several of them can share one space, each on its own tab. When it's empty it says **Drag applets here**. It has no settings of its own.

## Kate Sessions

Lists your sessions of the Kate text editor and opens one when you click it. **Search…** filters the list, and **Create new session and start Kate** lets you name a new session. It's only useful if Kate is installed; SonicDE doesn't include it.

## Konsole Profiles

Lists your [Terminal](../applications/terminal.md) profiles. Click one to open Terminal with that profile. It has no settings.

## Lock Keys Status

Shows a symbol while Caps Lock or Num Lock is on. On the **Keys** page of its settings, **Show when activated:** chooses **Caps Lock**, **Num Lock** or both. Only **Caps Lock** is checked by default.

## Media Frame

A picture frame for the desktop that shows your pictures one after another. Until you choose some it says **No media selected** and offers **Choose media…**.

Its settings have two pages:

- **Media:** **Add Folder…** and **Add Files…** choose what to show. Each entry has a **Remove path** button.
- **Behavior:** **Change picture every:** sets the time between pictures in **Hours**, **Minutes** and **Seconds**. **Image fill mode:** chooses how a picture fits the frame: **Stretch**, **Preserve aspect fit**, **Preserve aspect crop**, **Tile**, **Tile vertically**, **Tile horizontally** or **Pad** (shown at its own size). Under **General:**, **Randomize order** shuffles the pictures, **Pause slideshow when cursor is over image** stops it while you look, and **Click on image to open in external application** opens the picture in its usual application.

## Quicklaunch

A small grid of application launchers for a panel or the desktop. Drag applications onto it from the application launcher or the file manager, or right-click it and choose **Add Launcher…**. Right-click a launcher for **Edit Launcher…** and **Remove Launcher**.

Its settings:

- **Maximum rows:** (in a horizontal panel) or **Maximum columns:** (in a vertical one): how many rows or columns of launchers fit before it starts a new one.
- **Appearance:** **Show launcher names** writes each launcher's name under its icon. **Enable popup** adds an arrow that opens a popup for extra launchers, so you can keep some out of the way.
- **Title:** Check **Show:** to give the widget a title, and type your own into **Custom title**.

## Sticky Note

A note on your desktop. Type into it, and use the buttons at the bottom for **Bold**, **Italic**, **Underline** and **Strikethrough**. Right-click the text for editing actions such as **Paste with Full Formatting** and **Remove Formatting**. The delete button at the bottom removes the note. If the note has text in it, it asks **Discard this note?** first, so you don't lose a note by accident.

On the **Appearance** page of its settings:

- **Text font size:** From 4 to 128 points.
- The color of the note: white, black, red, orange, yellow, green, blue or pink, **A transparent sticky note**, or, on the desktop only, **A transparent sticky note with light text**.

In a panel, the note opens as a popup, and its **Keep Open** button stops it closing when you click elsewhere.

## Timer

A countdown timer. Scroll over the digits to set the time, or right-click the widget and choose one of your predefined timers. Click **Start Timer** to begin and **Pause Timer** to pause. The right-click menu also has **Start**, **Stop** and **Reset**.

Its settings have two pages:

- **General:** Under **Display:**, **Show title:** with a title of your own, **Show remaining time**, **Show seconds**, **Show timer toggle** (the start and pause button) and **Show progress bar**. Under **On timeout:**, **Show notification:** with your own text, which is **Timer finished** if you leave it empty, and **Run command:**, a command that runs when the time is up.
- **Predefined Timers:** **Add** a timer, then scroll over its digits to set the time and click **Apply**. Each timer has **Edit** and **Delete** buttons. They appear in the widget's right-click menu.

## User Switcher

Shows who is logged in and lets you switch to another user. Its popup lists the current user and the other sessions on this computer, with **New Session**, **Lock Screen** and **Show Logout Screen** at the bottom.

On the **General** page of its settings:

- **Username style:** **Full name (if available)** or **Login username**.
- **Show:** What the panel button shows: **Name**, **User picture**, or **Name and user picture**.
- **Advanced:** **Show technical session information** adds the console or display each session runs on.

## Web Browser

Shows a web page on your desktop or in a panel popup, with **Go Back**, **Go Forward**, **Go Home** and a reload button. Right-click a link for **Open Link in Browser** and **Copy Link Address**. In a panel, **Keep open** stops the popup closing when you click elsewhere.

Its settings have two pages:

- **General:** **On startup:** either **Load last-visited page** or **Always load this page:** with an address. **Content scaling:** is either a **Fixed scale:** or **Automatic scaling if width is below** a width you choose, which shrinks the page when the widget is narrow. **Browser Settings:** **Private Browsing** keeps no history or cookies.
- **Appearance:** **Icon:** in a panel, either the **Website's favicon** or an icon you choose. **Display Navigation Bar** shows or hides the buttons and address bar.

The Web Browser widget is only there if Qt WebEngine was installed when SonicDE was built.
