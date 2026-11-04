---
title: About page
description: Information about your application.
source_url: https://develop.kde.org/docs/getting-started/kirigami/advanced-add_about_page/
source_authors: [Carl Schwan, Felipe Kinoshita, Ignacy Kajdan, Kunda Ki, Martin Frueh, Mikhail Zolotukhin, Nicolas Fella, Phu Nguyen, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami AboutPage.qml and AboutItem.qml, KAboutData (sonic-frameworks-core-addons), the org.kde.coreaddons AboutData type, SonicDE's kirigami6 application template; the project built and run, and a test build that opens the page with and without its link properties"
---

# About page

[Kirigami.AboutPage](/docs/api/kirigami/qml-org-kde-kirigami-aboutpage) is a page that shows the application's copyright notice, its list of contributors and some information about the platform it runs on.

We build on the code from [Using separate files in a C++ project](separate-files.md), starting with its `main.cpp`.

### main.cpp

```cpp
#include <QApplication>
#include <QQmlApplicationEngine>
#include <QtQml>
#include <QUrl>
#include <QQuickStyle>
#include <KAboutData>
#include <KLocalizedQmlContext>
#include <KLocalizedString>
#include <KIconTheme>

int main(int argc, char *argv[])
{
    KIconTheme::initTheme();
    QApplication app(argc, argv);
    KLocalizedString::setApplicationDomain("tutorial");
    QApplication::setOrganizationName(QStringLiteral("KDE"));
    QApplication::setOrganizationDomain(QStringLiteral("kde.org"));
    QApplication::setApplicationName(QStringLiteral("Kirigami Tutorial"));
    QApplication::setDesktopFileName(QStringLiteral("org.kde.tutorial"));

    if (qEnvironmentVariableIsEmpty("QT_QUICK_CONTROLS_STYLE")) {
        QQuickStyle::setStyle(QStringLiteral("org.kde.desktop"));
    }

    KAboutData aboutData(
        QStringLiteral("tutorial"),
        i18nc("@title", "Kirigami Tutorial"),
        QStringLiteral("1.0"),
        i18n("A tutorial application"),
        KAboutLicense::GPL,
        i18n("(c) 2026"),
        QString(),
        QStringLiteral("https://example.com/tutorial/"),
        QStringLiteral("https://example.com/tutorial/bugs/"));

    aboutData.addAuthor(
        i18nc("@info:credit", "Your name"),
        i18nc("@info:credit", "Author Role"),
        QStringLiteral("your@email.com"),
        QStringLiteral("https://yourwebsite.com"));

    // The homepage would otherwise set the desktop file name to com.example.tutorial
    aboutData.setDesktopFileName(QStringLiteral("org.kde.tutorial"));

    // Set aboutData as information about the application
    KAboutData::setApplicationData(aboutData);

    QQmlApplicationEngine engine;

    KLocalization::setupLocalizedContext(&engine);
    engine.loadFromModule("org.kde.tutorial", "Main");

    if (engine.rootObjects().isEmpty()) {
        return -1;
    }

    return app.exec();
}
```

Here we include [KAboutData](/docs/api/kcoreaddons/kaboutdata), a core KDE Frameworks component that stores information about our application, which many other framework components can reuse. We create an `aboutData` object with its fairly complete constructor and add author information. Use your own homepage and bug address: without a bug address, KAboutData uses KDE's (`submit@bugs.kde.org`).

Then we call [KAboutData::setApplicationData()](/docs/api/kcoreaddons/kaboutdata#setApplicationData), which sets the properties of the [QApplication](https://doc.qt.io/qt-6/qapplication.html) object from this data, overwriting what we set on it earlier.

That includes the desktop file name. The homepage we pass gives a default desktop file name, here `com.example.tutorial`, which doesn't match our `org.kde.tutorial.desktop` file. So we set the right one with [setDesktopFileName()](/docs/api/kcoreaddons/kaboutdata#setDesktopFileName).

### Main.qml

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.coreaddons
import org.kde.tutorial.components

Kirigami.ApplicationWindow {
    id: root

    width: 600
    height: 400

    title: i18nc("@title:window", "Day Kountdown")

    globalDrawer: Kirigami.GlobalDrawer {
        isMenu: true
        actions: [
            Kirigami.Action { // <==== Action to open the About page
                text: i18n("About")
                icon.name: "help-about"
                onTriggered: pageStack.layers.push(aboutPage)
            },
            Kirigami.Action {
                text: i18n("Quit")
                icon.name: "application-exit-symbolic"
                shortcut: StandardKey.Quit
                onTriggered: Qt.quit()
            }
        ]
    }

    Component { // <==== Component that instantiates the Kirigami.AboutPage
        id: aboutPage

        Kirigami.AboutPage {
            aboutData: AboutData
            getInvolvedUrl: "https://example.com/tutorial/contribute/"
        }
    }

    ListModel {
        id: kountdownModel
    }

    AddDialog {
        id: addDialog
    }

    pageStack.initialPage: Kirigami.ScrollablePage {
        title: i18nc("@title", "Kountdown")

        actions: [
            Kirigami.Action {
                id: addAction
                icon.name: "list-add-symbolic"
                text: i18nc("@action:button", "Add kountdown")
                onTriggered: addDialog.open()
            }
        ]

        Kirigami.CardsListView {
            id: cardsView
            model: kountdownModel
            delegate: KountdownDelegate {}
        }
    }
}
```

First we import `org.kde.coreaddons`, whose [AboutData](/docs/api/kcoreaddonsqml/qml-org-kde-coreaddons-aboutdata) singleton exposes what we set with [KAboutData::setApplicationData()](/docs/api/kcoreaddons/kaboutdata#setApplicationData) to QML. We then add a [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) to our [global drawer](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer) that takes us to the About page, and create a component with a [Kirigami.AboutPage](/docs/api/kirigami/qml-org-kde-kirigami-aboutpage) in it, whose [aboutData](/docs/api/kirigami/qml-org-kde-kirigami-aboutpage#aboutData-prop) property is that singleton.

For an application whose desktop file name starts with `org.sonicde.` or `org.kde.`, the About page by default shows a "Get Involved" button that links to SonicDE on GitHub. Our tutorial application has such a name, so we set [getInvolvedUrl](/docs/api/kirigami/qml-org-kde-kirigami-aboutpage#getInvolvedUrl-prop) to our own page. The "Donate" button only appears if you set [donateUrl](/docs/api/kirigami/qml-org-kde-kirigami-aboutpage#donateUrl-prop).

### CMakeLists

The root `CMakeLists.txt` file needs `CoreAddons` in its [find_package()](https://cmake.org/cmake/help/latest/command/find_package.html) call, and `src/CMakeLists.txt` needs to link `KF6::CoreAddons`, because of [KAboutData](/docs/api/kcoreaddons/kaboutdata). The tutorial's CMake files [already have both](understanding-cmakelists.md), so nothing needs to change.

## Running the application

If you now run your application and trigger the "About" action in the global drawer, you should see the About page.
