---
title: Connect logic to your QML user interface
description: Connect a back end that does calculations and supplies your user interface with data to display.
source_url: https://develop.kde.org/docs/getting-started/kirigami/advanced-connect_backend/
source_authors: [Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the complete project built against SonicDE's frameworks and run, plus a test build that opens the new page and changes the property; Qt 6.11 qqmlintegration.h documentation"
---

# Connect logic to your QML user interface

To integrate logic into the application, we need C++ back-end classes that do the important calculations. Writing logic in the QML files is discouraged, so move as much as possible to the back end, and use QML only to display the user interface.

We use the code from [Using separate files in a C++ project](separate-files.md) as our base.

## Project structure

```
kirigami-tutorial/
├── CMakeLists.txt
├── org.kde.tutorial.desktop
└── src/
    ├── CMakeLists.txt
    ├── main.cpp
    ├── Main.qml ----------------------- # Modified
    └── components/
        ├── CMakeLists.txt ------------- # Modified
        ├── AddDialog.qml
        ├── KountdownDelegate.qml
        ├── ExposePage.qml ------------- # New
        ├── backend.h ------------------ # New
        └── backend.cpp ---------------- # New
```

## Changes to existing code

### src/components/backend.h

First, create the header file with the code exposed to QML, namely the `Backend` type:

```cpp
#pragma once

#include <QObject>
#include <qqmlintegration.h>

class Backend : public QObject
{
    Q_OBJECT
    QML_ELEMENT
    QML_SINGLETON

public:
    explicit Backend(QObject *parent = nullptr);
};
```

Two things are needed to expose C++ code to QML. One of them is simply the [QML_ELEMENT](https://doc.qt.io/qt-6/qqmlintegration-h.html#QML_ELEMENT) macro, available in the `<qqmlintegration.h>` header.

The back end is created as a singleton, which means it is created only once and exists for the whole lifetime of the application. For this we use the [QML_SINGLETON](https://doc.qt.io/qt-6/qqmlintegration-h.html#QML_SINGLETON) macro.

### src/components/backend.cpp

Add the initial code for the constructor to `backend.cpp`:

```cpp
#include "backend.h"

Backend::Backend(QObject *parent)
    : QObject(parent)
{}
```

### src/components/ExposePage.qml

From now on, QML knows the back end as the `Backend` QML type. It is in a module called `org.kde.tutorial.components`.

So just by adding the import to a QML file, you can use the code exposed from C++:

```qml
import org.kde.tutorial.components
```

To start from a clean slate within the existing application code, create a new QML component containing an empty page:

```qml
import org.kde.kirigami as Kirigami
import org.kde.tutorial.components

Kirigami.Page {
    title: "Exposing to QML Tutorial"
    // ...
}
```

### src/Main.qml

To actually show the new page, let's add a menu option that [pushes the new page](page-row-and-page-stack.md) to the application, so we can test it easily.

For this we use a new [Kirigami.Action](actions-based-components.md) together with [Qt.createComponent()](https://doc.qt.io/qt-6/qtqml-javascript-dynamicobjectcreation.html) to create the page on the fly:

```qml
    globalDrawer: Kirigami.GlobalDrawer {
        isMenu: true
        actions: [
            Kirigami.Action {
                text: i18n("Exposing to QML")
                icon.name: "start-here-sonicde"
                onTriggered: pageStack.push(Qt.createComponent("org.kde.tutorial.components", "ExposePage"))
            },
            Kirigami.Action {
                text: i18n("Quit")
                icon.name: "application-exit-symbolic"
                shortcut: StandardKey.Quit
                onTriggered: Qt.quit()
            }
        ]
    }
```

### src/components/CMakeLists.txt

Lastly, add the new `backend.h`, `backend.cpp` and `ExposePage.qml` to CMake:

```cmake
add_library(kirigami-hello-components)

ecm_add_qml_module(kirigami-hello-components
    URI "org.kde.tutorial.components"
    GENERATE_PLUGIN_SOURCE
)

ecm_target_qml_sources(kirigami-hello-components
    SOURCES
    AddDialog.qml
    KountdownDelegate.qml
    ExposePage.qml
)

target_sources(kirigami-hello-components
    PRIVATE
    backend.cpp backend.h
)

ecm_finalize_qml_module(kirigami-hello-components)

install(TARGETS kirigami-hello-components ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})
```

Adding the files to an existing QML module in CMake is the second part of exposing code to QML.

The QML module must have been created with either `ecm_add_qml_module()` or [qt_add_qml_module()](https://doc.qt.io/qt-6/qt-add-qml-module.html), as they are required for [declarative registration](https://doc.qt.io/qt-6/qtqml-cppintegration-definetypes.html).

You should now be able to build and install the project with [the same steps as before](setup-cpp.md#building-and-installing-the-application).

## Making it functional

### src/components/backend.h

The class that will hold the logic is now connected to the application, but it doesn't do anything yet. To change that, let's add a property to the class. Properties are much more than a simple variable: they can inform the user interface about changes so it can update the right areas.

Right under the `QML_SINGLETON` macro, add a new [Q_PROPERTY](https://doc.qt.io/qt-6/qobject.html#Q_PROPERTY):

```cpp
Q_PROPERTY(QString introductionText READ introductionText WRITE setIntroductionText NOTIFY introductionTextChanged)
```

This may seem like a lot of code just to read and write some data from the back end. But a closer look shows that reading the property from the user interface can already run some logic, and so can writing it. Here, it automatically informs the front end and back end of changes.

Reading and writing are based on [getter and setter functions](https://www.w3schools.com/cpp/cpp_encapsulation.asp). Add a new private attribute to your class to hold the data, plus the getter and setter functions.

Add a new private section with the following:

```cpp
private:
    QString m_introductionText = QStringLiteral("Hello World!");
```

And add the following to the existing public section:

```cpp
public:
    QString introductionText() const;
    void setIntroductionText(const QString &introductionText);
    Q_SIGNAL void introductionTextChanged();
```

The first function is the getter, the second the setter, and the third a signal emitted when the property changes. They match the READ, WRITE and NOTIFY parts of the `Q_PROPERTY` above.

The result should look like this:

```cpp
#pragma once

#include <QObject>
#include <qqmlintegration.h>

class Backend : public QObject
{
    Q_OBJECT
    QML_ELEMENT
    QML_SINGLETON
    Q_PROPERTY(QString introductionText READ introductionText WRITE setIntroductionText NOTIFY introductionTextChanged)
public:
    explicit Backend(QObject *parent = nullptr);
    QString introductionText() const;
    void setIntroductionText(const QString &introductionText);
    Q_SIGNAL void introductionTextChanged();
private:
    QString m_introductionText = QStringLiteral("Hello World!");
};
```

### src/components/backend.cpp

The signal needs no implementation in `backend.cpp`, since it does nothing more than being emitted, but the getter and setter need implementations like these:

```cpp
#include "backend.h"

Backend::Backend(QObject *parent)
    : QObject(parent)
{}

QString Backend::introductionText() const
{
    return m_introductionText;
}

void Backend::setIntroductionText(const QString &introductionText)
{
    m_introductionText = introductionText;
    Q_EMIT introductionTextChanged();
}
```

When the setter is called, it emits the signal and so informs the user interface and back end of the change.

### src/components/ExposePage.qml

To display the text, add a [Kirigami.Heading](/docs/api/kirigami/qml-org-kde-kirigami-heading) to `src/components/ExposePage.qml`, under the [title](https://doc.qt.io/qt-6/qml-qtquick-controls-page.html#title-prop) property of the [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page) component we added.

The resulting file looks like this:

```qml
import org.kde.kirigami as Kirigami
import org.kde.tutorial.components

Kirigami.Page {
    title: "Exposing to QML Tutorial"
    Kirigami.Heading {
        anchors.centerIn: parent
        text: Backend.introductionText
    }
}
```

## Our app so far

Existing code:

<details>
<summary>CMakeLists.txt</summary>

```cmake
cmake_minimum_required(VERSION 3.20)
project(kirigami-tutorial)

find_package(ECM 6.0.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH})

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)
include(ECMFindQmlModule)
include(ECMQmlModule)

find_package(Qt6 REQUIRED COMPONENTS
    Core
    Quick
    Test
    Gui
    QuickControls2
    Widgets
)

find_package(KF6 REQUIRED COMPONENTS
    Kirigami
    I18n
    CoreAddons
    QQC2DesktopStyle
    IconThemes
)

ecm_find_qmlmodule(org.kde.kirigami REQUIRED)

add_subdirectory(src)

install(PROGRAMS org.kde.tutorial.desktop DESTINATION ${KDE_INSTALL_APPDIR})

feature_summary(WHAT ALL INCLUDE_QUIET_PACKAGES FATAL_ON_MISSING_REQUIRED_PACKAGES)
```

</details>

<details>
<summary>src/main.cpp</summary>

```cpp
#include <QApplication>
#include <QQmlApplicationEngine>
#include <QtQml>
#include <QUrl>
#include <QQuickStyle>
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

    QQmlApplicationEngine engine;

    KLocalization::setupLocalizedContext(&engine);
    engine.loadFromModule("org.kde.tutorial", "Main");

    if (engine.rootObjects().isEmpty()) {
        return -1;
    }

    return app.exec();
}
```

</details>

<details>
<summary>src/CMakeLists.txt</summary>

```cmake
add_executable(kirigami-hello)

ecm_add_qml_module(kirigami-hello
    URI
    org.kde.tutorial
)

target_sources(kirigami-hello
    PRIVATE
    main.cpp
)

ecm_target_qml_sources(kirigami-hello
    SOURCES
    Main.qml
)

target_link_libraries(kirigami-hello
    PRIVATE
    Qt6::Quick
    Qt6::Qml
    Qt6::Gui
    Qt6::QuickControls2
    Qt6::Widgets
    KF6::I18n
    KF6::I18nQml
    KF6::CoreAddons
    KF6::IconThemes
    kirigami-hello-components
)

install(TARGETS kirigami-hello ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})

add_subdirectory(components)
```

</details>

<details>
<summary>src/components/KountdownDelegate.qml</summary>

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

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
                level: 1
                text: i18n("%1 days", Math.round((date-Date.now())/86400000))
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
                text: i18n("Edit")
            }
        }
    }
}
```

</details>

<details>
<summary>src/components/AddDialog.qml</summary>

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.Dialog {
    id: addDialog
    title: i18nc("@title:window", "Add kountdown")
    standardButtons: Kirigami.Dialog.Ok | Kirigami.Dialog.Cancel
    padding: Kirigami.Units.largeSpacing
    preferredWidth: Kirigami.Units.gridUnit * 20

    Kirigami.FormLayout {
        Controls.TextField {
            id: nameField
            Kirigami.FormData.label: i18nc("@label:textbox", "Name*:")
            onAccepted: descriptionField.forceActiveFocus()
        }
        Controls.TextField {
            id: descriptionField
            Kirigami.FormData.label: i18nc("@label:textbox", "Description:")
            onAccepted: dateField.forceActiveFocus()
        }
        Controls.TextField {
            id: dateField
            Kirigami.FormData.label: i18nc("@label:textbox", "ISO Date*:")
            inputMask: "D999-99-99"
            onAccepted: addDialog.accepted()
        }
        Controls.Label {
            text: "* = required fields"
        }
    }
    Component.onCompleted: {
        const button = standardButton(Kirigami.Dialog.Ok);
        button.enabled = Qt.binding( () => requiredFieldsFilled() );
    }
    onAccepted: {
        if (!addDialog.requiredFieldsFilled()) return;
        appendDataToModel();
        clearFieldsAndClose();
    }
    function requiredFieldsFilled() {
        return (nameField.text !== "" && dateField.acceptableInput);
    }
    function appendDataToModel() {
        kountdownModel.append({
            name: nameField.text,
            description: descriptionField.text,
            date: new Date(dateField.text)
        });
    }
    function clearFieldsAndClose() {
        nameField.text = ""
        descriptionField.text = ""
        dateField.text = ""
        addDialog.close();
    }
}
```

</details>

Code written or changed on this page:

<details>
<summary>src/Main.qml</summary>

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.tutorial.components

Kirigami.ApplicationWindow {
    id: root

    width: 600
    height: 400

    title: i18nc("@title:window", "Day Kountdown")

    globalDrawer: Kirigami.GlobalDrawer {
        isMenu: true
        actions: [
            Kirigami.Action {
                text: i18n("Exposing to QML")
                icon.name: "start-here-sonicde"
                onTriggered: pageStack.push(Qt.createComponent("org.kde.tutorial.components", "ExposePage"))
            },
            Kirigami.Action {
                text: i18n("Quit")
                icon.name: "application-exit-symbolic"
                shortcut: StandardKey.Quit
                onTriggered: Qt.quit()
            }
        ]
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

</details>

<details>
<summary>src/components/CMakeLists.txt</summary>

```cmake
add_library(kirigami-hello-components)

ecm_add_qml_module(kirigami-hello-components
    URI "org.kde.tutorial.components"
    GENERATE_PLUGIN_SOURCE
)

ecm_target_qml_sources(kirigami-hello-components
    SOURCES
    AddDialog.qml
    KountdownDelegate.qml
    ExposePage.qml
)

target_sources(kirigami-hello-components
    PRIVATE
    backend.cpp backend.h
)

ecm_finalize_qml_module(kirigami-hello-components)

install(TARGETS kirigami-hello-components ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})
```

</details>

<details>
<summary>src/components/backend.h</summary>

```cpp
#pragma once

#include <QObject>
#include <qqmlintegration.h>

class Backend : public QObject
{
    Q_OBJECT
    QML_ELEMENT
    QML_SINGLETON
    Q_PROPERTY(QString introductionText READ introductionText WRITE setIntroductionText NOTIFY introductionTextChanged)
public:
    explicit Backend(QObject *parent = nullptr);
    QString introductionText() const;
    void setIntroductionText(const QString &introductionText);
    Q_SIGNAL void introductionTextChanged();
private:
    QString m_introductionText = QStringLiteral("Hello World!");
};
```

</details>

<details>
<summary>src/components/backend.cpp</summary>

```cpp
#include "backend.h"

Backend::Backend(QObject *parent)
    : QObject(parent)
{}

QString Backend::introductionText() const
{
    return m_introductionText;
}

void Backend::setIntroductionText(const QString &introductionText)
{
    m_introductionText = introductionText;
    Q_EMIT introductionTextChanged();
}
```

</details>

<details>
<summary>src/components/ExposePage.qml</summary>

```qml
import org.kde.kirigami as Kirigami
import org.kde.tutorial.components

Kirigami.Page {
    title: "Exposing to QML Tutorial"
    Kirigami.Heading {
        anchors.centerIn: parent
        text: Backend.introductionText
    }
}
```

</details>

Now [build](setup-cpp.md#building-and-installing-the-application) and start your program again. Open the new "Exposing to QML" entry from the menu: the new page shows a centered heading saying "Hello World!".

Congratulations, you learned:

- How to register back-end types with QML
- How to add new elements to the QML file
- How to create new QObject subclasses
- How to add properties, and what they do
- What signals are

To learn more about the integration between QML and C++, read the [Qt documentation](https://doc.qt.io/qt-6/qtqml-cppintegration-definetypes.html).
