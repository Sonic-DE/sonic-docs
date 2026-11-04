---
title: List views
description: A list view helps you display many components dynamically.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-listview/
source_authors: [Carl Schwan, Claudio Cambra, Frederik Schwarzer, Jeongu Kim, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Qt 6.11 Models and Views documentation, Kirigami delegates module and tests/ListItemTest.qml, Silver icon theme, examples run with the qml tool (plus a check of list sizes in Page and ScrollablePage)"
---

# List views

[List views](https://doc.qt.io/qt-6/qml-qtquick-listview.html) help you display objects from a model in an attractive way. To use a list view, you keep track of three things:

1. The **model**, which contains the data you want your list view to display.
2. The **delegate**, which defines how each element of the model is displayed.
3. The **list view** itself, which displays the information from the model according to the delegate.

For more background, the Qt documentation has [an informative page](https://doc.qt.io/qt-6/qtquick-modelviewsdata-modelview.html) on the topic.

## Essentials of models and views

A list view has two essential properties:

- [model](https://doc.qt.io/qt-6/qml-qtquick-listview.html#model-prop), which accepts the data, or the `id` of the object that holds the data.
- [delegate](https://doc.qt.io/qt-6/qml-qtquick-listview.html#delegate-prop), which accepts the component used to display the data of the model.

The model isn't visible, as it only contains data. The delegate is typically wrapped in a Component so that it is reusable: it serves as a blueprint for instantiating each delegate.

Here is an example with exactly one list view, one model and one delegate, using a [Controls.ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html):

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "List of SonicDE interfaces"
    width: 600
    height: 400
    pageStack.initialPage: Kirigami.ScrollablePage {
        ListView {
            anchors.fill: parent
            model: sonicInterfacesModel
            delegate: listDelegate
        }
        ListModel {
            id: sonicInterfacesModel
            ListElement { product: "Desktop interface"; target: "desktops" }
            ListElement { product: "Mobile interface";  target: "phones" }
            ListElement { product: "TV interface"; target: "TVs" }
        }
        Component {
            id: listDelegate
            Controls.ItemDelegate {
                width: ListView.view.width
                text: `The ${model.product} is SonicDE software developed for ${model.target}, stored at index ${model.index} of this list`
            }
        }
    }
}
```

And the exact same example, inline:

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "List of SonicDE interfaces (inline)"
    width: 600
    height: 400
    pageStack.initialPage: Kirigami.ScrollablePage {
        ListView {
            anchors.fill: parent
            model: ListModel {
                id: sonicInterfacesModel
                ListElement { product: "Desktop interface"; target: "desktops" }
                ListElement { product: "Mobile interface";  target: "phones" }
                ListElement { product: "TV interface"; target: "TVs" }
            }
            delegate: Controls.ItemDelegate {
                width: ListView.view.width
                text: `The ${model.product} is SonicDE software developed for ${model.target}, stored at index ${model.index} of this list`
            }
        }
    }
}
```

### Understanding models

The model contains the data used to populate the list view. Different ways of using models give different ways of accessing the data:

| Way to use | How to access | When to use |
| --- | --- | --- |
| Qt models with more than one role | `model.index`, `model.somerole` | In most cases |
| Qt models with one role | `model.index`, `model.somerole`, `model.modelData` | In most cases, for prototyping |
| JavaScript array model | `model.index`, `model.modelData` | For prototyping |
| Integer model | `model.index`, `model.modelData` | For prototyping |

You can read about [other ways to use models in the Qt documentation](https://doc.qt.io/qt-6/qtquick-modelviewsdata-modelview.html).

In the table above, "Qt models" means both C++ models such as [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html) and QML models such as ListModel. This page only covers QML models. A later page covers [connecting C++ models to QML using QAbstractListModel](connect-models.md).

The `model.index` property is available with every model and contains the index (the position) of each delegate. For convenience it can be shortened to `index`.

The `model.somerole` property above is just a placeholder, not a specific property that comes from QML: `somerole` can be any role the model defines. In the first example on this page, the `sonicInterfacesModel` model has the `product` and `target` roles, accessed with `model.product` and `model.target`.

Just as `model.index` can be shortened to `index`, each `model.somerole` property can be shortened to just `somerole` (like `product`), but it is recommended to turn them into required properties:

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "List of SonicDE interfaces (shortened with required properties)"
    width: 600
    height: 400
    pageStack.initialPage: Kirigami.ScrollablePage {
        ListView {
            anchors.fill: parent
            model: sonicInterfacesModel
            delegate: listDelegate
        }
        ListModel {
            id: sonicInterfacesModel
            ListElement { product: "Desktop interface"; target: "desktops" }
            ListElement { product: "Mobile interface";  target: "phones" }
            ListElement { product: "TV interface"; target: "TVs" }
        }
        Component {
            id: listDelegate
            Controls.ItemDelegate {
                width: ListView.view.width
                required property string product
                required property string target
                required property int index
                text: `The ${product} is SonicDE software developed for ${target}, stored at index ${index} of this list`
            }
        }
    }
}
```

Once a delegate has required properties, the `model`, `index` and `modelData` roles are only available to it through required properties with matching names, which is why `index` is required here too.

If the model has only one role, or no role at all, its data can also be accessed with the `model.modelData` property, which can be shortened to `modelData` (and so would also need to be a required property):

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "List of SonicDE software"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.ScrollablePage {
        ListView {
            anchors.fill: parent
            model: sonicSoftwareModel
            delegate: listDelegate
        }
        ListModel {
            id: sonicSoftwareModel
            ListElement { software: "Ecco" }
            ListElement { software: "Screenies" }
            ListElement { software: "System Monitor" }
            ListElement { software: "System Settings" }
            ListElement { software: "Welcome Center" }
        }
        Component {
            id: listDelegate
            Controls.ItemDelegate {
                width: ListView.view.width
                required property string modelData
                text: modelData // This matches model.software
            }
        }
    }
}
```

For comparison, here is the same code with a [JavaScript array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array), which has no role:

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "List of SonicDE software (as JS array)"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.ScrollablePage {
        ListView {
            anchors.fill: parent
            model: ["Ecco", "Screenies", "System Monitor", "System Settings", "Welcome Center"]
            delegate: listDelegate
        }
        Component {
            id: listDelegate
            Controls.ItemDelegate {
                width: ListView.view.width
                required property string modelData
                text: modelData
            }
        }
    }
}
```

An integer model can be useful in very specific cases, namely prototyping and tests. Its `modelData` is the index of each item:

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Simple list of indexes"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.ScrollablePage {
        ListView {
            anchors.fill: parent
            model: 30
            delegate: listDelegate
        }
        Component {
            id: listDelegate
            Controls.ItemDelegate {
                width: ListView.view.width
                required property string modelData
                text: `This delegate's index is: ${modelData}`
            }
        }
    }
}
```

### Understanding views and delegates

Let's go back to the original example:

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "List of SonicDE interfaces"
    width: 600
    height: 400
    pageStack.initialPage: Kirigami.ScrollablePage {
        ListView {
            // anchors.fill: parent
            model: sonicInterfacesModel
            delegate: listDelegate
        }
        ListModel {
            id: sonicInterfacesModel
            ListElement { product: "Desktop interface"; target: "desktops" }
            ListElement { product: "Mobile interface";  target: "phones" }
            ListElement { product: "TV interface"; target: "TVs" }
        }
        Component {
            id: listDelegate
            Controls.ItemDelegate {
                width: ListView.view.width
                text: `The ${model.product} is SonicDE software developed for ${model.target}, stored at index ${model.index} of this list`
            }
        }
    }
}
```

