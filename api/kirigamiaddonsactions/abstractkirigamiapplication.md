---
title: "AbstractKirigamiApplication Class"
description: "The main container for your actions."
---

# AbstractKirigamiApplication Class

The main container for your actions. [More...](#details)

- **Header:** `#include <AbstractKirigamiApplication>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](abstractkirigamiapplication-members.md)

## Properties

- [configurationView : QObject\*](#configurationView-prop)

## Public Functions

- [AbstractKirigamiApplication(QObject \*parent = nullptr)](#AbstractKirigamiApplication)
- [~AbstractKirigamiApplication()](#dtor.AbstractKirigamiApplication)
- [QAction \*action(const QString &actionName)](#action)
- [QList\<KirigamiActionCollection \*\> actionCollections() const](#actionCollections)
- [QObject \*configurationView() const](#configurationView)
- [KirigamiActionCollection \*mainCollection() const](#mainCollection)
- [void setConfigurationView(QObject \*configurationView)](#setConfigurationView)

## Signals

- [void actionCollectionsChanged()](#actionCollectionsChanged)
- [void configurationViewChanged()](#configurationViewChanged)

## Protected Functions

- [void readSettings()](#readSettings)
- [void setupActions()](#setupActions)

## Detailed Description {#details}

[AbstractKirigamiApplication](abstractkirigamiapplication.md) is a class that needs to be inherited in your application.

It allows to expose the various actions of your application to the QML frontend. Depending on the complexitiy of the application, you can either reimplement [setupActions](abstractkirigamiapplication.md#setupActions) only and put all your actions inside the [mainCollection](abstractkirigamiapplication.md#mainCollection), or, if you want to organize your actions in multiple collections, you can also expose the custom collections by overwriting [actionCollections](abstractkirigamiapplication.md#actionCollections).

```cpp
class MyKoolApp : public AbstractKirigamiApplication
{
    Q_OBJECT
    QML_ELEMENT

 public:
    explicit MyKoolApp(QObject *parent = nullptr);

    void setupActions() override;
};

MyKoolApp::MyKoolApp(QObject *parent)
    : AbstractKirigamiApplication(parent)
{
     setupActions();
}

void MyKoolApp::setupActions()
{
    AbstractKirigamiApplication::setupActions();

    auto actionName = QLatin1String("add_notebook");
    if (KAuthorized::authorizeAction(actionName)) {
        auto action = mainCollection()->addAction(actionName, this, &MyKoolApp::newNotebook);
        action->setText(i18nc("@action:inmenu", "New Notebook"));
        action->setIcon(QIcon::fromTheme(QStringLiteral("list-add-symbolic")));
        mainCollection()->addAction(action->objectName(), action);
        mainCollection()->setDefaultShortcut(action, QKeySequence(Qt::CTRL | Qt::SHIFT | Qt::Key_N));
    }
}
```

The application object then need to be assigned to the application property in a [StatefulWindow](qml-org-kde-kirigamiaddons-actions-statefulwindow.md).

```cpp
import org.kde.kirigamiaddons.actions as KirigamiActions

KirigamiActions.StatefulWindow {
    id: root

    application: MyKoolApp {}

    KirigamiActions.Action {
        actionName: 'add_notebook'
        application: root.application
    }
}
```

{}

## Property Documentation {#property-documentation}

### configurationView : QObject\* {#configurationView-prop}

This property holds the [configurationView](abstractkirigamiapplication.md#configurationView) of the application

When set, [AbstractKirigamiApplication](abstractkirigamiapplication.md) will setup a "options\_configure" action that will open the [configurationView](abstractkirigamiapplication.md#configurationView) when triggered.

**Access functions:**

- `QObject` \***[configurationView](abstractkirigamiapplication.md#configurationView)**() const
- `void` **[setConfigurationView](abstractkirigamiapplication.md#setConfigurationView)**(`QObject` \**configurationView*)

**Notifier signal:**

- `void` **[configurationViewChanged](abstractkirigamiapplication.md#configurationViewChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AbstractKirigamiApplication::AbstractKirigamiApplication(QObject \**parent* = nullptr) {#AbstractKirigamiApplication}

Default constructor of [AbstractKirigamiApplication](abstractkirigamiapplication.md) `parent` the parent object

### \[virtual noexcept\] AbstractKirigamiApplication::~AbstractKirigamiApplication() {#dtor.AbstractKirigamiApplication}

Default destructor of [AbstractKirigamiApplication](abstractkirigamiapplication.md)

### \[invokable\] QAction \*AbstractKirigamiApplication::action(const QString &*actionName*) {#action}

Get the named action. `actionName` the name of the action to look up. Returns nullptr is not such action is defined.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[virtual invokable\] QList\<KirigamiActionCollection \*\> AbstractKirigamiApplication::actionCollections() const {#actionCollections}

Return the list of [KirigamiActionCollection](kirigamiactioncollection.md) setup in your application. Overwrite this method if you are using custom collections.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[signal\] void AbstractKirigamiApplication::actionCollectionsChanged() {#actionCollectionsChanged}

Emitted when an action collection is assigned to this application.

### QObject \*AbstractKirigamiApplication::configurationView() const {#configurationView}

Getter for the configurationView property.

> **Note:** Getter function for property [configurationView](abstractkirigamiapplication.md#configurationView-prop).

*See also* [setConfigurationView](abstractkirigamiapplication.md#setConfigurationView)()

### \[signal\] void AbstractKirigamiApplication::configurationViewChanged() {#configurationViewChanged}

Changed signal for the [configurationView](abstractkirigamiapplication.md#configurationView) property.

> **Note:** Notifier signal for property [configurationView](abstractkirigamiapplication.md#configurationView-prop).

### KirigamiActionCollection \*AbstractKirigamiApplication::mainCollection() const {#mainCollection}

Return the main action collection.

### \[protected\] void AbstractKirigamiApplication::readSettings() {#readSettings}

Read the configured settings for the action.

### void AbstractKirigamiApplication::setConfigurationView(QObject \**configurationView*) {#setConfigurationView}

Setter for the [configurationView](abstractkirigamiapplication.md#configurationView) property. `configurationView` the new configuration view.

> **Note:** Setter function for property [configurationView](abstractkirigamiapplication.md#configurationView-prop).

*See also* [configurationView](abstractkirigamiapplication.md#configurationView)()

### \[virtual protected\] void AbstractKirigamiApplication::setupActions() {#setupActions}

Entry points to declare your actions.

Don't forget to call the parent implementation to get the following actions setup for you:

- CommandBar
- About page for your application
- About page for KDE

Once the actions are setup, call [readSettings](abstractkirigamiapplication.md#readSettings) to read the configured shortcuts.
