---
title: "Kirigami Addons Onboarding QML Types"
description: "Provides guided onboarding walkthroughs for Kirigami applications."
---

# Kirigami Addons Onboarding QML Types

Provides guided onboarding walkthroughs for Kirigami applications.

The onboarding module highlights controls in an application-provided source area, dims and blurs the rest of that area, and displays guidance in a tooltip. Applications describe walkthroughs with [Onboarding](qml-org-kde-kirigamiaddons-onboarding-onboarding.md) attached properties; the module creates and manages the overlay.

To use the module, import it in each QML file that declares a source, defines a step, or controls a walkthrough:

```qml
import org.kde.kirigamiaddons.onboarding
```

## Defining a Walkthrough {#defining-a-walkthrough}

A walkthrough consists of one source item and one or more descendant step items. Mark the common ancestor with [Onboarding::isSource](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#isSource-attached-prop) and provide guidance on each step with [Onboarding::texts](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#texts-attached-prop) or [Onboarding::additionalData](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#additionalData-attached-prop).

```qml
Item {
    Onboarding.isSource: true

    Button {
        text: i18nc("@action:button", "Create")
        Onboarding.texts: [
            i18nc("@info", "Create a new document with this button.")
        ]
    }

    Button {
        text: i18nc("@action:button", "Start Tutorial")
        onClicked: Onboarding.start()
    }
}
```

Steps are visited in attached-object creation order. Disabled steps are skipped. The source and all of its step items must remain instantiated for the duration of the walkthrough.

## Defining Groups {#defining-groups}

Groups allow an application to define multiple walkthroughs over the same source area. The empty string identifies the default group used by [Onboarding::start](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#start-method)(). A source lists the groups it owns in [Onboarding::sourceGroups](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#sourceGroups-attached-prop). Each step lists its groups in [Onboarding::groups](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#groups-attached-prop), with corresponding guidance at the same positions in [Onboarding::texts](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#texts-attached-prop).

```qml
Item {
    Onboarding.isSource: true
    Onboarding.sourceGroups: ["", "advanced"]

    Button {
        Onboarding.groups: ["", "advanced"]
        Onboarding.texts: [
            i18nc("@info", "Basic guidance for this control."),
            i18nc("@info", "Advanced guidance for this control.")
        ]
    }
}
```

A group must be declared by exactly one source item. Calling [Onboarding::start](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#start-method-1)(string) for a missing or ambiguous group does not start a walkthrough and produces a warning.

## Navigation and Lifecycle {#navigation-and-lifecycle}

The default overlay provides Previous, Next, and Cancel buttons. The Left and Right arrow keys navigate between enabled steps, and Escape stops the walkthrough. Applications can also call [Onboarding::next](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#next-method)(), [Onboarding::previous](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#previous-method)(), and [Onboarding::stop](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#stop-method)().

Use [Onboarding::aboutToShow](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#aboutToShow-signal) on a step when its target must first be made visible, for example by changing a page in a [SwipeView](https://doc.qt.io/qt-6/qml-qtquick-controls-swipeview.html). The target is resolved on the next event-loop turn after the signal is emitted. [Onboarding::hide](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#hide-signal) is emitted when the step ceases to be current.

## Custom Content and Appearance {#custom-content-and-appearance}

[Onboarding::additionalData](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#additionalData-attached-prop) stores application-defined metadata on each step. Set [Onboarding::additionalDataComponent](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#additionalDataComponent-prop) to a component that reads the current step's metadata through `Onboarding.currentItem.additionalData`. The component is inserted between the guidance text and the navigation controls.

The highlight can be expanded with [Onboarding::padding](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#padding-prop). The background effect can be adjusted with [Onboarding::blur](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#blur-prop) and [Onboarding::blurMax](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#blurMax-prop). The module clamps highlight padding so the highlighted rectangle remains inside the source area.

## Contents

- [OnboardToolTip](qml-org-kde-kirigamiaddons-onboarding-onboardtooltip.md): Persistent tooltip styled for onboarding walkthroughs.
- [Onboarding](qml-org-kde-kirigamiaddons-onboarding-onboarding.md): Describes and controls guided onboarding walkthroughs.
