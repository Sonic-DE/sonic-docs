---
title: Cards
description: A card is an overview of and entry point to more detailed information, and can give direct access to the most important actions of an item.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-card/
source_authors: [Antti Savolainen, Carl Schwan, Claudio Cambra, Julius Künzel, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami AbstractCard (template and DefaultCardBackground), Card.qml, CardsLayout.qml and CardsListView.qml; snippets run with the qml tool, plus a CardsLayout column check at two widths"
---

# Cards

The Kirigami types [AbstractCard](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard) and [Card](/docs/api/kirigami/qml-org-kde-kirigami-card) implement the card component popular on many mobile and web platforms. Cards display a collection of information or actions in an attractive and distinctive way.

Kirigami also offers two components for laying out your cards: a [positioner](https://doc.qt.io/qt-6/qtquick-positioning-layouts.html), CardsLayout, and a [view](https://doc.qt.io/qt-6/qtquick-modelviewsdata-modelview.html), CardsListView. Both give your cards responsive layouts.

## AbstractCard

A [Kirigami.AbstractCard](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard) is the simplest type of card. It's just a rectangle with a shadow, which can contain any [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html). It can also have Items assigned to its [header](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard#header-prop) or [footer](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard#footer-prop) properties. Here a [Kirigami.Heading](/docs/api/kirigami/qml-org-kde-kirigami-heading) is its `header` and a [Controls.Label](https://doc.qt.io/qt-6/qml-qtquick-controls-label.html) is the card's [contentItem](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html#contentItem-prop).

```qml
Kirigami.AbstractCard {
    Layout.fillHeight: true
    header: Kirigami.Heading {
        text: qsTr("AbstractCard")
        level: 2
    }
    contentItem: Controls.Label {
        wrapMode: Text.WordWrap
        text: "..."
    }
}
```

## Card

A [Kirigami.Card](/docs/api/kirigami/qml-org-kde-kirigami-card) inherits from [AbstractCard](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard) and provides more features out of the box. Cards have the same [header](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard#header-prop) and [footer](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard#footer-prop) as an AbstractCard, but you are encouraged to use a [banner](/docs/api/kirigami/qml-org-kde-kirigami-card#banner-prop) and a set of [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) in the [actions](/docs/api/kirigami/qml-org-kde-kirigami-card#actions-prop) group instead.

```qml
Kirigami.Card {
    actions: [
        Kirigami.Action {
            text: qsTr("Action1")
            icon.name: "add-placemark"
        },
        Kirigami.Action {
            text: qsTr("Action2")
            icon.name: "address-book-new-symbolic"
        },
        // ...
    ]
    banner {
        source: "../banner.jpg"
        title: "Title Alignment"
        // The title can be positioned in the banner
        titleAlignment: Qt.AlignLeft | Qt.AlignBottom
    }
    contentItem: Controls.Label {
        wrapMode: Text.WordWrap
        text: "My Text"
    }
}

```

## CardsLayout

A [Kirigami.CardsLayout](/docs/api/kirigami/qml-org-kde-kirigami-cardslayout) is most useful when the cards aren't instantiated by a model, or are instantiated by a model that always has very few items. They are presented as a grid of two columns, which stays centered if the application is really wide, or becomes a single column if there isn't enough space for two, such as on a phone screen.

> **Note:** [CardsListView](/docs/api/kirigami/qml-org-kde-kirigami-cardslistview) is better suited for larger models.

> **Important:** A [CardsLayout](/docs/api/kirigami/qml-org-kde-kirigami-cardslayout) should always be contained within a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html).

A card can optionally be oriented horizontally, with its [headerOrientation](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard#headerOrientation-prop) set to `Qt.Horizontal`. It is then wider than tall, and better suited to being placed in a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html). If you put it in a [CardsLayout](/docs/api/kirigami/qml-org-kde-kirigami-cardslayout) anyway, keep in mind that the layout's [maximumColumns](/docs/api/kirigami/qml-org-kde-kirigami-cardslayout#maximumColumns-prop) is `2` by default.

```qml
ColumnLayout {
    Kirigami.CardsLayout {
        Kirigami.Card {
            contentItem: Controls.Label {
                wrapMode: Text.WordWrap
                text: "My Text2"
            }
        }
        Kirigami.AbstractCard {
            contentItem: Controls.Label {
                wrapMode: Text.WordWrap
                text: "My Text"
            }
        }
        Kirigami.Card {
            headerOrientation: Qt.Horizontal
            contentItem: Controls.Label {
                wrapMode: Text.WordWrap
                text: "My Text2"
            }
        }
    }
}
```

## CardsListView

A [Kirigami.CardsListView](/docs/api/kirigami/qml-org-kde-kirigami-cardslistview) is a list view meant for [AbstractCard](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard) components.

A [CardsListView](/docs/api/kirigami/qml-org-kde-kirigami-cardslistview) stretches its cards to its own width, so only use it with cards that look good at any horizontal size. Using a [Card](/docs/api/kirigami/qml-org-kde-kirigami-card) in it is discouraged, unless the card's [headerOrientation](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard#headerOrientation-prop) is [Qt.Horizontal](https://doc.qt.io/qt-6/qt.html#Orientation-enum).

```qml
Kirigami.CardsListView {
    id: view
    model: 100

    delegate: Kirigami.AbstractCard {
        //NOTE: never put a Layout as contentItem as it will cause binding loops
        contentItem: Item {
            implicitWidth: delegateLayout.implicitWidth
            implicitHeight: delegateLayout.implicitHeight
            GridLayout {
                id: delegateLayout
                anchors {
                    left: parent.left
                    top: parent.top
                    right: parent.right
                    //IMPORTANT: never put the bottom margin
                }
                rowSpacing: Kirigami.Units.largeSpacing
                columnSpacing: Kirigami.Units.largeSpacing
                columns: width > Kirigami.Units.gridUnit * 20 ? 4 : 2
                Kirigami.Icon {
                    source: "applications-graphics"
                    Layout.fillHeight: true
                    Layout.maximumHeight: Kirigami.Units.iconSizes.huge
                    Layout.preferredWidth: height
                }
                Kirigami.Heading {
                    level: 2
                    text: qsTr("Product ")+ modelData
                }
                Controls.Button {
                    Layout.alignment: Qt.AlignRight
                    Layout.columnSpan: 2
                    text: qsTr("Install")
                }
            }
        }
    }
}
```
