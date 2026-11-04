---
title: Scrollable pages and list views
description: Scrollable pages are useful together with vertical components or dynamic components such as list views.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-scrollablepages_listviews/
source_authors: [Carl Schwan, Claudio Cambra, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami ScrollablePage.qml, PullDownIndicator.qml and PlaceholderMessage.qml, KItemModels KSortFilterProxyModel, snippets run in a test window with the qml tool"
---

# Scrollable pages and list views

## Kirigami.ScrollablePage

A [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage) is a page that holds scrollable content, such as a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html). Scrolling and scroll bars are managed automatically.

```qml
Kirigami.ScrollablePage {
    id: root
    // The rectangle will automatically be scrollable
    Rectangle {
        width: root.width
        implicitHeight: 99999
    }
}
```

The page works out how far its content can scroll from the `implicitHeight` of its children, so give them an implicit height: a child that only sets `height` doesn't make the page scrollable.

In almost every other way, a scrollable page is the same as a normal page.

> **Warning:** Don't put a [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html) inside a [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage): the children of a `Kirigami.ScrollablePage` are already inside a `ScrollView`.

## ListView in a ScrollablePage

When the direct children of a [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage) extend vertically beyond the size of the page itself, a scroll bar appears at the right edge of the page and the page becomes scrollable.

Often you have more than one child in your [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage), and positioning items can be tricky, especially together with a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

* Non-visual components don't change how the page looks when they are inside the [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html), so we can move them into the scope of the list view. The same goes for elements anchored to the center of the page, such as placeholder messages for empty list views.
* For other items, it may make sense to move them to the header or footer of the [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage). This is often the case for search bars.

### PlaceholderMessage

You can add a [Kirigami.PlaceholderMessage](/docs/api/kirigami/qml-org-kde-kirigami-placeholdermessage) with some instructions for when the list view is empty. Its [helpfulAction](/docs/api/kirigami/qml-org-kde-kirigami-placeholdermessage#helpfulAction-prop) adds a button the user can click.

```qml
Kirigami.ScrollablePage {
    ListView {
        id: listView
        Kirigami.PlaceholderMessage {
            anchors.centerIn: parent
            width: parent.width - (Kirigami.Units.largeSpacing * 4)
            visible: listView.count === 0
            text: i18n("No data found")
            helpfulAction: Kirigami.Action {
                text: i18n("Load data")
                // More code...
            }
        }
        model: // Model code...
    }
}
```

### Search in the ListView

A search field is often added to a [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage) to filter the [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html). You can do this by replacing the default [titleDelegate](/docs/api/kirigami/qml-org-kde-kirigami-page#titleDelegate-prop) with a [Kirigami.SearchField](/docs/api/kirigami/qml-org-kde-kirigami-searchfield).

```qml
Kirigami.ScrollablePage {
    titleDelegate: Kirigami.SearchField {
        Layout.topMargin: Kirigami.Units.smallSpacing
        Layout.bottomMargin: Kirigami.Units.smallSpacing
        Layout.fillHeight: true
        Layout.fillWidth: true
        onTextChanged: mySortFilterModel.filterString = text
        KeyNavigation.tab: listView
    }

    ListView {
        id: listView
        // Rest of listview code...
    }
}
```

> **Hint:** With [KSortFilterProxyModel](/docs/api/kitemmodelsqml/qml-org-kde-kitemmodels-ksortfilterproxymodel) from [KItemModels](/docs/api/kitemmodels/kitemmodels-index) (`import org.kde.kitemmodels`) you can add filtering directly in QML, without any C++ code. Set its `sourceModel` and [filterRoleName](/docs/api/kitemmodelsqml/qml-org-kde-kitemmodels-ksortfilterproxymodel#filterRoleName-prop), use it as the list view's model, and the search field above filters it through [filterString](/docs/api/kitemmodelsqml/qml-org-kde-kitemmodels-ksortfilterproxymodel#filterString-prop).

### Pull to refresh

ScrollablePage also provides a "pull to refresh" action. Turn it on with [supportsRefreshing](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage#supportsRefreshing-prop):

```qml
Kirigami.ScrollablePage {
    id: view
    supportsRefreshing: true
    onRefreshingChanged: {
        if (refreshing) {
            myModel.refresh();
        }
    }
    ListView {
        // NOTE: MyModel doesn't come from the components,
        // it's purely an example on how it can be used together with
        // some application logic that can update the list model
        // and signals when it's done.
        model: MyModel {
            id: myModel
            onRefreshDone: view.refreshing = false;
        }
        delegate: Controls.ItemDelegate {}
    }
}
```

Pulling the list down far enough and holding it briefly sets [refreshing](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage#refreshing-prop) to `true`. A busy indicator stays above the list until your code sets `refreshing` back to `false`, as `onRefreshDone` does here.
