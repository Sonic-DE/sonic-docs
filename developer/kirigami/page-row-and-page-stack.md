---
title: Page rows and page stacks
description: "Add flow to your application: add, remove and replace pages in different ways."
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-pagerow_pagestack/
source_authors: [Carl Schwan, Claudio Cambra, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami PageRow.qml, AbstractApplicationWindow.qml and the global toolbar style group, examples run with the qml tool plus a push/pop/goBack/goForward check"
---

# Page rows and page stacks

## A row of pages

So far we have seen that one of the core components of a Kirigami window is a [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page). A single page can fill the whole screen of the application, or it can be shown together with other pages at the same time, if there is space.

Whenever a page is added, or *pushed*, it appears to the right of the existing pages, forming a row. This row of pages is managed by the fittingly named [Kirigami.PageRow](/docs/api/kirigami/qml-org-kde-kirigami-pagerow).

A minimal page row with a single page could look like this:

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Single Page"
    width: 500
    height: 200

    Kirigami.PageRow {
        anchors.fill: parent

        Kirigami.Page {
            id: mainPage
            anchors.fill: parent
            Rectangle {
                anchors.fill: parent
                color: "lightblue"
            }
        }
    }
}
```

Two improvements can be made here. First, with [initialPage](/docs/api/kirigami/qml-org-kde-kirigami-pagerow#initialPage-prop) we can both make `mainPage` the first page of the page row and have the page row manage its size, instead of manual [anchors](https://doc.qt.io/qt-6/qtquick-positioning-anchors.html), [positioners](https://doc.qt.io/qt-6/qtquick-positioning-layouts.html) or [layouts](https://doc.qt.io/qt-6/qtquicklayouts-index.html). Second, we can add a toolbar by choosing a toolbar style with [globalToolBar](/docs/api/kirigami/qml-org-kde-kirigami-pagerow#globalToolBar-prop)`.style`. There are a few styles to choose from (Auto, Breadcrumb, Titles, ToolBar and None); we'll use `Kirigami.ApplicationHeaderStyle.Auto` for now, which behaves like ToolBar on the desktop.

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "With globalToolBar and initialPage"
    width: 500
    height: 200
    Kirigami.PageRow {
        anchors.fill: parent
        globalToolBar.style: Kirigami.ApplicationHeaderStyle.Auto
        initialPage: Kirigami.Page {
            Rectangle {
                anchors.fill: parent
                color: "lightblue"
            }
        }
    }
}
```

The usual ways to add pages to a page row are setting its [initialPage](/docs/api/kirigami/qml-org-kde-kirigami-pagerow#initialPage-prop) (which can also take an array of pages) and calling [push()](/docs/api/kirigami/qml-org-kde-kirigami-pagerow#push-method). PageRow also has [insertPage()](/docs/api/kirigami/qml-org-kde-kirigami-pagerow#insertPage-method) and [replace()](/docs/api/kirigami/qml-org-kde-kirigami-pagerow#replace-method), described in its API reference. To remove a page from the page row, use [pop()](/docs/api/kirigami/qml-org-kde-kirigami-pagerow#pop-method); [goBack()](/docs/api/kirigami/qml-org-kde-kirigami-pagerow#goBack-method) and [goForward()](/docs/api/kirigami/qml-org-kde-kirigami-pagerow#goForward-method) move between pages.

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Multiple pages in a row"
    width: 700
    height: 300
    Kirigami.PageRow {
        id: mainRow
        anchors.fill: parent
        globalToolBar.style: Kirigami.ApplicationHeaderStyle.Auto
        initialPage: Kirigami.Page {
            id: firstPage
            Rectangle {
                anchors.fill: parent
                color: "lightblue"
                Controls.Button {
                    anchors.centerIn: parent
                    text: "Push!"
                    onClicked: mainRow.push(secondPage)
                }
            }
        }

        Component {
            id: secondPage
            Kirigami.Page {
                Rectangle {
                    anchors.fill: parent
                    color: "lightgreen"
                    Controls.Button {
                        anchors.centerIn: parent
                        text: "Pop!"
                        onClicked: mainRow.pop()
                    }
                }
            }
        }
    }
}
```

Clicking "Push!" shows a second, light green page next to the first one; clicking "Pop!" removes it again.

## The application's stack of pages

If a [Kirigami.PageRow](/docs/api/kirigami/qml-org-kde-kirigami-pagerow) with a toolbar looks familiar, that's because you have seen it before. [ApplicationWindow.pageStack](/docs/api/kirigami/qml-org-kde-kirigami-applicationwindow#pageStack-prop) is nothing more than a very convenient, global page row. Every function available to a `PageRow` is also available to the `pageStack`.

The previous example becomes much shorter with the `pageStack`, and on the desktop its toolbar also gets back and forward buttons:

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Using the pageStack"
    width: 500
    height: 200
    pageStack.initialPage: Kirigami.Page {
        id: firstPage
        Rectangle {
            anchors.fill: parent
            color: "lightblue"
            Controls.Button {
                anchors.centerIn: parent
                text: "Push!"
                onClicked: pageStack.push(secondPage)
            }
        }
    }
    Component {
        id: secondPage
        Kirigami.Page {
            Rectangle {
                anchors.fill: parent
                color: "lightgreen"
                Controls.Button {
                    anchors.centerIn: parent
                    text: "Pop!"
                    onClicked: pageStack.pop()
                }
            }
        }
    }
}
```

In general you'll want to use the `pageStack` rather than your own [PageRow](/docs/api/kirigami/qml-org-kde-kirigami-pagerow), especially as your application grows and its components live in separate files. If you create your window in `Main.qml` with a [Kirigami.ApplicationWindow](/docs/api/kirigami/qml-org-kde-kirigami-applicationwindow), a component in another file can still reach the global `pageStack` by calling [applicationWindow()](/docs/api/kirigami/qml-org-kde-kirigami-abstractapplicationwindow#applicationWindow-method):

```qml
// "Main.qml"
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Pushing a Page from a different QML file"
    width: 700
    height: 400
    pageStack.initialPage: BasicPage {}
}
```

and

```qml
// "BasicPage.qml"
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.Page {
    Controls.Button {
        anchors.centerIn: parent
        text: "This pushes page1 from BasicPage\ninto the pageStack from Main.qml!"
        onClicked: {
            applicationWindow().pageStack.push(page1)
        }
        Component {
            id: page1
            Kirigami.Page {
                Controls.Label {
                    anchors.centerIn: parent
                    text: "page1 was pushed!"
                }
            }
        }
    }
}
```

Clicking the button pushes a new page with the help of `applicationWindow()`.
