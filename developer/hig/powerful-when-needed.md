---
title: Powerful when needed
description: Settings, accelerators and extensibility for demanding users.
source_url: https://develop.kde.org/hig/powerful_when_needed/
source_authors: [Nate Graham, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace kcms/colors (accent color, Edit Color Scheme), API reference for Kirigami, KConfigGui and KNewStuff, ProvidersUrl in shipped .knsrc files"
---

# Powerful when needed

While SonicDE applications can certainly be simple and opinionated, they aren't afraid of providing power-user functionality when needed, suitable for demanding users, experts, and professionals.

Note that this is not a hard requirement. Remember “when needed.”

## Customization increases reach

The primary purpose of configurable settings is to make the software more usable for different types of users with well-developed workflow preferences. These users can have strong voices, or be potential future contributors to your application!

The best settings support diversity of usage by allowing the user to switch between multiple supported and valid behaviors or workflows according to their preferences and hardware. Settings to simply enable or disable a feature entirely are warning signs of sloppy design.

Visual customization is of secondary importance, so don't impair the default user experience in pursuit of it. As much as possible, defer to the platform's own visual styling conventions and theming tools. This allows users with strong aesthetic preferences to do theming at the system level, and their applications will all respond accordingly.

Don't use customizability to avoid making design decisions, work around your own bugs, or just because customization is possible. The more settings your application presents, the more frustrated users will become when it doesn't have exactly the one they're looking for.

Don't use customizability to override platform settings or styling, with one exception: when the application is used on a platform lacking a global setting that SonicDE has, it can be exposed as an application-specific setting.

Use [Kirigami.FormLayout](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formlayout) to build your configuration pages.

Apply newly-saved settings immediately; don't require re-launching the application.

## Accelerators for experts

Expert users love to streamline their tasks with keyboard shortcuts and context menus, so make sure to implement them! Remember that these are *accelerators*; never rely exclusively on keyboard shortcuts or context menus to access functionality. Primary workflows and their controls must be visible by default.

Either assign a keyboard shortcut to every action that can be performed, or at least make shortcuts assignable by the user. For standard actions, use the shortcuts provided by [KStandardShortcut](/docs/api/kconfiggui/kstandardshortcut).

For both touchpads and touchscreens, only implement two-finger gestures in your application. Three- and four-finger gestures can conflict with gestures provided by the system.

Don't use the `Meta` key for application-specific shortcuts; this is reserved for global shortcuts.

## User-driven extensibility

The best applications are modular, with extra functionality provided through plugins. This allows users to self-satisfy rather than asking the developers for new features.

SonicDE's frameworks include the [KNewStuff](/docs/api/knewstuffcore/knewstuff-index) system for getting and managing user-provided third-party content from the [KDE Store](https://store.kde.org) or any other [Open Collaboration Services](https://en.wikipedia.org/wiki/Open_Collaboration_Services) server. Using KNewStuff, users can download new content and functionality. If you use a custom downloader UI, it is your responsibility to warn users that this content represents a digital Wild West with no assumptions of stability or safety!

> **Warning: explicit “Basic” and “Advanced” settings.** Avoid hiding settings on pages or views named “Advanced”. The distinction between a basic and an advanced setting depends on the user's needs and workflow, and the word “Advanced” communicates nothing about what might be inside.
>
> What works better is a progressive disclosure model where a view first presents data or settings in a simplified form, but optional and non-critical details about each item can be shown on a sub-page, separate window, or a collapsed view. This often achieves a similar effect as having an “Advanced” page, but the contents are clear to the user before they visit it.
>
> For example, System Settings' Colors page has a “basic” accent color feature and a grid view of all the installed color schemes, but each color scheme can be fully edited in a separate window, by clicking its “Edit Color Scheme…” button. This constitutes the “advanced” view.
