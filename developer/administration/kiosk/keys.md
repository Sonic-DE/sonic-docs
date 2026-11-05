---
title: Kiosk keys
description: The keys that can be used with Kiosk and what they do.
source_url: https://develop.kde.org/docs/administration/kiosk/keys/
source_authors: [Blagovest Petrov, Carl Schwan, Harald Sitter, Kristen McWilliam, Nicolas Fella, Thiago Sueto, Yvan Masson, shenleban tongying]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "every key compared with KAuthorized calls and action names across SonicDE's repositories: the standard action table, sonic-terminal's action collection, kauthorized.h and the authorize calls. Keys not found in the code were removed. Whether the prefix is needed was read from each call. Only some were run: see the introduction page."
---

# Kiosk keys

This page lists keys that can be used with Kiosk and what they do. The [introduction](introduction.md) explains how to use them, along with URL restrictions and more.

Which file to put them in depends on whether they should apply to all applications or one. For all applications, put them in `kdeglobals`. For one application, put them in its own configuration file, such as `konsolerc` for the terminal.

## Application action restrictions

These disable actions commonly found in applications. In `kdeglobals`:

```ini
[KDE Action Restrictions][$i]
action/<key>=false
```

| Menu | Key | Action |
| --- | --- | --- |
| File | `action/file_new` | New |
| File | `action/file_open` | Open |
| File | `action/file_open_recent` | Open Recent File |
| File | `action/file_save` | Save |
| File | `action/file_save_as` | Save As |
| File | `action/file_revert` | Revert |
| File | `action/file_close` | Close |
| File | `action/file_print` | Print |
| File | `action/file_print_preview` | Print Preview |
| File | `action/file_mail` | Email File |
| File | `action/file_quit` | Quit |
| Edit | `action/edit_undo` | Undo |
| Edit | `action/edit_redo` | Redo |
| Edit | `action/edit_cut` | Cut |
| Edit | `action/edit_copy` | Copy |
| Edit | `action/edit_paste` | Paste |
| Edit | `action/edit_clear` | Clear |
| Edit | `action/edit_select_all` | Select All |
| Edit | `action/edit_deselect` | Deselect |
| Edit | `action/edit_find` | Find |
| Edit | `action/edit_find_next` | Find Next |
| Edit | `action/edit_find_prev` | Find Previous |
| Edit | `action/edit_replace` | Replace |
| View | `action/view_actual_size` | 100% Zoom |
| View | `action/view_fit_to_page` | Fit To Page |
| View | `action/view_fit_to_width` | Fit To Width |
| View | `action/view_fit_to_height` | Fit To Height |
| View | `action/view_zoom_in` | Zoom In |
| View | `action/view_zoom_out` | Zoom Out |
| View | `action/view_zoom` | Zoom |
| View | `action/view_redisplay` | Refresh |
| Go | `action/go_up` | Up |
| Go | `action/go_back` | Back |
| Go | `action/go_forward` | Forward |
| Go | `action/go_home` | Home |
| Go | `action/go_previous` | Previous |
| Go | `action/go_next` | Next |
| Go | `action/go_goto` | Go To |
| Go | `action/go_goto_page` | Go To Page |
| Go | `action/go_goto_line` | Go To Line |
| Go | `action/go_first` | Go To Start |
| Go | `action/go_last` | Go To End |
| Bookmarks | `action/bookmarks` | The bookmarks menu |
| Bookmarks | `action/bookmark_add` | Add Bookmark |
| Bookmarks | `action/bookmark_edit` | Edit Bookmarks |
| Tools | `action/tools_spelling` | Check Spelling |
| Settings | `action/options_show_menubar` | Show or hide the menu bar |
| Settings | `action/options_show_toolbar` | Show or hide the toolbar, and the "Toolbars" submenu if present |
| Settings | `action/options_show_statusbar` | Show or hide the status bar |
| Settings | `action/options_configure` | Configure the application |
| Settings | `action/options_configure_keybinding` | Configure Shortcuts |
| Settings | `action/options_configure_toolbars` | Configure Toolbars |
| Settings | `action/options_configure_notifications` | Configure Notifications |
| Settings | `action/fullscreen` | Full screen mode |
| Settings | `action/switch_application_language` | Switch the application's language |
| Help | `action/help_contents` | The application's handbook |
| Help | `action/help_whats_this` | "What's this" mode |
| Help | `action/help_report_bug` | Report a bug |
| Help | `action/help_donate` | Donate |
| Help | `action/help_about_app` | About the application |
| Help | `action/help_about_kde` | About the desktop |

## File manager

| Key | Action |
| --- | --- |
| `action/editfiletype` | Edit associated applications |
| `action/properties` | File properties |
| `action/openwith` | Open a file with another application |
| `action/kdesktop_rmb` | The desktop's context menu |

