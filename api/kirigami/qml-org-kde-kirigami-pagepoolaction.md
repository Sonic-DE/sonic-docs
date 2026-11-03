---
title: "PagePoolAction QML Type"
description: "An action used to load Pages coming from a common PagePool in a PageRow or QtQuickControls2 StackView."
---

# PagePoolAction QML Type

An action used to load Pages coming from a common [PagePool](qml-org-kde-kirigami-pagepool.md) in a [PageRow](qml-org-kde-kirigami-pagerow.md) or [QtQuickControls2](https://doc.qt.io/qt-6/qtquickcontrols2-module.html) [StackView](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html). [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Action](qml-org-kde-kirigami-action.md)

## Detailed Description {#details}

*See also* [PagePool](qml-org-kde-kirigami-pagepool.md)

## Property Documentation {#property-documentation}

### basePage : Page {#basePage-prop}

This property sets the page in the [pageStack](qml-org-kde-kirigami-pagepoolaction.md#pageStack-prop) after which new pages will be pushed.

All pages present after the given basePage will be removed from the [pageStack](qml-org-kde-kirigami-pagepoolaction.md#pageStack-prop)

### initialProperties : var {#initialProperties-prop}

This property holds a function that generate the property values for the created page when it is pushed onto the Kirigami.[PagePool](qml-org-kde-kirigami-pagepool.md).

Example usage:

```qml
Kirigami.PagePoolAction {
    text: i18n("Security")
    icon.name: "security-low"
    page: Qt.resolvedUrl("Security.qml")
    initialProperties: {
        return {
            room: root.room
        }
    }
}
```

### page : string {#page-prop}

This property holds the url or filename of the page that this action will load.

### pagePool : KC.PagePool {#pagePool-prop}

This property holds the [PagePool](qml-org-kde-kirigami-pagepool.md) object used by this [PagePoolAction](qml-org-kde-kirigami-pagepoolaction.md).

[PagePool](qml-org-kde-kirigami-pagepool.md) will make sure only one instance of the page identified by the page url will be created and reused.

[PagePool](qml-org-kde-kirigami-pagepool.md)'s lastLoaderUrl property will be used to control the mutual exclusivity of the checked state of the [PagePoolAction](qml-org-kde-kirigami-pagepoolaction.md) instances sharing the same [PagePool](qml-org-kde-kirigami-pagepool.md).

### pageStack : Item {#pageStack-prop}

The pageStack property accepts either a Kirigami.[PageRow](qml-org-kde-kirigami-pagerow.md) or a [QtQuickControls2](https://doc.qt.io/qt-6/qtquickcontrols2-module.html) [StackView](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html); the component that will instantiate the pages, which has to work with a stack logic.

Kirigami.[PageRow](qml-org-kde-kirigami-pagerow.md) is recommended, but will work with QtQuicControls2 [StackView](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html) as well.

default: bound to [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md)'s global pageStack, which is a [PageRow](qml-org-kde-kirigami-pagerow.md) by default

### useLayers : bool {#useLayers-prop}

This property sets whether [PagePoolAction](qml-org-kde-kirigami-pagepoolaction.md) will use the layers property implemented by the [pageStack](qml-org-kde-kirigami-pagepoolaction.md#pageStack-prop).

This is intended for use with [PageRow](qml-org-kde-kirigami-pagerow.md) layers to allow PagePoolActions to push context-specific pages onto the layers stack.

default: `false`

## Method Documentation {#method-documentation}

### bool layerContainsPage() {#layerContainsPage-method}

Returns `true` if the page has been loaded and placed on `pageStack.layers` and [useLayers](qml-org-kde-kirigami-pagepoolaction.md#useLayers-prop) is true, otherwise returns `null`.

### Item pageItem() {#pageItem-method}

Returns the page item held in the [PagePool](qml-org-kde-kirigami-pagepool.md) or null if it has not been loaded yet.

### bool stackContainsPage() {#stackContainsPage-method}

Returns `true` if the page has been loaded and placed on the [pageStack](qml-org-kde-kirigami-pagepoolaction.md#pageStack-prop), otherwise returns `null`.
