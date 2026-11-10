---
title: Window Rules
description: Change the settings of specific windows and applications.
source_url: https://invent.kde.org/plasma/kwin-x11/-/blob/master/doc/windowspecific-x11/index.docbook
source_authors: [Lauri Watts, KDE UserBase contributors]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-win a4e76b52c5 (src/kcms/rules); read from code, not clicked through"
---

# Window Rules

Window rules let you set an application's window attributes. For example, when an application starts it can be forced to always run on virtual desktop 2, or a defect in an application can be worked around by forcing its window above others.

Many of these settings are the ones you can set for all windows in [Window Behavior](window-behavior.md), but some are more detailed. They include geometry, placement, whether a window is kept above or below others, focus stealing prevention and translucency. They only apply if you use SonicWin, the desktop's window manager.

## The rule list

You can open this module from System Settings, or by right-clicking a window's titlebar and choosing **More Actions** then **Configure Special Window Settings…** or **Configure Special Application Settings…**, which fills in the window's details for you.

The main page lists your rules:

- **Add New…** creates a rule. Each rule in the list has buttons to **Edit**, **Duplicate** and **Delete** it.
- **Import…** and **Export…** share rules with others as `.kwinrule` files. Choose which rules to export.
- Drag rules to set the order they're evaluated in.

![Ordering the rules](images/window-rules/kwin-rules-ordering.png)

### Rule evaluation

When an application starts, or the rules change, they're evaluated from the top of the list to the bottom. For all rules that match a window, the combined set of attributes is applied before the window is displayed.

If two or more matching rules set the same attribute, the setting in the *first* rule in the list is used.

> [!TIP]
> You can treat an application's child windows differently by putting the more restrictive rules first. See the [example with a child window](#an-application-on-all-desktops-with-one-different-child-window).

## Editing a rule

Each rule has a **Description**, which is shown in the list, its window matching criteria, and any properties you've added. Click **Add Property...** to choose which ones to change.

![The rule editor](images/window-rules/kwin-rule-editor.png)

### Window matching

![Window matching](images/window-rules/kwin-window-matching.png)

These criteria decide whether the rule applies to a window. You can specify any number of them, and none matches any window.

- **Window class (application):** Matches the class. **Match whole window class** also includes the secondary class.
- **Window types:** Restricts the match to types such as Normal window and Dialog window.
- **Window role:** Restricts the match to the window's function, such as a main window or chat window.
- **Window title:** Restricts the match to the window's title.
- **Machine (hostname):** Restricts the match to the host associated with the window.

For each field you can choose how it's compared:

