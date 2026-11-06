---
title: What makes a SonicDE application?
description: The philosophy, target users and technologies behind SonicDE applications.
source_url: https://develop.kde.org/hig/kde_app_design/
source_authors: [Joshua Goins, Nate Graham]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-ecco (QtWidgets), sonic-frameworks-quick-ui (Kirigami), Qt 6.11 documentation"
---

# What makes a SonicDE application?

## Philosophy and target user groups

- **Guided common workflows:** SonicDE applications endeavor to offer a good user experience for casual users. Make the application's 80% common use case simple and obvious, with guidance and feedback appropriate for non-experts.
- **Customization supports diversity:** SonicDE applications can be customized with the primary goal of allowing people with diverse workflows and functional preferences to use them. A secondary goal is satisfying people with diverse and subjective aesthetic preferences.
- **Not afraid to grow:** SonicDE applications don't limit themselves to being small and single-purpose. Within the scope of their design domain, they are comfortable appealing to ever-growing numbers of experts by evolving over time to offer powerful features and user-directed extensibility.

Together these characteristics embody the central principle: **Simple by default, powerful when needed**. The target user group of a SonicDE application therefore stretches from people with basic technical knowledge all the way to experts and professionals.

Users can be expected to be familiar with common user interface design patterns (windows, buttons, menus, list views and tab views, etc.) and able to perform tasks such as searching for data that isn't immediately visible, or writing an email reply to multiple people. Users below this skill level are generally de-prioritized. Don't be afraid to pick your users.

## Development technologies

SonicDE applications are built with [Qt](https://www.qt.io/) and SonicDE's frameworks, plus one of Qt's graphical user interface (GUI) toolkits:

- [QtWidgets](https://doc.qt.io/qt-6/qtwidgets-index.html) is the original way of writing GUI applications with Qt. It is best suited for traditional desktop applications with complex interfaces, such as the Ecco file manager.
- [QtQuick](https://doc.qt.io/qt-6/qmlapplications.html) with [Kirigami](../kirigami/setup-cpp.md) feature hardware-accelerated rendering, [declarative](https://en.wikipedia.org/wiki/Declarative_programming) UI design, and better support for animations, touch, and gestures. Kirigami is a convergent UI toolkit that extends QtQuick with higher-level controls that conform to these guidelines and adapt to the device's form factor.

Use QtQuick with Kirigami when writing a new application. GUI code examples throughout these guidelines primarily use QtQuick and Kirigami components, but the general principles extend to applications using either technology.
