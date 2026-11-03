---
title: "OnboardToolTip QML Type"
description: "Persistent tooltip styled for onboarding walkthroughs."
---

# OnboardToolTip QML Type

Persistent tooltip styled for onboarding walkthroughs. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.onboarding
- Inherits: [ToolTip](https://doc.qt.io/qt-6/qml-qtquick-controls-tooltip.html)

## Detailed Description {#details}

[OnboardToolTip](qml-org-kde-kirigamiaddons-onboarding-onboardtooltip.md) is the tooltip used by the default [Onboarding](qml-org-kde-kirigamiaddons-onboarding-onboarding.md) overlay. It applies the platform tooltip color set, stays open until its owner hides it, sizes itself to its content, and uses Kirigami spacing and corner radius metrics.

The type inherits the standard [ToolTip](https://doc.qt.io/qt-6/qml-qtquick-controls-tooltip.html) API and can be used when custom onboarding visuals need the same appearance and persistent popup behavior as the built-in overlay.
