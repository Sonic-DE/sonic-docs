---
title: Simple by default
description: Make your application friendly and usable for people using it for the first time.
source_url: https://develop.kde.org/hig/simple_by_default/
source_authors: [John Veness, Joshua Goins, Kunda Ki, Nate Graham, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "API reference for Kirigami, KConfigWidgets, KIO and KWallet; Kirigami Units values printed from the stage build"
---

# Simple by default

Focus on the core experience for new users using the default settings. Future experts begin as novices; don't scare them away before they find your application's powerful features!

Multiple techniques are used to make your application friendlier and more usable for people using it for the first time, or at a basic level of technical skill:

## Be welcoming, not demanding or baffling

Show something actionable when the application is first launched, and guide the user through its initial or primary interaction flow. Don't waste the user's time by requiring them to hunt around for the obvious “next step” or make a decision about something they don't understand yet.

Examples of guided workflows:

- In a content creation application, show a blank canvas if it's obvious how to add content to it. This works well in writing and artistic applications. If the content created in the application is more complex than an untrained user would understand (e.g. circuit design or 3D modeling), prompt the user to go through a tutorial or new content creation wizard so they can get up to speed quickly.
- In a content consumption application, show a placeholder message to open a file, point to a folder full of files, or otherwise get the user's content into the application. If there are no privacy concerns, show a list or grid of recently-accessed content.
- In an application like a chat or email client that's largely a front-end for an online service, show a placeholder message briefly introducing the service and prompting the user to log into their account for it, or create one. Remember the account's credentials using [KWallet](/docs/api/kwallet/kwallet-index) and log the user in automatically on subsequent launches.
- In a utility application, show the UI for the primary function as simply and obviously as possible without making the user configure anything or hunt for the “do it” button.

Use [Kirigami.PlaceholderMessage](/docs/api/kirigami/qml-org-kde-kirigami-placeholdermessage) to display placeholder messages in empty views. Include an icon, explanation text, and ideally a [helpfulAction](/docs/api/kirigami/qml-org-kde-kirigami-placeholdermessage#helpfulAction-prop) button the user can click on to proceed or add content to the view.

For specialized applications or features that are unfamiliar to a normal person, write a sentence or two of text explaining what the application or feature is used for. This message can go in the placeholder content in an otherwise empty view, or at the top of a page that's full of controls.

Only use a first-run wizard in a complex application, for one of the following:

- To perform mandatory and unskippable setup actions that must be done before the application can be used.
- As an optional and skippable teaching tool.

Don't ask the user to express preferences or make decisions about optional settings in a wizard, or implement one for a simple to medium-sized application.

## Optimize common workflows

Don't make the user do unnecessary work to use your application. Anticipate what the user is likely to do next and offer that. For example:

- In cases where the user needs to choose a device to use from a set of many, preselect the last-used device or the one most likely to be useful, instead of asking the user to explicitly choose a device every time before they can proceed. If there is only one available device, skip this step entirely.
- When the user asks to compose a new email, if the clipboard's top item is an email address, pre-populate the “To:” field with that address.
- Allow the user to rename files and folders inline, rather than with a separate modal dialog box.

## Show the most important UI elements

New users will judge your application based on what they can see. Optimize the post-launch experience to guide the user through the primary workflow.

Keep it simple: don't bombard the user with extraneous UI controls that aren't interactive or relevant in their current context, and avoid button overload. Consider the following techniques to reduce visual complexity without reducing functionality:

- Condense related buttons into a single one that opens a menu.
- Group related features or controls and put them on separate pages.
- In Kirigami applications, use [Kirigami.Page.actions](/docs/api/kirigami/qml-org-kde-kirigami-page#actions-prop) and [context drawers](../kirigami/drawers.md), which show only actions contextually relevant to the visible content.
- In QtWidgets applications, use [KHamburgerMenu](/docs/api/kconfigwidgets/khamburgermenu) to provide a curated list of the most important actions.

Determine which functionality is most important to your application and keep it visible by default; don't hide it behind menus, controls that appear on hover, keyboard shortcuts, or gestures. Any actions exclusively available via one of these means must be of low importance, because less experienced users will frequently miss them.

## Optimize launch time and UI responsiveness

Make your application lightning fast or new users will lose interest quickly.

Display a progress indicator for tasks that take longer than a second. If the progress is inherently indeterminate, use a [QtQuick.Controls.BusyIndicator](https://doc.qt.io/qt-6/qml-qtquick-controls-busyindicator.html); otherwise use [Kirigami.LoadingPlaceholder](/docs/api/kirigami/qml-org-kde-kirigami-loadingplaceholder) for progress that is always determinate or can vary between determinate and indeterminate.

Prefer determinate progress indication when an exact count of remaining tasks or time is known. Here technical jargon in the text is acceptable: accurate details can be used for debugging purposes, and also convince the user that the application is still doing something. If an exact count of remaining tasks or time is not known, use the indeterminate variant.

## Be consistent

New users learn software by relying on consistent visual cues from other software: what a button looks like and how it behaves, where menus can be found, what sidebars are used for, and so on. If they use other SonicDE applications, they've developed a general sense of how those applications work. Make use of this knowledge! Other similar well-designed applications are a good precedent to follow.

Avoid custom styling and minimize the use of custom components. Adhere to standards:

- Standard colors that pull from the user's active color scheme with [Kirigami.Theme](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme)
- Standard icon sizes with [Kirigami.Units.iconSizes](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units#iconSizes-prop)
- Standard spacing units with:
  - [Kirigami.Units.smallSpacing](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units#smallSpacing-prop)
  - [Kirigami.Units.mediumSpacing](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units#mediumSpacing-prop)
  - [Kirigami.Units.largeSpacing](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units#largeSpacing-prop)
- Standard durations for animations with:
  - [Kirigami.Units.veryShortDuration](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units#veryShortDuration-prop)
  - [Kirigami.Units.shortDuration](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units#shortDuration-prop)
  - [Kirigami.Units.longDuration](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units#longDuration-prop)
  - [Kirigami.Units.veryLongDuration](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units#veryLongDuration-prop)

## Use sensible defaults

Optimize default settings for new users unfamiliar with the application, and consider what kind of expectations they'll be bringing along so you can cater to them. Seek inspiration from other applications with similar functionality.

Make sure the main window is large enough to show its UI labels and controls with no elision or overflow menus. Don't keep running in the background as a System Tray icon when closed.

Integrating into other desktop environments is a virtue, but don't sacrifice integration or visual fidelity within SonicDE in cases where the two goals conflict irreconcilably.

## Maximize safety

Guide the user towards making good decisions, and either prevent them from making bad ones, or at least warn them of the consequences. Make the user feel like they know where they are and how to get back to safety when they feel confused or overwhelmed.

The easier something is to remove from the application, the easier it should be to get it back. Use menus or sub-pages to hide features that destroy data or difficult-to-restore content so they can't be triggered by a stray click, or else use a confirmation dialog. Move files to the trash, don't delete them immediately.

Offer an undo for every action that removes content not trivial to re-add. For cases requiring immediate deletion, employ a deferred deletion approach by postponing the underlying delete operation until after the user has dismissed the option to undo it.

Make the UI for undo actions dismissable and non-modal so it doesn't annoy the user. [showPassiveNotification](/docs/api/kirigami/qml-org-kde-kirigami-abstractapplicationwindow#showPassiveNotification-method) automatically disappears after a few seconds, and is good for cases where losing the option to undo is not catastrophic. A [Kirigami.InlineMessage](../kirigami/inline-messages.md) does not disappear automatically and is better for truly destructive actions such as deleting files.

Finally, use [standard iconography for destructive actions](icons/index.md#icons-for-destructive-actions).

## Remember history

Always remember the window size and position when your application is re-opened.

In many applications, it also makes sense to remember the active view, set of open files, and scroll positions within documents. For example:

- In large project-based applications where re-creating the project state is time-consuming.
- In file-based applications where the user is likely to continue using the same file over multiple sessions (e.g. a word processor or spreadsheet application).

Don't remember state and open files in small utility applications or applications where the user is likely to open a different file every time they use it, for example video players and PDF document viewers. In such applications, instead show the user a list or grid of recently-opened files generated using [KRecentDocument](/docs/api/kiocore/krecentdocument) so they can quickly return to them if needed. When allowing the user to open files in ways that bypass the standard Open dialog, manually add them to the recent files list using `KRecentDocument`.