Unlike the model (which merely contains data) and a delegate [Component](https://doc.qt.io/qt-6/qml-qtqml-component.html) (which only appears when instantiated), the view is a visual component that is instantiated immediately, so it needs either its size set or anchors or layouts.

Views are usually lists of content the user wants to scroll through. When one is added to a [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage), it becomes the main content with little padding around it, and there's no need to make it fill the page. When the view is added to a plain [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page), you need to set its size before it shows up. In other words: in the scrollable page above, `anchors.fill: parent` isn't required; in a plain page, it would be.

There are several view APIs you can use, some from Qt and some from Kirigami. These are the most common:

* Qt's [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
* Qt's [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html)
* Qt's [TableView](https://doc.qt.io/qt-6/qml-qtquick-tableview.html)
* Qt's [TreeView](https://doc.qt.io/qt-6/qml-qtquick-treeview.html)
* Kirigami's [CardsListView](/docs/api/kirigami/qml-org-kde-kirigami-cardslistview)
* Kirigami's [ColumnView](/docs/api/kirigami/qml-org-kde-kirigami-layouts-columnview)

The delegate, on the other hand, always needs its size set. Usually it is set to use the full width of the view.

> **Common mistakes:** Delegates shouldn't have bottom anchors, since a delegate doesn't need the same height as the view. In other words, you will probably never want `anchors.fill: parent` on a delegate.
>
> You could set its size from its parent with anchors, the parent usually being the view's contentItem:
>
> ```qml
> Controls.ItemDelegate {
>     anchors.left: parent.left
>     anchors.right: parent.right
>     text: // ...
> }
> ```
>
> But the delegate's parent isn't guaranteed to be a view, so avoid this. Instead, use the [ListView.view](https://doc.qt.io/qt-6/qml-qtquick-listview.html#view-attached-prop) attached property to refer to the delegate's view:
>
> ```qml
> Controls.ItemDelegate {
>     width: ListView.view.width
>     text: // ...
> }
> ```

The most common place for a delegate is inside a [Component](https://doc.qt.io/qt-6/qml-qtqml-component.html), which doesn't instantiate the delegate immediately. When a view is built, it uses the delegate as a blueprint for each of its items.

You can make your own components to use as delegates without delegate-specific Qt APIs (for example, a Layout containing a few Items), but Qt Quick Controls provides delegate APIs that are simpler to use:

* [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html) (delegates with only text)
* [CheckDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-checkdelegate.html) (delegates with a checkbox)
* [RadioDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-radiodelegate.html) (delegates with a radio button)
* [SwitchDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-switchdelegate.html) (delegates with a switch)
* [SwipeDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-swipedelegate.html) (delegates that can be swiped)

Prefer the upstream Qt delegates where possible.

On top of these Qt delegates, Kirigami provides its own equivalents, which add subtitles and icons:

* [TitleSubtitle](/docs/api/kirigami/qml-org-kde-kirigami-delegates-titlesubtitle)
* [IconTitleSubtitle](/docs/api/kirigami/qml-org-kde-kirigami-delegates-icontitlesubtitle)
* [SubtitleDelegate](/docs/api/kirigami/qml-org-kde-kirigami-delegates-subtitledelegate)
* [CheckSubtitleDelegate](/docs/api/kirigami/qml-org-kde-kirigami-delegates-checksubtitledelegate)
* [RadioSubtitleDelegate](/docs/api/kirigami/qml-org-kde-kirigami-delegates-radiosubtitledelegate)
* [SwitchSubtitleDelegate](/docs/api/kirigami/qml-org-kde-kirigami-delegates-switchsubtitledelegate)

The types ending in "Delegate" can be used directly as the view's delegate, just like `Controls.ItemDelegate` in the previous examples:

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.kirigami.delegates as KD

Kirigami.ApplicationWindow {
    title: "List of SonicDE interfaces"
    width: 600
    height: 400
    pageStack.initialPage: Kirigami.ScrollablePage {
        ListView {
            model: sonicInterfacesModel
            delegate: listDelegate
        }
        ListModel {
            id: sonicInterfacesModel
            ListElement { product: "Desktop interface"; target: "desktops" }
            ListElement { product: "Mobile interface";  target: "phones" }
            ListElement { product: "TV interface"; target: "TVs" }
        }
        Component {
            id: listDelegate
            KD.CheckSubtitleDelegate {
                width: ListView.view.width
                text: `The ${model.product} is SonicDE software developed for ${model.target}.`
                subtitle: `This delegate is stored at index ${model.index} of this list`
                icon.name: "start-here-sonicde"
            }
        }
    }
}
```

TitleSubtitle and IconTitleSubtitle are meant to replace the contentItem of a Qt delegate, for example:

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.kirigami.delegates as KD

Kirigami.ApplicationWindow {
    title: "List of SonicDE interfaces"
    width: 600
    height: 400
    pageStack.initialPage: Kirigami.ScrollablePage {
        ListView {
            // anchors.fill: parent
            model: sonicInterfacesModel
            delegate: listDelegate
        }
        ListModel {
            id: sonicInterfacesModel
            ListElement { product: "Desktop interface"; target: "desktops" }
            ListElement { product: "Mobile interface";  target: "phones" }
            ListElement { product: "TV interface"; target: "TVs" }
        }
        Component {
            id: listDelegate
            Controls.ItemDelegate {
                width: ListView.view.width
                text: `The ${model.product} is SonicDE software developed for ${model.target}.`
                contentItem: KD.IconTitleSubtitle {
                    title: parent.text
                    subtitle: `This delegate is stored at index ${model.index} of this list`
                    icon.name: "start-here-sonicde"
                }
            }
        }
    }
}
```

For a practical example of the Kirigami delegates, see [ListItemTest.qml in the Kirigami repository](https://github.com/Sonic-DE/sonic-frameworks-quick-ui/blob/master/tests/ListItemTest.qml).