## Terminal

These are actions of the terminal. They can go in `kdeglobals` or `konsolerc`. An application's actions are named in its source, so this is a selection:

| Key | Action |
| --- | --- |
| `action/new-tab` | Create a new tab |
| `action/new-window` | Create a new window |
| `action/clone-tab` | Clone the current tab |
| `action/close-session` | Close the current session |
| `action/rename-session` | Rename the current session |
| `action/detach-tab` | Detach the current tab |
| `action/next-tab` | Go to the next tab |
| `action/previous-tab` | Go to the previous tab |
| `action/move-tab-to-left` | Move the tab to the left |
| `action/move-tab-to-right` | Move the tab to the right |
| `action/split-view` | Split the view |
| `action/clear-history` | Clear the scrollback |
| `action/clear-history-and-reset` | Clear the scrollback and reset |
| `action/adjust-history` | Configure the scrollback |
| `action/enlarge-font` | Increase the font size |
| `action/shrink-font` | Decrease the font size |
| `action/reset-font-size` | Reset the font size |
| `action/manage-profiles` | Manage profiles |
| `action/edit-current-profile` | Edit the current profile |
| `action/monitor-activity` | Monitor for activity |
| `action/monitor-silence` | Monitor for silence |
| `action/set-encoding` | Set the encoding |
| `action/save-layout` | Save the tab layout |
| `action/load-layout` | Load a tab layout |

## SonicWin

| Key | Action |
| --- | --- |
| `action/kwin_rmb` | Context menus on window titlebars and frames |

## Desktop shell

Locking the entire desktop configuration file with `[$i]` makes everything immutable. Locking a containment's group makes that group of widgets immutable, and locking a widget means it can't be moved, as well as being otherwise locked.

These restrictions are also available:

| Key | Action |
| --- | --- |
| `plasma/allow_configure_when_locked` | Whether widgets and containments can be configured when locked. The default is true, as a convenience to users. |
| `plasma/containment_actions` | Whether mouse actions are allowed on the desktop and panels, most notably context menus. The code checks this with and without the `action/` prefix, so set both. |
| `plasma/plasmashell/unlockedDesktop` | Whether widgets can be unlocked. If false, widgets can't be unlocked, favorites and applications in the launchers can't be changed, and launchers in the task manager can't be added or removed. |
| `plasma-desktop/scripting_console` | Whether the desktop scripting console is accessible. |
| `plasma-desktop/add_activities` | Whether the user can add activities. |

### Downloading add-ons

SonicDE offers to download widgets, wallpapers, scripts and other third-party add-ons from the KDE Store. To disable this:

| Key | Action |
| --- | --- |
| `ghns` | Whether the download dialog can be opened |

## Authorizing

An application's `.desktop` file can have an additional field, `X-KDE-AuthorizeAction`. The file is then valid only if the actions in this field are authorized. Separate several actions with commas.

If a user doesn't have authorization for even one of the listed actions, the application doesn't appear in the menu, can't be run through that `.desktop` file, and isn't used to open files of the types it is associated with.

## Session capability restrictions

These apply to the desktop session and aren't specific to an application. In `kdeglobals`:

```ini
[KDE Action Restrictions][$i]
<key>=false
```

| Key | Action |
| --- | --- |
| `editable_desktop_icons` | Whether icons on the desktop can be moved around. To prevent adding, removing or renaming icons, make the desktop folder read-only. |
| `lineedit_text_completion` | Whether input lines can remember what was entered and make suggestions. If several people share an account, you might disable this for privacy. |
| `lineedit_reveal_password` | Whether password fields can have a button that shows the password in plain text. |
| `action/lock_screen` | Whether the user can lock the screen. |
| `logout`, `action/logout` | Whether the user can log out. Set both. |
| `movable_toolbars` | Whether the user can move toolbars. See also `action/options_show_toolbar`. |
| `run_command`, `action/run_command` | Whether KRunner is available, and its entry in the desktop's context menu. Set both. |
| `run_desktop_files` | Whether users can run `.desktop` files that aren't part of the desktop, the application menu, registered services or autostarting services. |
| `shell_access` | Whether a shell can be started for entering commands. This also decides whether KRunner can run shell commands and arbitrary executables, and whether a command can be typed into the "Open With" dialog. See also `run_desktop_files`. |
| `action/start_new_session` | Whether the user can start a new session. |
| `action/switch_user` | Whether the user can switch users. |

## Telemetry

Telemetry is off by default, but a user can choose to enable it in applications. To disable it globally, set this in `/etc/xdg/KDE/UserFeedback.conf`:

```ini
[UserFeedback]
Enabled=false
```
