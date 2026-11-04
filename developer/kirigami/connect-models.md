---
title: Connect C++ models to your QML user interface
description: Data from the C++ back end to the QML front end.
source_url: https://develop.kde.org/docs/getting-started/kirigami/advanced-connect_models/
source_authors: [Jonah Brüchert, Kuneho Cottonears, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the complete project built against SonicDE's frameworks and run (test build edits, adds and deletes through the QML page); the model run under QAbstractItemModelTester; Qt 6.11 QAbstractItemModel documentation"
---

# Connect C++ models to your QML user interface

As shown in the [previous page](connect-backend.md), you can connect C++ code to QML by creating a class that QML treats as just another component. However, you may want to represent more complicated data, such as data that needs to act as a custom [ListModel](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html) or that needs to be delegated from a [Repeater](https://doc.qt.io/qt-6/qml-qtquick-repeater.html).

We can create our own [models](https://doc.qt.io/qt-6/qabstractlistmodel.html) on the C++ side, and declare how the data of that model is represented in the QML front end.

It is strongly recommended to read the [List views](listview-components.md) page before this one.

The code for this page is based on the previous page, [Connect logic to your QML user interface](connect-backend.md).

## Project structure

```
kirigami-tutorial/
├── CMakeLists.txt --------------------- # Modified
├── org.kde.tutorial.desktop
└── src/
    ├── CMakeLists.txt
    ├── main.cpp
    ├── Main.qml ----------------------- # Modified
    └── components/
        ├── CMakeLists.txt ------------- # Modified
        ├── AddDialog.qml
        ├── KountdownDelegate.qml
        ├── ExposePage.qml
        ├── ModelsPage.qml ------------- # New
        ├── backend.h
        ├── backend.cpp
        ├── model.h -------------------- # New
        └── model.cpp ------------------ # New
```

## Creating a new page for the models tutorial

Before anything else, let's add a new page to our QML code.

First, in `src/Main.qml`, add the following action to the global drawer:

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
                text: i18n("C++ models in QML")
                icon.name: "start-here-sonicde"
                onTriggered: pageStack.push(Qt.createComponent("org.kde.tutorial.components", "ModelsPage"))
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

Then create a new `src/components/ModelsPage.qml` with the following contents:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ScrollablePage {
    title: "C++ models in QML"
    // ...
}
```

And finally add it to `src/components/CMakeLists.txt`:

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
    ModelsPage.qml
)

target_sources(kirigami-hello-components
    PRIVATE
    backend.cpp backend.h
)

ecm_finalize_qml_module(kirigami-hello-components)

install(TARGETS kirigami-hello-components ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})
```

This page is the canvas for this tutorial.

## Using raw strings

To make it easier to follow how the model is filled, we turn off a feature that applications using extra-cmake-modules (ECM) get by default: [QT_NO_CAST_FROM_ASCII](https://doc.qt.io/qt-6/qstring.html#QT_NO_CAST_FROM_ASCII), which disallows implicit conversions from plain C strings. This saves us from writing [QStringLiteral()](https://doc.qt.io/qt-6/qstring.html#QStringLiteral) every time a string appears in our C++ code, which helps in the upcoming header file.

In the root `CMakeLists.txt` file, add the `remove_definitions()` line:

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
remove_definitions(-DQT_NO_CAST_FROM_ASCII)

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

Disabling this definition is for teaching purposes *only*. Production code should use QStringLiteral() or the [Qt string literals namespace](https://doc.qt.io/qt-6/qt-literals-stringliterals.html) instead where possible.

## Preparing the class

We will create a class that contains a [QMap](https://doc.qt.io/qt-6/qmap.html), with a [QString](https://doc.qt.io/qt-6/qstring.html) as key and [QStringList](https://doc.qt.io/qt-6/qstringlist.html) objects as values. The front end can read and display the keys and values, and the class is as simple to use as a one-dimensional array. It should look similar to a QML ListModel.

To do this, we create a class that inherits from [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html). Let's also add some data to the QMap. These declarations go in `model.h`.

Create two new files, `src/components/model.h` and `src/components/model.cpp`, and add them to `src/components/CMakeLists.txt`:

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
    ModelsPage.qml
)

target_sources(kirigami-hello-components
    PRIVATE
    backend.cpp backend.h
    model.cpp model.h
)

ecm_finalize_qml_module(kirigami-hello-components)

install(TARGETS kirigami-hello-components ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})
```

Add the following as the initial contents of `src/components/model.h`:

```cpp
#pragma once

#include <QAbstractListModel>
#include <qqmlintegration.h>

class Model : public QAbstractListModel {
    Q_OBJECT
    QML_ELEMENT
public:

private:
    QMap<QString, QStringList> m_list = {
            {"Feline", {"Tigress",   "Waai Fuu"}},
            {"Fox",    {"Carmelita", "Diane", "Krystal"}},
            {"Goat",   {"Sybil",     "Toriel"}}
    };
};
```

Of course, we can't just display this class as it is. We also need to tell QML how to represent the data in the class. We do this by overriding three essential virtual functions:

- [rowCount()](https://doc.qt.io/qt-6/qabstractitemmodel.html#rowCount): think of this function as a way to tell QML how many items the model should present.
- [roleNames()](https://doc.qt.io/qt-6/qabstractitemmodel.html#roleNames): you can think of role names as property names attached to data in QML. This function creates those roles.
- [data()](https://doc.qt.io/qt-6/qabstractitemmodel.html#data): this function is called to retrieve the data that corresponds to the role names from the model.

The custom role names created by `roleNames()` are only usable while a model is being delegated, not outside it. See [Models and Views](https://doc.qt.io/qt-6/qtquick-modelviewsdata-modelview.html#models).

Technically, models in Qt are tables, with rows and columns. So overriding `rowCount()` tells Qt how many rows a model has. Since we only deal with a one-dimensional array here, you can think of "rows" as the "number of elements".

### Overriding and implementing rowCount()

Let's override the function in the `src/components/model.h` header file. The [rowCount()](https://doc.qt.io/qt-6/qabstractitemmodel.html#rowCount) function has its own parameter, but this example doesn't use it, so it doesn't need a name.

```cpp
#pragma once

#include <QAbstractListModel>
#include <qqmlintegration.h>

class Model : public QAbstractListModel {
    Q_OBJECT
    QML_ELEMENT
public:
    int rowCount(const QModelIndex &) const override;

private:
    QMap<QString, QStringList> m_list = {
            {"Feline", {"Tigress",   "Waai Fuu"}},
            {"Fox",    {"Carmelita", "Diane", "Krystal"}},
            {"Goat",   {"Sybil",     "Toriel"}}
    };
};
```

Then declare how many rows the model has in `src/components/model.cpp`:

```cpp
#include "model.h"

int Model::rowCount(const QModelIndex &) const {
    return m_list.count();
}
```

### Overriding and implementing roleNames()

Before overriding `roleNames()`, we need to declare the roles on the C++ side with a public enum. These enum values are passed to `data()` every time QML accesses the corresponding role, so we can make `data()` return what we want.

Let's create the enum for the roles in `src/components/model.h`, where each value is a role on the C++ side:

```cpp
#pragma once

#include <QAbstractListModel>
#include <qqmlintegration.h>

class Model : public QAbstractListModel {
    Q_OBJECT
    QML_ELEMENT
public:
    enum Roles {
        SpeciesRole = Qt::UserRole,
        CharactersRole
    };

    QHash<int, QByteArray> roleNames() const override;
    int rowCount(const QModelIndex &) const override;

private:
    QMap<QString, QStringList> m_list = {
            {"Feline", {"Tigress",   "Waai Fuu"}},
            {"Fox",    {"Carmelita", "Diane", "Krystal"}},
            {"Goat",   {"Sybil",     "Toriel"}}
    };
};
```

With that settled, we can finally create the roles on the QML side, with a [QHash](https://doc.qt.io/qt-6/qhash.html) whose keys are the enum values, paired with [QByteArrays](https://doc.qt.io/qt-6/qbytearray.html). This goes in `src/components/model.cpp`. The text in the QByteArray is what the actual QML code uses.

```cpp
#include "model.h"

int Model::rowCount(const QModelIndex &) const {
    return m_list.count();
}

QHash<int, QByteArray> Model::roleNames() const {
    return {
        {SpeciesRole,   "species"},
        {CharactersRole, "characters"}
    };
}
```

In our example model, the role "species" retrieves the QString keys "Feline", "Fox" and "Goat", each in a separate delegate. The same works for the QStringList values, the list of character names.

### Overriding and implementing data()

Two parameters are passed to `data()`: `index` and `role`. The `index` is the position of the data in the model. As stated before, QML uses `role` to get specific data back when it accesses a role.

In `data()`, a switch statement returns the appropriate data and data type for the role, which works because `data()` returns a [QVariant](https://doc.qt.io/qt-6/qvariant.html). We still need to find the right position of the data, though. In the example below, a new iterator variable is set to the beginning of the list plus the row of the index, and the data that the iterator points to is returned.

We can't just return whatever data we want, though. We may be binding data to a property of an incompatible type, such as a QStringList to a QString, so you may have to convert data to display it properly. For this, we create a new private, static function named `formatList()`, which joins the list into one string with [QStringList::join()](https://doc.qt.io/qt-6/qstringlist.html#join).

This results in the following code in `src/components/model.cpp`:

```cpp
#include "model.h"

int Model::rowCount(const QModelIndex &) const {
    return m_list.count();
}

QHash<int, QByteArray> Model::roleNames() const {
    return {
        {SpeciesRole,   "species"},
        {CharactersRole, "characters"}
    };
}

QVariant Model::data(const QModelIndex &index, int role) const {
    const auto it = std::next(m_list.begin(), index.row());
    switch (role) {
        case SpeciesRole:
            return it.key();
        case CharactersRole:
            return formatList(it.value());
        default:
            return {};
    }
}

QString Model::formatList(const QStringList& list) {
    return list.join(", ");
}
```

And the following code in `src/components/model.h`:

```cpp
#pragma once

#include <QAbstractListModel>
#include <qqmlintegration.h>

class Model : public QAbstractListModel {
    Q_OBJECT
    QML_ELEMENT
public:
    enum Roles {
        SpeciesRole = Qt::UserRole,
        CharactersRole
    };
    int rowCount(const QModelIndex &) const override;
    QHash<int, QByteArray> roleNames() const override;
    QVariant data(const QModelIndex &index, int role) const override;

private:
    QMap<QString, QStringList> m_list = {
        {"Feline", {"Tigress",   "Waai Fuu"}},
        {"Fox",    {"Carmelita", "Diane", "Krystal"}},
        {"Goat",   {"Sybil",     "Toriel"}}
    };
    static QString formatList(const QStringList& list);
};
```

## Class usage in QML

The QML file just contains three [Kirigami.AbstractCard](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard) components, with the key as the header and the value as the content. These cards are created by delegating an AbstractCard with a Repeater, with our custom model as the model. The data is accessed with the word `model`, followed by the roles we declared in `roleNames()`.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ScrollablePage {
    title: "C++ models in QML"
    Model {
        id: customModel
    }
    ColumnLayout {
        anchors.left: parent.left
        anchors.right: parent.right
        Repeater {
            model: customModel
            delegate: Kirigami.AbstractCard {
                header: Kirigami.Heading {
                    text: model.species
                    level: 2
                }
                contentItem: Controls.Label {
                    text: model.characters
                }
            }
        }
    }
}
```

## Data modification

### Editing data with dataChanged() and setData()

You may want to modify data in the model and have the changes reflected in the front end. Every time we change data in the model, we must emit the [dataChanged()](https://doc.qt.io/qt-6/qabstractitemmodel.html#dataChanged) signal, which applies the changes in the front end at the cells given in its arguments. Here we can just use the `index` argument of [setData()](https://doc.qt.io/qt-6/qabstractitemmodel.html#setData).

[setData()](https://doc.qt.io/qt-6/qabstractitemmodel.html#setData) is a virtual function you can override so that modifying the data from the front end automatically changes it in the back end. It has three parameters:

- `index`: the location of the data.
- `value`: the new data.
- `role`: which data of the item to change. When QML code assigns to a role of a delegate's `model`, as our page will do with `model.characters`, `setData()` is called with that role, here `CharactersRole`.

We only accept the characters role, with a value that can be converted to a string. With `index`, we find where the data should be changed to the contents of `value`.

```cpp
#include "model.h"

int Model::rowCount(const QModelIndex &) const {
    return m_list.count();
}

QHash<int, QByteArray> Model::roleNames() const {
    return {
        {SpeciesRole,   "species"},
        {CharactersRole, "characters"}
    };
}

QVariant Model::data(const QModelIndex &index, int role) const {
    const auto it = std::next(m_list.begin(), index.row());
    switch (role) {
        case SpeciesRole:
            return it.key();
        case CharactersRole:
            return formatList(it.value());
        default:
            return {};
    }
}

QString Model::formatList(const QStringList& list) {
    return list.join(", ");
}

bool Model::setData(const QModelIndex &index, const QVariant &value, int role) {
    if (role != CharactersRole || !value.canConvert<QString>()) {
        return false;
    }

    auto it = std::next(m_list.begin(), index.row());
    QString charactersUnformatted = value.toString();
    QStringList characters = charactersUnformatted.split(", ");

    m_list[it.key()] = characters;
    Q_EMIT dataChanged(index, index);

    return true;
}
```

`setData()` doesn't emit [dataChanged()](https://doc.qt.io/qt-6/qabstractitemmodel.html#dataChanged) automatically; that has to be done manually.

With the corresponding addition in `src/components/model.h`:

```cpp
#pragma once

#include <QAbstractListModel>
#include <qqmlintegration.h>

class Model : public QAbstractListModel {
    Q_OBJECT
    QML_ELEMENT
public:
    enum Roles {
        SpeciesRole = Qt::UserRole,
        CharactersRole
    };
    int rowCount(const QModelIndex &) const override;
    QHash<int, QByteArray> roleNames() const override;
    QVariant data(const QModelIndex &index, int role) const override;
    bool setData(const QModelIndex &index, const QVariant &value, int role) override;
private:
    QMap<QString, QStringList> m_list = {
        {"Feline", {"Tigress",   "Waai Fuu"}},
        {"Fox",    {"Carmelita", "Diane", "Krystal"}},
        {"Goat",   {"Sybil",     "Toriel"}}
    };
    static QString formatList(const QStringList& list);
};
```

Let's update the QML code so we can open a prompt for editing the model, with a [Controls.Button](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html) on the cards.

Add the following [Kirigami.PromptDialog](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-promptdialog) to `src/components/ModelsPage.qml`, together with a new edit button:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.tutorial.components

Kirigami.ScrollablePage {
    title: "C++ models in QML"
    Model {
        id: customModel
    }
    ColumnLayout {
        anchors.left: parent.left
        anchors.right: parent.right
        Repeater {
            model: customModel
            delegate: Kirigami.AbstractCard {
                Layout.fillHeight: true
                header: Kirigami.Heading {
                    text: model.species
                    level: 2
                }
                contentItem: Item {
                    implicitWidth: delegateLayout.implicitWidth
                    implicitHeight: delegateLayout.implicitHeight
                    ColumnLayout {
                        id: delegateLayout
                        Controls.Label {
                            text: model.characters
                        }
                        Controls.Button {
                            text: "Edit"
                            onClicked: {
                                editPrompt.text = model.characters;
                                editPrompt.model = model;
                                editPrompt.open();
                            }
                        }
                    }
                }
            }
        }
    }
    Kirigami.PromptDialog {
        id: editPrompt
        property var model
        property alias text: editPromptText.text
        title: "Edit Characters"
        standardButtons: Kirigami.Dialog.Ok | Kirigami.Dialog.Cancel
        onAccepted: {
            const model = editPrompt.model;
            model.characters = editPromptText.text;
            editPrompt.close();
        }
        Controls.TextField {
            id: editPromptText
            onAccepted: editPrompt.accept()
        }
    }
}
```

Now, whenever the values of the model change in the front end, the changes also update the back end.

### Adding rows

We can now modify the data of existing keys in the QMap, which the front end shows as changes to the contents of the AbstractCards. But what if we need to add a new key to the QMap and have it reflected on the QML side? Let's create a new method, callable from QML, to do this.

To make the method visible in QML, we begin its declaration with the [Q_INVOKABLE](https://doc.qt.io/qt-6/qobject.html#Q_INVOKABLE) macro. The method takes a string parameter, the new key in the QMap.

```cpp
#pragma once

#include <QAbstractListModel>
#include <qqmlintegration.h>

class Model : public QAbstractListModel {
    Q_OBJECT
    QML_ELEMENT
public:
    enum Roles {
        SpeciesRole = Qt::UserRole,
        CharactersRole
    };
    int rowCount(const QModelIndex &) const override;
    QHash<int, QByteArray> roleNames() const override;
    QVariant data(const QModelIndex &index, int role) const override;
    Q_INVOKABLE void addSpecies(const QString &species);

private:
    QMap<QString, QStringList> m_list = {
        {"Feline", {"Tigress",   "Waai Fuu"}},
        {"Fox",    {"Carmelita", "Diane", "Krystal"}},
        {"Goat",   {"Sybil",     "Toriel"}}
    };
    static QString formatList(const QStringList& list);
};
```

Inside this method, we need to tell Qt that we want to create more rows in the model. This is done by calling [beginInsertRows()](https://doc.qt.io/qt-6/qabstractitemmodel.html#beginInsertRows) to begin the row insertion, then inserting what we need, and then calling [endInsertRows()](https://doc.qt.io/qt-6/qabstractitemmodel.html#endInsertRows) to end the operation. These two calls inform the views, so no `dataChanged()` is needed.

`beginInsertRows()` first takes a QModelIndex for the parent of the new rows; for a list it is just `QModelIndex()`. Then come the row numbers the first and last new rows will have once inserted. A QMap keeps its keys sorted, so the new key doesn't necessarily end up at the end: its row is where [lowerBound()](https://doc.qt.io/qt-6/qmap.html#lowerBound) finds it, which we turn into a row number with `std::distance()`. If the species is empty or already exists, inserting wouldn't add a row, so we return early.

```cpp
#include "model.h"

int Model::rowCount(const QModelIndex &) const {
    return m_list.count();
}

QHash<int, QByteArray> Model::roleNames() const {
    return {
        {SpeciesRole,   "species"},
        {CharactersRole, "characters"}
    };
}

QVariant Model::data(const QModelIndex &index, int role) const {
    const auto it = std::next(m_list.begin(), index.row());
    switch (role) {
        case SpeciesRole:
            return it.key();
        case CharactersRole:
            return formatList(it.value());
        default:
            return {};
    }
}

QString Model::formatList(const QStringList& list) {
    return list.join(", ");
}

bool Model::setData(const QModelIndex &index, const QVariant &value, int role) {
    if (role != CharactersRole || !value.canConvert<QString>()) {
        return false;
    }

    auto it = std::next(m_list.begin(), index.row());
    QString charactersUnformatted = value.toString();
    QStringList characters = charactersUnformatted.split(", ");

    m_list[it.key()] = characters;
    Q_EMIT dataChanged(index, index);

    return true;
}

void Model::addSpecies(const QString& species) {
    if (species.isEmpty() || m_list.contains(species)) {
        return;
    }
    const int row = std::distance(m_list.begin(), m_list.lowerBound(species));
    beginInsertRows(QModelIndex(), row, row);
    m_list.insert(species, {});
    endInsertRows();
}
```

Let's update the QML code so we can add a new key to the QMap:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.tutorial.components

Kirigami.ScrollablePage {
    title: "C++ models in QML"
    actions: [
        Kirigami.Action {
            icon.name: "list-add-symbolic"
            text: "Add New Species"
            onTriggered: {
                addPrompt.open();
            }
        }
    ]
    Model {
        id: customModel
    }
    ColumnLayout {
    // ...
    }
    Kirigami.PromptDialog {
        id: addPrompt
        title: "Add New Species"
        standardButtons: Kirigami.Dialog.Ok
        onAccepted: {
            customModel.addSpecies(addPromptText.text);
            addPromptText.text = ""; // Clear TextField every time it's done
            addPrompt.close();
        }
        Controls.TextField {
            id: addPromptText
            Layout.fillWidth: true
            onAccepted: addPrompt.accept()
        }
    }
    Kirigami.PromptDialog {
        id: editPrompt
        // ...
    }
}
```

Now there is a new action at the top of the application that opens a prompt for adding a new element, with our own data, to the model.

### Removing rows

Removing rows works like adding them. Let's create another method to call from QML. This time it takes an additional parameter: an integer, the row number. The species name is used to remove the key from the QMap, and the row number to remove the row in the front end, between [beginRemoveRows()](https://doc.qt.io/qt-6/qabstractitemmodel.html#beginRemoveRows) and [endRemoveRows()](https://doc.qt.io/qt-6/qabstractitemmodel.html#endRemoveRows).

Add a new Q_INVOKABLE function named `deleteSpecies()` in `src/components/model.h`:

```cpp
#pragma once

#include <QAbstractListModel>
#include <qqmlintegration.h>

class Model : public QAbstractListModel {
    Q_OBJECT
    QML_ELEMENT
public:
    enum Roles {
        SpeciesRole = Qt::UserRole,
        CharactersRole
    };
    int rowCount(const QModelIndex &) const override;
    QHash<int, QByteArray> roleNames() const override;
    QVariant data(const QModelIndex &index, int role) const override;
    Q_INVOKABLE void addSpecies(const QString &species);
    Q_INVOKABLE void deleteSpecies(const QString &speciesName, const int &rowIndex);

private:
    QMap<QString, QStringList> m_list = {
        {"Feline", {"Tigress",   "Waai Fuu"}},
        {"Fox",    {"Carmelita", "Diane", "Krystal"}},
        {"Goat",   {"Sybil",     "Toriel"}}
    };
    static QString formatList(const QStringList& list);
};
```

With a matching implementation in `src/components/model.cpp`:

```cpp
#include "model.h"

int Model::rowCount(const QModelIndex &) const {
    return m_list.count();
}

QHash<int, QByteArray> Model::roleNames() const {
    return {
        {SpeciesRole,   "species"},
        {CharactersRole, "characters"}
    };
}

QVariant Model::data(const QModelIndex &index, int role) const {
    const auto it = std::next(m_list.begin(), index.row());
    switch (role) {
        case SpeciesRole:
            return it.key();
        case CharactersRole:
            return formatList(it.value());
        default:
            return {};
    }
}

QString Model::formatList(const QStringList& list) {
    return list.join(", ");
}

bool Model::setData(const QModelIndex &index, const QVariant &value, int role) {
    if (role != CharactersRole || !value.canConvert<QString>()) {
        return false;
    }

    auto it = std::next(m_list.begin(), index.row());
    QString charactersUnformatted = value.toString();
    QStringList characters = charactersUnformatted.split(", ");

    m_list[it.key()] = characters;
    Q_EMIT dataChanged(index, index);

    return true;
}

void Model::addSpecies(const QString& species) {
    if (species.isEmpty() || m_list.contains(species)) {
        return;
    }
    const int row = std::distance(m_list.begin(), m_list.lowerBound(species));
    beginInsertRows(QModelIndex(), row, row);
    m_list.insert(species, {});
    endInsertRows();
}

void Model::deleteSpecies(const QString &speciesName, const int& rowIndex) {
    beginRemoveRows(QModelIndex(), rowIndex, rowIndex);
    m_list.remove(speciesName);
    endRemoveRows();
}
```

Now let's update the application so a "Delete" button appears in a RowLayout next to the edit button inside our AbstractCard, and connect it to our delete method:

```qml
        Repeater {
            model: customModel
            delegate: Kirigami.AbstractCard {
                Layout.fillHeight: true
                header: Kirigami.Heading {
                    text: model.species
                    level: 2
                }
                contentItem: Item {
                    implicitWidth: delegateLayout.implicitWidth
                    implicitHeight: delegateLayout.implicitHeight
                    ColumnLayout {
                        id: delegateLayout
                        Controls.Label {
                            text: model.characters
                        }
                        RowLayout {
                            Layout.fillWidth: true
                            Controls.Button {
                                text: "Edit"
                                onClicked: {
                                    editPrompt.text = model.characters;
                                    editPrompt.model = model;
                                    editPrompt.open();
                                }
                            }
                            Controls.Button {
                                text: "Delete"
                                onClicked: {
                                    customModel.deleteSpecies(model.species, index);
                                }
                            }
                        }
                    }
                }
            }
        }
```

## Our app so far

Existing code:

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

Code written or changed on this page:

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
remove_definitions(-DQT_NO_CAST_FROM_ASCII)

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
                text: i18n("C++ models in QML")
                icon.name: "start-here-sonicde"
                onTriggered: pageStack.push(Qt.createComponent("org.kde.tutorial.components", "ModelsPage"))
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
    ModelsPage.qml
)

target_sources(kirigami-hello-components
    PRIVATE
    backend.cpp backend.h
    model.cpp model.h
)

ecm_finalize_qml_module(kirigami-hello-components)

install(TARGETS kirigami-hello-components ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})
```

</details>

<details>
<summary>src/components/ModelsPage.qml</summary>

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.tutorial.components

Kirigami.ScrollablePage {
    title: "C++ models in QML"
    actions: [
        Kirigami.Action {
            icon.name: "list-add-symbolic"
            text: "Add New Species"
            onTriggered: {
                addPrompt.open();
            }
        }
    ]
    Model {
        id: customModel
    }
    ColumnLayout {
        anchors.left: parent.left
        anchors.right: parent.right
        Repeater {
            model: customModel
            delegate: Kirigami.AbstractCard {
                Layout.fillHeight: true
                header: Kirigami.Heading {
                    text: model.species
                    level: 2
                }
                contentItem: Item {
                    implicitWidth: delegateLayout.implicitWidth
                    implicitHeight: delegateLayout.implicitHeight
                    ColumnLayout {
                        id: delegateLayout
                        Controls.Label {
                            text: model.characters
                        }
                        RowLayout {
                            Layout.fillWidth: true
                            Controls.Button {
                                text: "Edit"
                                onClicked: {
                                    editPrompt.text = model.characters;
                                    editPrompt.model = model;
                                    editPrompt.open();
                                }
                            }
                            Controls.Button {
                                text: "Delete"
                                onClicked: {
                                    customModel.deleteSpecies(model.species, index);
                                }
                            }
                        }
                    }
                }
            }
        }
    }
    Kirigami.PromptDialog {
        id: addPrompt
        title: "Add New Species"
        standardButtons: Kirigami.Dialog.Ok
        onAccepted: {
            customModel.addSpecies(addPromptText.text);
            addPromptText.text = ""; // Clear TextField every time it's done
            addPrompt.close();
        }
        Controls.TextField {
            id: addPromptText
            Layout.fillWidth: true
            onAccepted: addPrompt.accept()
        }
    }

    Kirigami.PromptDialog {
        id: editPrompt
        property var model
        property alias text: editPromptText.text
        title: "Edit Characters"
        standardButtons: Kirigami.Dialog.Ok | Kirigami.Dialog.Cancel
        onAccepted: {
            const model = editPrompt.model;
            model.characters = editPromptText.text;
            editPrompt.close();
        }
        Controls.TextField {
            id: editPromptText
            onAccepted: editPrompt.accept()
        }
    }
}
```

</details>

<details>
<summary>src/components/model.h</summary>

```cpp
#pragma once

#include <QAbstractListModel>
#include <qqmlintegration.h>

class Model : public QAbstractListModel {
    Q_OBJECT
    QML_ELEMENT
public:
    enum Roles {
        SpeciesRole = Qt::UserRole,
        CharactersRole
    };
    int rowCount(const QModelIndex &) const override;
    QHash<int, QByteArray> roleNames() const override;
    QVariant data(const QModelIndex &index, int role) const override;
    bool setData(const QModelIndex &index, const QVariant &value, int role) override;
    Q_INVOKABLE void addSpecies(const QString &species);
    Q_INVOKABLE void deleteSpecies(const QString &speciesName, const int &rowIndex);
private:
    QMap<QString, QStringList> m_list = {
        {"Feline", {"Tigress",   "Waai Fuu"}},
        {"Fox",    {"Carmelita", "Diane", "Krystal"}},
        {"Goat",   {"Sybil",     "Toriel"}}
    };
    static QString formatList(const QStringList& list);
};
```

</details>

<details>
<summary>src/components/model.cpp</summary>

```cpp
#include "model.h"

int Model::rowCount(const QModelIndex &) const {
    return m_list.count();
}

QHash<int, QByteArray> Model::roleNames() const {
    return {
        {SpeciesRole,   "species"},
        {CharactersRole, "characters"}
    };
}

QVariant Model::data(const QModelIndex &index, int role) const {
    const auto it = std::next(m_list.begin(), index.row());
    switch (role) {
        case SpeciesRole:
            return it.key();
        case CharactersRole:
            return formatList(it.value());
        default:
            return {};
    }
}

QString Model::formatList(const QStringList& list) {
    return list.join(", ");
}

bool Model::setData(const QModelIndex &index, const QVariant &value, int role) {
    if (role != CharactersRole || !value.canConvert<QString>()) {
        return false;
    }

    auto it = std::next(m_list.begin(), index.row());
    QString charactersUnformatted = value.toString();
    QStringList characters = charactersUnformatted.split(", ");

    m_list[it.key()] = characters;
    Q_EMIT dataChanged(index, index);

    return true;
}

void Model::addSpecies(const QString& species) {
    if (species.isEmpty() || m_list.contains(species)) {
        return;
    }
    const int row = std::distance(m_list.begin(), m_list.lowerBound(species));
    beginInsertRows(QModelIndex(), row, row);
    m_list.insert(species, {});
    endInsertRows();
}

void Model::deleteSpecies(const QString &speciesName, const int& rowIndex) {
    beginRemoveRows(QModelIndex(), rowIndex, rowIndex);
    m_list.remove(speciesName);
    endRemoveRows();
}
```

</details>

## More information

For more information, see [Using C++ Models with Qt Quick Views](https://doc.qt.io/qt-6/qtquick-modelviewsdata-cppmodels.html) and [Model/View Programming](https://doc.qt.io/qt-6/model-view-programming.html).
