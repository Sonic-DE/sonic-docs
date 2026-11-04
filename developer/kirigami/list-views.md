---
title: Layouts, ListViews, and Cards
description: Different ways of placing things on a page.
source_url: https://develop.kde.org/docs/getting-started/kirigami/introduction-listviews/
source_authors: [Antti Savolainen, Carl Schwan, Claudio Cambra, Harshit Tomar, Michael Rostom, Mikhail Zolotukhin, Nicolas Fella, Swapnil Tripathi, Thiago Sueto, Yuri Chornoivan]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-quick-ui (CardsListView, AbstractCard, Heading, Separator, platform/units.cpp default units); the example was built into the tutorial application and loaded offscreen without QML errors
---

# Laying out your content

Now that we understand pages, it is time to put things on them. This section goes through some important layout components and elements for designing our application.

By the end of it you'll have a neat-looking application.

## ListViews

If you've used SonicDE's System Settings, you have come across a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html). Put simply, it shows data in a list.

```qml
pageStack.initialPage: Kirigami.ScrollablePage {
    // ...
    Kirigami.CardsListView {
       id: cardsView
        model: kountdownModel
        delegate: kountdownDelegate
    }
}
```

That looks cryptic, but don't worry. Let's start from the beginning.

We add this component inside the [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage) from the last step.

