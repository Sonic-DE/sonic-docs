---
title: FormCard About pages
description: Learn to create About pages to credit your application.
source_url: https://develop.kde.org/docs/getting-started/kirigami/addons-about/
source_authors: [Melissa Autumn, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-quick-ui-addons source (AboutKDEPage.qml, AboutKDE.qml, AboutPage.qml); the project built and each page opened in a test build against the staged libraries, plus the About links' defaults for org.sonicde, org.kde and other application ids."
---

# FormCard About pages

Some Kirigami Addons components let you credit your work and the work of other contributors to your project, and mention the frameworks your application uses: [AboutKDEPage](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-aboutkdepage) and [AboutPage](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-aboutpage).

## About SonicDE

Each button we created in the [previous step](addons-introduction.md) should open a new page. You add a page by instantiating it as a [Component](https://doc.qt.io/qt-6/qml-qtqml-component.html) and calling `pageStack.layers.push()` from its button in `Main.qml`:

```qml
import QtQuick
import QtQuick.Layouts

import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.formcard as FormCard

Kirigami.ApplicationWindow {
    id: root
    width: 600
    height: 700

    Component {
        id: aboutsonicde
        FormCard.AboutKDEPage {}
    }

    pageStack.initialPage: Kirigami.ScrollablePage {
        ColumnLayout {
            FormCard.FormCard {
                FormCard.FormButtonDelegate {
                    id: aboutSonicDEButton
                    icon.name: "start-here-sonicde"
                    text: i18n("About SonicDE Page")
                    onClicked: root.pageStack.layers.push(aboutsonicde)
                }

                FormCard.FormButtonDelegate {
                    id: aboutPageButton
                    icon.name: "applications-utilities"
                    text: i18n("About Addons Example")
                }

                FormCard.FormButtonDelegate {
                    id: settingsButton
                    icon.name: "settings-configure"
                    text: i18n("Single Settings Page")
                }
            }
        }
    }
}
```

That's really it! All it takes is instantiating `FormCard.AboutKDEPage`. The type keeps its upstream name, but on SonicDE it shows an "About SonicDE" page: what SonicDE is, how to report bugs, and how to get involved. (`FormCard.AboutKDE` is a deprecated name for the same page, and logs a warning.)

## About page

The application's [AboutPage](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-aboutpage) is just as simple to use. By default it shows the data set with `KAboutData::setApplicationData(aboutData);` in `main.cpp`, so for a simple About page, add the following to your `Main.qml`:

```qml
    Component {
        id: aboutpage
        FormCard.AboutPage {}
    }
```

and open it from its button:

```qml
                FormCard.FormButtonDelegate {
                    id: aboutPageButton
                    icon.name: "applications-utilities"
                    text: i18n("About Addons Example")
                    onClicked: root.pageStack.layers.push(aboutpage)
                }
```

> **Note:** If your application's desktop file name starts with `org.sonicde.` or `org.kde.`, the page's "Get Involved" button links to SonicDE on GitHub, unless you set [getInvolvedUrl](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-aboutpage#getInvolvedUrl-prop) yourself. The "Donate" button only appears if you set [donateUrl](/docs/api/kirigamiaddonsformcard/qml-org-kde-kirigamiaddons-formcard-aboutpage#donateUrl-prop). See the [Kirigami About page](about-page.md).

### Using JSON instead of KAboutData

Instead of letting your About page get its information from [KAboutData](/docs/api/kcoreaddons/kaboutdata), you can pass a JSON object directly. For your application icon to show up, you still need [QApplication::setWindowIcon()](https://doc.qt.io/qt-6/qguiapplication.html#windowIcon-prop) in your `main.cpp`, or a `programLogo` key.

Create a `MyAboutPage.qml` like this:

```qml
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.AboutPage {
    title: i18nc("@action:button", "About")
    aboutData: {
        "displayName" : "Addons Example",
        "productName" : "",
        "componentName" : "addonsexample",
        "shortDescription" : "This program shows how to use AboutPage",
        "homepage" : "https://example.com/addonsexample/",
        "bugAddress" : "",
        "version" : "1.0",
        "otherText" : "Optional text shown in the About",
        "authors" : [
            {
                "name" : "John Doe",
                "task" : "Maintainer",
                "emailAddress" : "",
                "webAddress" : "",
                "ocsUsername" : ""
            }
        ],
        "credits" : [],
        "translators" : [],
        "licenses" : [
            {
                "name" : "GPL v3",
                "text" : "Long license text goes here",
                "spdx" : "GPL-3.0"
            }
        ],
        "copyrightStatement" : "© 2023",
        "releases" : [],
        "desktopFileName" : ""
    }

}
```

Then add the file to `ecm_target_qml_sources()` in `CMakeLists.txt` and use the new page in your `Main.qml`:

```qml
    Component {
        id: aboutpage
        MyAboutPage {}
    }
```

The main JSON object contains the keys `displayName`, `productName`, `homepage` and so on. The keys `authors`, `credits`, `translators` and `licenses` can each take an array of objects. The objects in `authors`, `credits` and `translators` share the same keys, and each is displayed in its own section, while `licenses` has the keys `name`, `text` and `spdx` for each license, since a project often has several licenses.

Your application should set at least these keys so it has no empty fields: `displayName`, `version`, `shortDescription`, `homepage`, `copyrightStatement` and `authors`. Also set `releases`, even to an empty array, or the page logs a warning. You are encouraged to fill in as many keys as possible.
