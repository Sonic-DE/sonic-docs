---
title: "SearchPopupField QML Type"
description: "SearchField with a Popup to show autocompletion entries or search results. This type is deprecated. We strongly advise against using it in new code."
---

# SearchPopupField QML Type

[SearchField](../kirigami/qml-org-kde-kirigami-searchfield.md) with a Popup to show autocompletion entries or search results. **This type is deprecated. We strongly advise against using it in new code.** [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [Control](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html)
- Status: Deprecated

**This type is deprecated. We strongly advise against using it in new code.**

## Detailed Description {#details}

Use Kirigami.[SearchDialog](../kirigami/qml-org-kde-kirigami-dialogs-searchdialog.md) instead.

Can be replaced by the following code:

```qml
Kirigami.SearchField {
    TapHandler {
        onTapped: {
            searchDialog.open();
        }
        acceptedButtons: Qt.RightButton | Qt.LeftButton
    }
    Keys.onPressed: (event) => {
        if (event.key !== Qt.Key_Tab || event.key !== Qt.Key_Backtab) {
            searchDialog.open();
            searchDialog.text = text;
        }
    }
    Keys.priority: Keys.AfterItem

    Kirigami.SearchDialog {
        id: searchDialog
        ...
    }
}
```

*See also* [SearchDialog](../kirigami/qml-org-kde-kirigami-dialogs-searchdialog.md)

## Property Documentation {#property-documentation}

### \[default: false\] autoAccept : bool {#autoAccept-prop}

This property sets whether the accepted signal is fired automatically when the text is changed.

Setting this to `false` will require that the user presses return or enter (the same way a [TextInput](https://doc.qt.io/qt-6/qml-qtquick-textinput.html) works).

### \[default: false\] delaySearch : bool {#delaySearch-prop}

This property sets whether to delay automatic acceptance of the search input.

Set this to `true` if your search is expensive (such as for online operations or in exceptionally slow data sets) and want to delay it for 2.5 seconds.

> **Note:** If you must have immediate feedback (filter-style), use the [text](qml-org-kde-kirigamiaddons-components-searchpopupfield.md#text-prop) property directly instead of [accepted](qml-org-kde-kirigamiaddons-components-searchpopupfield.md#accepted-signal)()

### fieldFocus : bool {#fieldFocus-prop}

This hold the [focus](https://doc.qt.io/qt-6/qml-qtquick-item.html#focus-prop) state of the internal [SearchField](../kirigami/qml-org-kde-kirigami-searchfield.md).

### popup : Popup {#popup-prop}

### \[default\] popupContentItem : Item {#popupContentItem-prop}

This property holds the content item of the [popup](qml-org-kde-kirigamiaddons-components-searchpopupfield.md#popup-prop).

Overflow will be automatically handled as popupContentItem is contained inside a [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html).

This is the default element of [SearchPopupField](qml-org-kde-kirigamiaddons-components-searchpopupfield.md).

```qml
SearchPopupField {
    ListView {
        model: SearchModel {}
        delegate: QQC2.ItemDelegate {}

        Kirigami.PlaceholderMessage {
            id: loadingPlaceholder
            anchors.centerIn: parent
            width: parent.width - Kirigami.Units.gridUnit * 4
            // ...
        }
    }
}
```

### searchField : Kirigami.SearchField {#searchField-prop}

### text : string {#text-prop}

This property holds the [text](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#text-prop) of the search field.

## Signal Documentation {#signal-documentation}

### accepted() {#accepted-signal}

This signal is triggered when the user trigger a search.

> **Note:** The corresponding handler is `onAccepted`.
