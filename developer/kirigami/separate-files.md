---
title: Using separate files in a C++ project
description: Split unwieldy code into separate files.
source_url: https://develop.kde.org/docs/getting-started/kirigami/introduction-separatefiles/
source_authors: [Antti Savolainen, Carl Schwan, Claudio Cambra, Martin Frueh, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-cmake-modules (ECMQmlModule, KDECMakeSettings RPATH), sonic-frameworks-quick-ui; the three-file project below was built against SonicDE's frameworks and loaded offscreen without QML errors
---

# Using separate files in a C++ project

## Why and how

For the first time, we split some of our components into QML files of their own. If we keep adding to `Main.qml`, it soon becomes hard to tell what does what.

In this step we split `Main.qml` into `Main.qml`, `AddDialog.qml` and `KountdownDelegate.qml`.

Even with code spread over several QML files, real projects can end up with very many files. A common solution is to sort them into folders. We look briefly at three common approaches and use one of them:

- keeping the QML files with the C++ files;
- keeping the QML files in another folder, in the same QML module;
- keeping the QML files in another folder, in a separate QML module.

After the split, each file has its own concern ([separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)) and [implementation details are abstracted](https://en.wikipedia.org/wiki/Abstraction_(computer_science)) away, which makes the code easier to read.

### QML files with the C++ files

The project's QML files stay with the C++ files in `src/`:

```text
kirigami-tutorial/
├── CMakeLists.txt
├── org.kde.tutorial.desktop
└── src/
    ├── CMakeLists.txt
    ├── main.cpp
    ├── Main.qml
    ├── AddDialog.qml
    └── KountdownDelegate.qml
```

That is what we did so far: you just keep adding QML files to `kirigami-tutorial/src/CMakeLists.txt`. There is no separation at all, and once the project has more than a few QML files (and C++ files that create types for QML), the folder becomes crowded.

### QML files in another folder, same module

All QML files go in a folder of their own, usually `src/qml/`:

```text
kirigami-tutorial/
├── CMakeLists.txt
├── org.kde.tutorial.desktop
└── src/
    ├── CMakeLists.txt
    ├── main.cpp
    └── qml/
        ├── Main.qml
        ├── AddDialog.qml
        └── KountdownDelegate.qml
```

This structure is very common, mostly because it needs no extra `CMakeLists.txt` and no separate module for `src/qml/`. The files are in a folder of their own, but you still add them in `kirigami-tutorial/src/CMakeLists.txt`, and they all belong to the same QML module as `Main.qml`.

Once a project has more than a dozen QML files, `src/` stays tidy but `src/CMakeLists.txt` gets crowded, and it becomes hard to tell ordinary C++ files from C++ files with types for QML.

It also breaks locality: the description of the dependencies is no longer next to the dependencies themselves.

### QML files in another folder, separate module

All QML files go in a folder with its own `CMakeLists.txt` and its own QML module:

```text
kirigami-tutorial/
├── CMakeLists.txt
├── org.kde.tutorial.desktop
└── src/
    ├── CMakeLists.txt
    ├── main.cpp
    ├── Main.qml
    └── components/
        ├── CMakeLists.txt
        ├── AddDialog.qml
        └── KountdownDelegate.qml
```

This structure is less common and needs an extra `CMakeLists.txt`, but it is the most flexible. We call the folder "components", since we turn parts of `Main.qml` into two new QML components, and describe them in `kirigami-tutorial/src/components/CMakeLists.txt`. `Main.qml` stays in `src/`, so the program still uses it at start, as before.

Later you could add more folders of QML files grouped by purpose, such as "models" and "settings", and keep C++ files with types for QML (models, for example) next to the QML files that use them.

This tutorial uses this structure.

## Preparing CMake for the new files

First, create `kirigami-tutorial/src/components/CMakeLists.txt`:

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
)

ecm_finalize_qml_module(kirigami-hello-components)

install(TARGETS kirigami-hello-components ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})
```

It creates a new target, `kirigami-hello-components`, and turns it into a QML module with the import name `org.kde.tutorial.components` with `ecm_add_qml_module()` (from ECM's `ECMQmlModule`), then adds the QML files.

The target is separate from the program, so it is a separate QML module. That needs two more things: `GENERATE_PLUGIN_SOURCE`, which generates the code for its Qt plugin, and `ecm_finalize_qml_module()`, which finishes it and installs it (by default into `KDE_INSTALL_QMLDIR`, in a folder named after the URI). Then we install the library as in the previous steps.

We used [add_library()](https://cmake.org/cmake/help/latest/command/add_library.html) so that we can link `kirigami-hello-components` to the program in the [target_link_libraries()](https://cmake.org/cmake/help/latest/command/target_link_libraries.html) call of `kirigami-tutorial/src/CMakeLists.txt`:

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

[add_subdirectory()](https://cmake.org/cmake/help/latest/command/add_subdirectory.html) makes CMake read `kirigami-tutorial/src/components/`. (`KF6::I18nQml` is there because our `main.cpp` sets up `i18n()` for QML with `KLocalization::setupLocalizedContext()`; see [Setup with C++](setup-cpp.md#maincpp).)

So far `Main.qml` didn't need to import `org.kde.tutorial`: it is the program's entry point and runs anyway. Our components are now in a separate QML module, so `kirigami-tutorial/src/Main.qml` needs a new import, the URI defined above, `org.kde.tutorial.components`:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.tutorial.components

// The rest of the code...
```

And we are ready to go.

## Splitting Main.qml

The custom delegate with `id: kountdownDelegate` from the [previous step](dialog.md#our-application-so-far) can be split off completely, because it is already wrapped in a QML [Component](https://doc.qt.io/qt-6/qml-qtqml-component.html). A Component lets us define it without creating it; a separate QML file works the same way.

So once the code is in its own file, there's no point keeping it wrapped in a Component: we move just the [Kirigami.AbstractCard](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard) into the file. This is `KountdownDelegate.qml`:

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

The dialog with `id: addDialog` isn't wrapped in a Component, and isn't visible by default, so its code can be copied as it is into `AddDialog.qml`:

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

With the code split, `Main.qml` becomes much shorter:

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

Now there are two more QML files, `AddDialog.qml` and `KountdownDelegate.qml`, and `Main.qml` has to use them. It does that by *instantiating* them: `AddDialog.qml` becomes `AddDialog {}` (with `id: addDialog`, which the action opens), and `KountdownDelegate.qml` becomes `KountdownDelegate {}`, the list view's delegate.

Most of the components you have seen written with an uppercase name followed by braces were instantiations of a QML component. That is why our new QML files must start with an uppercase letter.

Build the project and run it: the window behaves exactly as before, but the code is split into separate parts, which makes it much easier to manage.