- **Unimportant:** Ignores the field.
- **Exact match** and **Substring match:** Both ignore case. For example, *AB* matches *AB*, *ab*, *Ab* and *aB*.
- **Regular expression:** Uses [Qt's regular expressions](https://doc.qt.io/qt-6/qregularexpression.html).

### Detect Window Properties

You can enter this information by hand, but it's better to use **Detect Window Properties**.

1. Start the application you want to create a rule for.
2. Choose a delay with the button's menu: **Instantly**, or after a number of seconds.
3. Click **Detect Window Properties**.
4. When the pointer turns into crosshairs, click inside the application's window, not on its titlebar.
5. A list shows information about the window. Select what you want to use, and it's filled in as matching criteria or property values.

![Detect Window Properties](images/window-rules/kwin-detect-window.png)

Using a combination of this, a rule can apply to a whole application, by class, or to a specific type of window within it, such as a toolbar.

## Window properties

![Window properties](images/window-rules/kwin-window-attributes.png)

Each property has a setting that determines how it's applied. It accepts at least one of these:

- **Do not affect:** Makes sure a later matching rule doesn't affect the property.
- **Apply initially:** Starts the window with the property, and lets it change while running.
- **Remember:** Uses the rule's value, and if it changes while running, saves and uses the new value instead.
- **Force:** The setting can't be changed while running.
- **Apply now** and **Force temporarily:** Apply the setting once and then unset it. **Apply now** lets it change while running, and **Force temporarily** stops it being changed until all affected windows close.

> [!WARNING]
> With Apply now, if the rule has no other properties set, it's deleted after evaluation. With Force temporarily, it's deleted after the last affected window closes.

Yes/No settings turn a property on or off. It can help to read them literally: Skip taskbar set to No means don't skip the taskbar, so the window is shown there.

### Size & Position

- **Position:** Puts the window's upper left corner at the given coordinates. The origin, (0,0), is the upper left of the desktop.
- **Size:** The window's width and height.
- **Maximized horizontally** and **Maximized vertically:** Turn each kind of maximizing on or off. Use both, or Initial placement set to Maximized, for full maximizing.
- **Virtual desktop**, **Activities** and **Screen:** Put the window on the given desktop, activity or screen. **All desktops** puts it on all of them.
- **Fullscreen**, **Minimized** and **Shaded:** Turn these on or off. For example, a window can be started minimized.
- **Initial placement:** Overrides the global placement policy with **Default**, **No placement** (top-left corner), **Minimal overlapping**, **Maximized**, **Centered**, **Random**, **In top-left corner**, **Under mouse** or **On main window**, which keeps a child window within its parent.
- **Ignore requested geometry:** Whether to ignore the position the window asks for. Some applications set their own geometry after starting.
- **Minimum Size** and **Maximum Size:** The smallest and largest sizes allowed.
- **Obey geometry restrictions:** Some applications, like video players and terminals, ask to be constrained to certain aspect ratios or to grow by steps larger than one pixel. This sets whether to follow those requests.

### Arrangement & Access

- **Keep above other windows** and **Keep below other windows.**
- **Skip taskbar:** Whether the window appears in the task manager.
- **Skip pager:** Whether it appears in the Pager widget.
- **Skip switcher:** Whether it appears in the Alt+Tab list.
- **Shortcut:** Assigns a shortcut to the window.

![The Pager widget with four desktops](images/window-rules/pager-4-desktops.png)

### Appearance & Fixes

- **No titlebar and frame.**
- **Titlebar color scheme:** A color scheme for the window's titlebar.
- **Active opacity** and **Inactive opacity:** The window's opacity as a percentage when active or inactive. These need desktop effects, and readability may suffer at very low values.
- **Focus stealing prevention:** How to handle a window that wants focus, from **None**, which always grants it, through **Low**, **Normal** and **High**, to **Extreme**, which only grants it when you ask for it explicitly.
- **Focus protection:** Controls how well the window is protected from having focus taken from it, at the same levels.
- **Accept focus:** Whether the window becomes focused when clicked.
- **Ignore global shortcuts:** Stops global shortcuts, as set in [Shortcuts](shortcuts.md), from working while the window is active.
- **Closeable:** Whether the window can be closed from its titlebar. A terminal may still be closed by ending its shell.
- **Desktop file name:** The application's desktop file, used for things like its icon.
- **Block compositing:** Turns off compositing while *any* matching window exists. It comes back on when the last one closes.
- **Layer:** Forces the window into a stacking layer, which decides what it can cover and what covers it. From bottom to top: **Desktop**, **Below**, **Normal**, **Above**, **Notification**, **Fullscreen**, **Popup**, **Critical notification**, **On-screen display** and **Overlay**.
- **Adaptive sync** and **Allow tearing**, where they're supported.

## Examples

The first example gives all the steps. Later ones only give the parts specific to them. The screenshots are from an older version of the module, using Akregator, Kopete, KNotes, Thunderbird and Emacs as the applications.

### Pin a window to a desktop and set other properties

Pin an application to virtual desktop 2 and start it with a preferred size and position. Each property uses **Apply initially** so it can be changed while running.

1. Start the application on desktop 2, and size and position it to suit.

   ![The application on desktop 2](images/window-rules/akregator-fav.png)

2. Right-click the titlebar and open the window rules from **More Actions**, or click **Add New…** in the module.

   ![Opening the window rules](images/window-rules/config-win-behavior.png)

   ![The rule list](images/window-rules/kwin-rules-main.png)

   ![A new rule](images/window-rules/window-matching-init.png)

3. Click **Detect Window Properties**, then click inside the window. Match only by the primary class name, so leave the extra options unchecked.

   ![The detected window properties](images/window-rules/akgregator-info.png)

4. Enter a meaningful **Description**, which is shown in the rule list.

   ![The matching criteria with a description](images/window-rules/window-matching-ready-akregator.png)

5. Add the properties **Position**, **Size** and **Virtual desktop**. Their initial values come from Detect Window Properties and can be changed.

   ![The window properties](images/window-rules/akregator-attributes.png)

6. Apply your changes.

   ![The new rule in the list](images/window-rules/kwin-rules-main-n-akregator.png)

### An application on all desktops, with one different child window

Show a chat application and its child windows on all desktops and skip the taskbar and pager, except that conversation windows do show in the taskbar. Each property uses **Force**.

This needs two rules, and because of [rule evaluation](#rule-evaluation) the conversation window's rule must come first, since its matching is more restrictive:

1. **The conversation window:** Detect the window, and select its window role to restrict the rule to conversation windows. Add **Virtual desktop** set to All desktops, **Skip taskbar** set to No, and **Skip pager** set to Yes.

   ![The conversation window's properties](images/window-rules/kopete-chat-info.png)

   ![The conversation rule's matching criteria](images/window-rules/window-matching-kopete-chat.png)

   ![The conversation rule's properties](images/window-rules/kopete-chat-attribute.png)

2. **The application:** Detect the main window and match only by primary class name. Add **Virtual desktop** set to All desktops, and **Skip taskbar** and **Skip pager** set to Yes.

   ![The main window's properties](images/window-rules/kopete-info.png)

   ![The application rule's matching criteria](images/window-rules/window-matching-kopete.png)

   ![The application rule's properties](images/window-rules/kopete-attribute-1.png)

   ![More of the application rule's properties](images/window-rules/kopete-attribute-2.png)

![The conversation rule listed before the application rule](images/window-rules/kwin-kopete-rules.png)

### Hide a window from the Pager

If an application's windows don't offer this themselves, detect one, match by primary class name, and add **Skip pager** with **Force**.

![The detected window properties](images/window-rules/knotes-info.png)

![The matching criteria](images/window-rules/window-matching-knotes.png)

![The Skip pager property](images/window-rules/knotes-attribute.png)

### Force a window to the top

To bring an active window to the top, set its **Focus stealing prevention** to None, usually with **Force**.

![Focus stealing prevention set to None](images/window-rules/focus-stealing-pop2top-attribute.png)

### Several rules for one application

An email application can have several kinds of window. Rules with enough matching criteria don't depend on their order:

- **Main window:** Detect it and select the window role. Add **Virtual desktop**, **Position** and **Size** to pin it.

  ![The main window's properties](images/window-rules/tbird-main-info.png)

  ![The main window rule's matching criteria](images/window-rules/window-matching-tbird-main.png)

  ![The main window rule's properties](images/window-rules/tbird-main-attribute.png)

- **Composer:** Detect it and select the window role and type. Add **Focus stealing prevention** set to None and **Keep above other windows**, so it comes to the top when activated.

  ![The composer's properties](images/window-rules/tbird-compose-info.png)

  ![The composer rule's matching criteria](images/window-rules/window-matching-tbird-compose.png)

  ![The composer rule's properties](images/window-rules/tbird-compose-attribute.png)

- **Reminder:** Detect it and select the secondary class and window type. Add **Keep above other windows** and **Focus stealing prevention** set to Extreme, so it comes to the top without taking focus and isn't dismissed by accident.

  ![The reminder's properties](images/window-rules/tbird-reminder-info.png)

  ![The reminder rule's matching criteria](images/window-rules/window-matching-tbird-reminder.png)

  ![The reminder rule's properties](images/window-rules/tbird-reminder-attribute-1.png)

  ![More of the reminder rule's properties](images/window-rules/tbird-reminder-attribute-2.png)

## Application workarounds

### Full-screen resize error

Some editors, such as Emacs and gVim, can have window resizing problems when maximized. A rule works around it: detect the window, match by primary class name, then add **Obey geometry restrictions** set to No with **Force**.

![The detected window properties](images/window-rules/emacs-info.png)

![The matching criteria](images/window-rules/window-matching-emacs.png)

![Obey geometry restrictions set to No](images/window-rules/emacs-attribute.png)
