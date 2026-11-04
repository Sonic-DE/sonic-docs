---
title: Explaining pages
description: Pages organize your application's content.
source_url: https://develop.kde.org/docs/getting-started/kirigami/introduction-pages/
source_authors: [Carl Schwan, Chris Holland, Claudio Cambra, Jonah Brüchert, Joshua Wug, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-quick-ui (Page.qml derives from QQC2.Page, ScrollablePage); the example was built into the tutorial application and loaded offscreen without QML errors
---

# Explaining pages

## Our application

In the previous step we set up, built and ran our first Kirigami application. With the basics in place, we can start building a full application.

These tutorials build an application that shows the user how many days are left until events of their choice.

This section is about pages, one of the key structural elements of every Kirigami application.

## Pages

Kirigami applications are usually organized in pages, with [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page). Pages are the application's different "screens". Give each part of your application's interaction a page of its own; to keep things simple, you can write each page in its own QML file.

Pages are organized in a [page stack](/docs/api/kirigami/qml-org-kde-kirigami-abstractapplicationwindow#pageStack-prop), on which pages are pushed and popped. On a phone only the top page is shown; on a larger screen (desktop or tablet), several pages can be shown side by side.

> **Note:** [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page) derives from [Controls.Page](https://doc.qt.io/qt-6/qml-qtquick-controls-page.html), so you can use its properties too. When you read QML API documentation, also look at the functions and properties a type inherits.

Back to the `Main.qml` file from the previous step:

```qml
// Includes relevant modules used by the QML
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

// Provides basic features needed for all kirigami applications
Kirigami.ApplicationWindow {
    // Unique identifier to reference this object
    id: root

    width: 400
    height: 300

    // Window title
    // i18nc() makes a string translatable
    // and provides additional context for the translators
    title: i18nc("@title:window", "Hello World")

    // Set the first page that will be loaded when the app opens
    // This can also be set to an id of a Kirigami.Page
    pageStack.initialPage: Kirigami.Page {
        Controls.Label {
            // Center label horizontally and vertically within parent object
            anchors.centerIn: parent
            text: i18n("Hello World!")
        }
    }
}
```

The application starts with our [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page). All it has is a label saying "Hello World", but we're going to spruce things up.

The application will show a number of countdowns. A normal [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page) has a fixed height, so we use a [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage) instead, which comes with its own scroll bar.

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

    pageStack.initialPage: Kirigami.ScrollablePage {
        title: i18nc("@title", "Kountdown")
    }
}
```

Kirigami pages also show a title in the toolbar, so the user sees at once which page they are on. Just set the page's [title](https://doc.qt.io/qt-6/qml-qtquick-controls-page.html#title-prop) property, here with one of the `i18nc()` functions from the previous step.

> **Note:** You could also put the page in a QML file of its own. Create the file, for example `kirigami-tutorial/src/StartPage.qml`, add it to `ecm_target_qml_sources()` in `kirigami-tutorial/src/CMakeLists.txt`, and set it as the window's first page:
>
> ```js
> pageStack.initialPage: Qt.resolvedUrl("StartPage.qml")
> ```
>
> `pageStack.initialPage` sets the first page of the application's page stack, and [Qt.resolvedUrl()](https://doc.qt.io/qt-6/qml-qtqml-qt.html#resolvedUrl-method) turns the QML file's relative URL into an absolute one.
>
> [Page rows and page stacks](page-row-and-page-stack.md) describes other page structures.
