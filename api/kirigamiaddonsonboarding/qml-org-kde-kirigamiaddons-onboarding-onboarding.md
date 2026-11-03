---
title: "Onboarding QML Type"
description: "Describes and controls guided onboarding walkthroughs."
---

# Onboarding QML Type

Describes and controls guided onboarding walkthroughs. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.onboarding

## Detailed Description {#details}

Onboarding is an uncreatable attached type. Attach it to one item to define the source area and to descendant items to define walkthrough steps. Its controller properties and methods share one walkthrough state, so they can be accessed as `Onboarding.active`, `Onboarding.start()`, and similar expressions from any object in a QML file that imports the module.

A step participates after either [Onboarding::texts](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#texts-attached-prop) or [Onboarding::additionalData](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#additionalData-attached-prop) has been assigned. It must belong to the requested group, be a descendant of that group's source item, and provide either non-empty text for the group or non-empty additional data.

> **Note:** Only one walkthrough is active at a time. Starting another group replaces the current walkthrough without emitting [Onboarding::finished](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#finished-signal).

## Property Documentation {#property-documentation}

### active : bool {#active-prop}

This read-only property is `true` while a walkthrough is active.

The default value is `false`.

### additionalDataComponent : Component {#additionalDataComponent-prop}

This property holds an optional component inserted into the default onboarding tooltip. The component can read metadata from `Onboarding.currentItem.additionalData` and should set `visible` to `false` when it has nothing to display.

The value is shared by all walkthroughs. The default value is `null`.

### blur : real {#blur-prop}

This property holds the blur amount applied outside the highlighted rectangle. It is forwarded to the blur effect's `blur` property.

The value is shared by all walkthroughs. The default value is `0.55`.

### blurMax : int {#blurMax-prop}

This property holds the maximum blur radius used by the background effect. Higher values can improve blur quality at a greater rendering cost.

The value is shared by all walkthroughs. The default value is `64`.

### currentIndex : int {#currentIndex-prop}

This read-only property holds the current step's index in the collected step list. Disabled steps remain in that list and are skipped during navigation, so successive values are not necessarily contiguous.

The value is `-1` when no step is current.

### currentItem : Onboarding {#currentItem-prop}

This read-only property holds the Onboarding attached object for the current target item. It provides access to step-specific properties such as [Onboarding::target](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#target-attached-prop) and [Onboarding::additionalData](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#additionalData-attached-prop).

The value is `null` while no step is current.

### currentText : string {#currentText-prop}

This read-only property holds the current step's text for the active group. The value is empty when no step is current or when the step contributes only [Onboarding::additionalData](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#additionalData-attached-prop).

### hasNextItem : bool {#hasNextItem-prop}

This read-only property is `true` when an enabled step exists after the current index in the collected step list. The default overlay uses it while [Onboarding::active](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#active-prop) to decide whether to show its Next button.

The collected list remains available after [Onboarding::stop](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#stop-method)(), so use [Onboarding::active](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#active-prop) rather than this property to determine whether a walkthrough is running.

### hasPreviousItem : bool {#hasPreviousItem-prop}

This read-only property is `true` when an enabled step exists before the current index in the collected step list. The default overlay uses it while [Onboarding::active](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#active-prop) to decide whether to show its Previous button.

### height : real {#height-prop}

This read-only property holds the highlighted rectangle's height, including effective vertical [Onboarding::padding](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#padding-prop).

The value is `0` when no step is current.

### padding : real {#padding-prop}

This property holds the requested space between the current target and the highlight border. Padding is applied symmetrically on each axis and clamped independently so the highlight remains within the source item's bounds. Negative values therefore have the same visual result as `0`.

The value is shared by all walkthroughs. The default value is `0`.

### source : Item {#source-prop}

This read-only property holds the source item selected for the most recently started walkthrough. Test [Onboarding::active](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#active-prop) before treating it as an active overlay source.

The value is `null` before a source is selected or after that source is destroyed.

### width : real {#width-prop}

This read-only property holds the highlighted rectangle's width, including effective horizontal [Onboarding::padding](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#padding-prop).

The value is `0` when no step is current.

### x : real {#x-prop}

This read-only property holds the highlighted rectangle's x coordinate in the source item's coordinate system. It includes the effective [Onboarding::padding](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#padding-prop) and updates when the target or its ancestors move.

The value is `0` when no step is current.

### y : real {#y-prop}

This read-only property holds the highlighted rectangle's y coordinate in the source item's coordinate system. It includes the effective [Onboarding::padding](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#padding-prop) and updates when the target or its ancestors move.

The value is `0` when no step is current.

## Attached Property Documentation {#attached-property-documentation}

### Onboarding.additionalData : var {#additionalData-attached-prop}

Application-defined metadata associated with this step. The value is a JavaScript object exposed through `Onboarding.currentItem.additionalData` while the step is current.

Assigning this property marks the item as a walkthrough step. Non-empty metadata allows the step to participate even when its text for the active group is empty. Display the metadata by setting [Onboarding::additionalDataComponent](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#additionalDataComponent-prop).

The default value is an empty object.

### Onboarding.enabled : bool {#enabled-attached-prop}

Whether this step can become current. Disabled steps remain in the collected step list but are skipped by initial selection and navigation. Changes take effect for subsequent navigation.

The default value is `true`.

### Onboarding.groups : list\<string\> {#groups-attached-prop}

The groups this step belongs to. Entries correspond by position to entries in [Onboarding::texts](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#texts-attached-prop). A step can belong to multiple groups and provide different text for each one.

The default value is a list containing the empty string.

### Onboarding.isSource : bool {#isSource-attached-prop}

Whether the attached item defines an onboarding source area.

While its walkthrough is active, the module enables the source item's layer so it can apply the masked blur effect. The previous `layer.enabled` value is restored when the walkthrough stops. The source should be a common visual ancestor of all steps in the groups it owns.

The default value is `false`.

### Onboarding.sequence : int {#sequence-attached-prop}

This read-only property holds the attached object's ordering key. The controller sorts participating steps by this value, which reflects attached-object creation order.

### Onboarding.sourceGroups : list\<string\> {#sourceGroups-attached-prop}

The groups owned by this source item. Each group must be owned by exactly one source item among the currently instantiated objects. The empty string identifies the default group.

The default value is a list containing the empty string.

### Onboarding.target : Item {#target-attached-prop}

This read-only property holds the item to which this Onboarding object is attached. For [Onboarding::currentItem](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#currentItem-prop), it is the item enclosed by the highlight.

### Onboarding.texts : list\<string\> {#texts-attached-prop}

The guidance strings for this step. Each string applies to the group at the same index in [Onboarding::groups](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#groups-attached-prop). A missing or out-of-range entry produces an empty string for that group.

Assigning this property marks the item as a walkthrough step. A step with empty text participates only when [Onboarding::additionalData](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#additionalData-attached-prop) is non-empty.

The default value is an empty list.

## Signal Documentation {#signal-documentation}

### aboutToStart() {#aboutToStart-signal}

Emitted after the source and step list have been selected but before the source layer, visual effect, and first step are activated.

Use this signal for application-wide preparation that must happen before a walkthrough becomes visible.

> **Note:** The corresponding handler is `onAboutToStart`.

### finished() {#finished-signal}

Emitted after [Onboarding::stop](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#stop-method)() has deactivated and reset the walkthrough. It is also emitted if an active source item is destroyed.

The signal is not emitted when [Onboarding::start](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#start-method-1)(string) replaces one active walkthrough with another.

> **Note:** The corresponding handler is `onFinished`.

## Attached Signal Documentation {#attached-signal-documentation}

### aboutToShow() {#aboutToShow-signal}

Emitted after this step is selected but before it becomes [Onboarding::currentItem](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#currentItem-prop) and before its geometry is resolved.

Use this handler to expose or instantiate the target, for example by selecting the page that contains it. The controller updates the current item on the next event-loop turn.

> **Note:** The corresponding handler is `onAboutToShow`.

### hide() {#hide-signal}

Emitted when this step stops being the current step because navigation, stopping, or restarting replaces or clears it.

> **Note:** The corresponding handler is `onHide`.

## Method Documentation {#method-documentation}

### void next() {#next-method}

Advances to the next enabled step. Disabled or destroyed step items are skipped. This method has no effect when the walkthrough is inactive or there is no later enabled step.

### void previous() {#previous-method}

Returns to the previous enabled step. Disabled or destroyed step items are skipped. This method has no effect when the walkthrough is inactive or there is no earlier enabled step.

### void start() {#start-method}

Starts the default group, identified by the empty string.

Exactly one item must declare the default group in [Onboarding::sourceGroups](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#sourceGroups-attached-prop), and that source must contain at least one participating step. If the source cannot be resolved, the walkthrough is not started.

### void start(string *group*) {#start-method-1}

Starts the walkthrough for `group`.

Exactly one source item must include `group` in [Onboarding::sourceGroups](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#sourceGroups-attached-prop). Steps are collected from descendant items whose [Onboarding::groups](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#groups-attached-prop) contain `group` and that provide content for the group. If the source cannot be resolved or no participating steps exist, the walkthrough is not started.

Calling this method while another walkthrough is active hides its current step and replaces its source, group, and step list.

### void stop() {#stop-method}

Stops the current walkthrough, hides its current step, removes the visual effect, restores the source item's previous `layer.enabled` value, resets [Onboarding::currentIndex](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#currentIndex-prop) to `-1`, and emits [Onboarding::finished](qml-org-kde-kirigamiaddons-onboarding-onboarding.md#finished-signal).

Calling this method when no walkthrough or current step exists has no effect.