We use [Kirigami.CardsListView](/docs/api/kirigami/qml-org-kde-kirigami-cardslistview), a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) that makes it easy to show cards in a list. ListViews show data taken from a model: they fill themselves from the data we point them to. That is the [model](https://doc.qt.io/qt-6/qml-qtquick-listview.html#model-prop) property, which here points to `kountdownModel`.

### Model

```qml
Kirigami.ApplicationWindow {
    // ...
    ListModel {
        id: kountdownModel
        // Each ListElement is an element on the list, containing information
        ListElement {
            name: "Dog birthday!!"
            description: "Big doggo birthday blowout."
            date: 100
        }
    }
    // ...
}
```

We add `kountdownModel` inside the [Kirigami.ApplicationWindow](/docs/api/kirigami/qml-org-kde-kirigami-applicationwindow) from the last step.

A model defines how a data entry is structured. Our `kountdownModel` has a single element for now. Its [ListElement](https://doc.qt.io/qt-6/qml-qtqml-models-listelement.html) shows the structure of the data: a name, a description and a date. That isn't fixed; your model can hold other kinds of data. The first two are strings, and the third is a number we use as a placeholder for now.

> **Note:** QML builds on JavaScript, so many of the language's features are available in QML files. But QML variables must be declared with `property`, except inside JavaScript code blocks. See [JavaScript in QML](https://doc.qt.io/qt-6/qtqml-javascript-topic.html).

Models can also be changed with several methods. Some important ones:

- [ListModel.append(yourobject: jsobject)](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html#append-method) adds a JavaScript object (JSObject), `yourobject`, after the last item of the ListModel. The object must have the right properties and data types.
- [ListModel.get(index: int)](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html#get-method) returns the JSObject at the given index.
- [ListModel.remove(index: int, count: int)](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html#remove-method) removes the JSObject at `index`, and as many after it as `count` says (1 removes only the one at `index`).
- [ListModel.set(index: int, yourobject: jsobject)](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html#set-method) changes the item at `index` to the values in `yourobject`, with the same rules as `append()`.

### Delegates

`kountdownModel` holds the data to show; `kountdownDelegate` decides how it is shown in the [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html). The [Kirigami.CardsListView](/docs/api/kirigami/qml-org-kde-kirigami-cardslistview) is made for card delegates, and our delegates are drawn as [Kirigami.AbstractCard](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard)s.

Delegates automatically get the properties of the model's [ListElement](https://doc.qt.io/qt-6/qml-qtqml-models-listelement.html)s, so we can refer to `name`, `description` and `date` like ordinary variables in the delegate.

### Building the delegate card

The [Component](https://doc.qt.io/qt-6/qml-qtqml-component.html) that is our delegate goes inside the [Kirigami.ApplicationWindow](/docs/api/kirigami/qml-org-kde-kirigami-applicationwindow). Then we look at what each part does.

```qml
Kirigami.ApplicationWindow {
    // ...
    Component {
        id: kountdownDelegate
        Kirigami.AbstractCard {
            contentItem: Item {
                // implicitWidth/Height define the natural width/height
                // of an item if no width or height is specified.
                // The setting below defines a component's preferred size based on its content
                implicitWidth: delegateLayout.implicitWidth
                implicitHeight: delegateLayout.implicitHeight
                GridLayout {
                    id: delegateLayout
                    anchors {
                        left: parent.left
                        top: parent.top
                        right: parent.right
                    }
                    rowSpacing: Kirigami.Units.largeSpacing
                    columnSpacing: Kirigami.Units.largeSpacing
                    columns: root.wideScreen ? 4 : 2

                    Kirigami.Heading {
                        level: 1
                        text: date
                    }

                    ColumnLayout {
                        Kirigami.Heading {
                            Layout.fillWidth: true
                            level: 2
                            text: name
                        }
                        Kirigami.Separator {
                            Layout.fillWidth: true
                            visible: description.length > 0
                        }
                        Controls.Label {
                            Layout.fillWidth: true
                            wrapMode: Text.WordWrap
                            text: description
                            visible: description.length > 0
                        }
                    }
                    Controls.Button {
                        Layout.alignment: Qt.AlignRight
                        Layout.columnSpan: 2
                        text: i18nc("@action:button","Edit")
                        // onClicked: to be done... soon!
                    }
                }
            }
        }
    }
    // ...
}
```

#### implicitWidth and implicitHeight

First, how the component's width and height are managed:

```qml
Kirigami.AbstractCard {
    contentItem: Item {
        implicitWidth: delegateLayout.implicitWidth
        implicitHeight: delegateLayout.implicitHeight
        GridLayout {
            id: delegateLayout
            // ...
        }
    }
}
```

The first properties set in our [Kirigami.AbstractCard](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard)'s content are [implicitWidth](https://doc.qt.io/qt-6/qml-qtquick-item.html#implicitWidth-prop) and [implicitHeight](https://doc.qt.io/qt-6/qml-qtquick-item.html#implicitHeight-prop), set to those of the [GridLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-gridlayout.html), `delegateLayout.implicitWidth` and `delegateLayout.implicitHeight`.

Every [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) has an implicit width and height: hints used as the default, or fallback, when no explicit width or height is set. They default to 0×0, so it is very important to set them for plain Items like this one.

Setting them to the GridLayout's makes sure the content doesn't spill out of the card: the card takes as much space as its content needs.

#### Layouts

The [GridLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-gridlayout.html) is inside the [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) we gave as [contentItem](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html#contentItem-prop): the Item holding what the card shows.

We also need a [layout](https://doc.qt.io/qt-6/qtquicklayouts-index.html), so the components don't pile up on top of each other. There are three main kinds:

- [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html) arranges components vertically, in one column;
- [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html) arranges them horizontally, in one row;
- [GridLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-gridlayout.html) arranges them in a grid of your choice.

With ColumnLayout and RowLayout, you just write the components inside the layout. We chose a GridLayout, which takes a bit more work:

```qml
GridLayout {
    id: delegateLayout
    anchors {
        left: parent.left
        top: parent.top
        right: parent.right
    }
    rowSpacing: Kirigami.Units.largeSpacing
    columnSpacing: Kirigami.Units.largeSpacing
    columns: root.wideScreen ? 4 : 2
    // ...
}
```

First the `anchors`. Qt Quick's [anchoring](https://doc.qt.io/qt-6/qtquick-positioning-anchors.html) positions components relative to parts of their parent. We anchor the GridLayout to the left, top and right of the card, so the content stretches across the whole card.

Then we set the spacing between the grid's rows and columns, so the components don't bunch up. Kirigami has [predefined units](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units) for this. Their default values are:

| Kirigami unit | Pixels |
| --- | --- |
| smallSpacing | 4 |
| mediumSpacing | 6 |
| largeSpacing | 8 |
| gridUnit | 18 |

> **Note:** The [design guidelines](../hig/index.md) say more about the units and how to use them.

`root` is the id of our [Kirigami.ApplicationWindow](/docs/api/kirigami/qml-org-kde-kirigami-applicationwindow). Its [wideScreen](/docs/api/kirigami/qml-org-kde-kirigami-abstractapplicationwindow#wideScreen-prop) property tells whether the screen is wide (a computer monitor, or a phone in landscape). The [conditional operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_operator) chooses the number of grid columns accordingly: 4 on a wide screen, 2 otherwise.

#### Inner components

We could just put three labels in the delegate, but that wouldn't look nice. We use a few more convenient components:

```qml
GridLayout {
    // ...
    Kirigami.Heading {
        level: 1
        text: date
    }

    ColumnLayout {
        Kirigami.Heading {
            Layout.fillWidth: true
            level: 2
            text: name
        }

        Kirigami.Separator {
            Layout.fillWidth: true
            visible: description.length > 0
        }

        Controls.Label {
            Layout.fillWidth: true
            wrapMode: Text.WordWrap
            text: description
            visible: description.length > 0
        }
    }

    Controls.Button {
        Layout.alignment: Qt.AlignRight
        Layout.columnSpan: 2
        text: i18nc("@action:button","Edit")
    }
}
```

- Left, a [Kirigami.Heading](/docs/api/kirigami/qml-org-kde-kirigami-heading): the `ListElement`'s `date` as a level 1 heading.
- Middle, a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html) with a [Kirigami.Heading](/docs/api/kirigami/qml-org-kde-kirigami-heading) for the task's name, a [Kirigami.Separator](/docs/api/kirigami/qml-org-kde-kirigami-primitives-separator) for the horizontal line, and a [Controls.Label](https://doc.qt.io/qt-6/qml-qtquick-controls-label.html) for the task's optional description. The last two have a [visible](https://doc.qt.io/qt-6/qml-qtquick-item.html#visible-prop) property that shows them only if the description isn't empty (`description.length > 0`).
- Right, a [Controls.Button](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html): a button that will do something... soon!

## Our application so far

`Main.qml`:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    id: root

    width: 400
    height: 300

    title: i18nc("@title:window", "Day Kountdown")

    // ListModel needed for ListView, contains elements to be displayed
    ListModel {
        id: kountdownModel
        // Each ListElement is an element on the list, containing information
        ListElement {
            name: "Dog birthday!!"
            description: "Big doggo birthday blowout."
            date: 100
        }
    }

    Component {
        id: kountdownDelegate
        Kirigami.AbstractCard {
            contentItem: Item {
                implicitWidth: delegateLayout.implicitWidth
                implicitHeight: delegateLayout.implicitHeight
                GridLayout {
                    id: delegateLayout
                    anchors {
                        left: parent.left
                        top: parent.top
                        right: parent.right
                    }
                    rowSpacing: Kirigami.Units.largeSpacing
                    columnSpacing: Kirigami.Units.largeSpacing
                    columns: root.wideScreen ? 4 : 2

                    Kirigami.Heading {
                        // Level determines the size of the heading
                        level: 1
                        text: date
                    }

                    // Layout for positioning elements vertically
                    ColumnLayout {
                        Kirigami.Heading {
                            Layout.fillWidth: true
                            level: 2
                            text: name
                        }
                        // Horizontal rule
                        Kirigami.Separator {
                            Layout.fillWidth: true
                            visible: description.length > 0
                        }
                        // Labels contain text
                        Controls.Label {
                            Layout.fillWidth: true
                            // Word wrap makes text stay within box and shift with size
                            wrapMode: Text.WordWrap
                            text: description
                            visible: description.length > 0
                        }
                    }
                    Controls.Button {
                        Layout.alignment: Qt.AlignRight
                        // Column spanning within grid layout (vertically in this case)
                        Layout.columnSpan: 2
                        text: i18nc("@action:button","Edit")
                        //onClicked: to be done...
                    }
                }
            }
        }
    }

    pageStack.initialPage: Kirigami.ScrollablePage {
        title: i18nc("@title", "Kountdown")

        // List view for card elements
        Kirigami.CardsListView {
            id: cardsView
            // Model contains info to be displayed
            model: kountdownModel
            // Delegate is how the information will be presented in the ListView
            delegate: kountdownDelegate
        }
    }
}
```

That's our basic card! With these steps we have laid the groundwork for adding all of the application's functionality.
