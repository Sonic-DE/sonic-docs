---
title: "KActionCategory Class"
description: "Categorize actions for KShortcutsEditor."
---

# KActionCategory Class

Categorize actions for [KShortcutsEditor](kshortcutseditor.md). [More...](#details)

- **Header:** `#include <KActionCategory>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kactioncategory-members.md)  
[Deprecated members](kactioncategory-obsolete.md)

## Properties

- [text : QString](#text-prop)

## Public Functions

- [KActionCategory(const QString &text, KActionCollection \*parent = nullptr)](#KActionCategory)
- [~KActionCategory()](#dtor.KActionCategory)
- [const QList\<QAction \*\> actions() const](#actions)
- [template \<typename ActionType\> ActionType \*add(const QString &name)](#add) (since 6.9)
- [QAction \*add(const int \*receiver, int slot)](#add-1) (since 6.9)
- [QAction \*addAction(KStandardActions::StandardAction actionType)](#addAction) (since 6.9)
- [QAction \*addAction(KStandardActions::StandardAction actionType, const QString &name)](#addAction-2) (since 6.15)
- [QAction \*addAction(const QString &name, QAction \*action)](#addAction-3)
- [QAction \*addAction(const int \*receiver, int slot)](#addAction-4) (since 6.9)
- [QAction \*addAction(KStandardActions::StandardAction actionType, const int \*receiver, int slot)](#addAction-5) (since 6.9)
- [QAction \*addAction(KStandardAction::StandardAction actionType, const QObject \*receiver = nullptr, const char \*member = nullptr)](#addAction-6)
- [QAction \*addAction(KStandardAction::StandardAction actionType, const QString &name, const QObject \*receiver = nullptr, const char \*member = nullptr)](#addAction-8)
- [KActionCollection \*collection() const](#collection)
- [void setText(const QString &text)](#setText)
- [QString text() const](#text)

## Detailed Description {#details}

[KActionCategory](kactioncategory.md) provides a second level to organize the actions in [KShortcutsEditor](kshortcutseditor.md).

The first possibility is using more than one action collection. Each actions collection becomes a top level node.

- action collection 1
   
   - first action
   - second action
   - third action

- action collection 2
   
   - first action
   - second action
   - third action

Using [KActionCategory](kactioncategory.md) it's possible to group the actions of one collection.

- action collection 1
   
   - first action
   - first category
      
      - action 1 in category
      - action 2 in category
   - second action

The usage is analogous to action collections. Just create a category and use it instead of the collection to create the actions.

The synchronization between [KActionCollection](kactioncollection.md) and [KActionCategory](kactioncategory.md) is done internally. There is for example no need to remove actions from a category. It is done implicitly if the action is removed from the associated collection.

```cpp
KActionCategory *file = new KActionCategory(i18n("File"), actionCollection());
file->addAction(
     KStandardActions::New,   //< see KStandardAction
     this,                   //< Receiver
     &MyApp::fileNew);       //< Slot

// ... more actions added to file ...

KActionCategory *edit = new KActionCategory(i18n("Edit"), actionCollection());
edit->addAction(
     KStandardActions::Copy,  //< see KStandardAction
     this,                   //< Receiver
     &MyApp::fileNew);       //< Slot

// ...
```

## Property Documentation {#property-documentation}

### text : QString {#text-prop}

**Access functions:**

- `QString` **[text](kactioncategory.md#text)**() const
- `void` **[setText](kactioncategory.md#setText)**(const `QString` &*text*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KActionCategory::KActionCategory(const QString &*text*, KActionCollection \**parent* = nullptr) {#KActionCategory}

Constructs a new [KActionCategory](kactioncategory.md) object named `text` as a child of `parent`.

### \[override virtual noexcept\] KActionCategory::~KActionCategory() {#dtor.KActionCategory}

Destructor.

### const QList\<QAction \*\> KActionCategory::actions() const {#actions}

Returns the actions belonging to this category.

### \[since 6.9\] template \<typename ActionType\> ActionType \*KActionCategory::add(const QString &*name*) {#add}

Creates a new action and adds it to the collection. The newly created action is also returned.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`name` The name by which the action be retrieved again from the collection.

Returns the created action.

This function was introduced in Qt 6.9.

### \[since 6.9\] QAction \*KActionCategory::add(const int \**receiver*, int *slot*) {#add-1}

Creates a new action, adds it to the collection and connects the action's triggered(bool) signal to the specified receiver/member. The newly created action is also returned.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`name` The name by which the action be retrieved again from the collection.

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns the created action.

This function was introduced in Qt 6.9.

### \[since 6.9\] QAction \*KActionCategory::addAction(KStandardActions::StandardAction *actionType*) {#addAction}

Creates a new standard action and adds it to the collection. The newly created action is also returned.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`actionType` The standard action type of the action to create.

Returns the created action.

This function was introduced in Qt 6.9.

### \[since 6.15\] QAction \*KActionCategory::addAction(KStandardActions::StandardAction *actionType*, const QString &*name*) {#addAction-2}

Creates a new standard action and adds it to the collection.

The newly created action is also returned.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`actionType` The standard action type of the action to create.

`name` The name by which the action be retrieved again from the collection.

Returns the created action.

This function was introduced in Qt 6.15.

### QAction \*KActionCategory::addAction(const QString &*name*, QAction \**action*) {#addAction-3}

Adds an action to the category.

These methods are provided for your convenience. They call the corresponding method of [KActionCollection](kactioncollection.md).

### \[since 6.9\] QAction \*KActionCategory::addAction(const int \**receiver*, int *slot*) {#addAction-4}

Creates a new action, adds it to the collection and connects the action's triggered(bool) signal to the specified receiver/member. The newly created action is also returned.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`name` The name by which the action be retrieved again from the collection.

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns the created action.

This function was introduced in Qt 6.9.

### \[since 6.9\] QAction \*KActionCategory::addAction(KStandardActions::StandardAction *actionType*, const int \**receiver*, int *slot*) {#addAction-5}

Creates a new standard action, adds it to the collection and connects the action's triggered(bool) signal to the specified receiver/member. The newly created action is also returned.

The [KActionCollection](kactioncollection.md) takes ownership of the action object.

`actionType` The standard action type of the action to create.

`name` The name by which the action be retrieved again from the collection.

`receiver` The [QObject](https://doc.qt.io/qt-6/qobject.html) to connect the triggered(bool) signal to. Leave nullptr if no connection is desired.

`slot` The slot or lambda to connect the triggered(bool) signal to.

Returns the created action.

This function was introduced in Qt 6.9.

### QAction \*KActionCategory::addAction(KStandardAction::StandardAction *actionType*, const QObject \**receiver* = nullptr, const char \**member* = nullptr) {#addAction-6}

This function overloads [KActionCategory::addAction(const QString &name, QAction \*action)](kactioncategory.md#addAction-3).

### QAction \*KActionCategory::addAction(KStandardAction::StandardAction *actionType*, const QString &*name*, const QObject \**receiver* = nullptr, const char \**member* = nullptr) {#addAction-8}

This function overloads [KActionCategory::addAction(const QString &name, QAction \*action)](kactioncategory.md#addAction-3).

### KActionCollection \*KActionCategory::collection() const {#collection}

Returns the action collection this category is associated with.

### void KActionCategory::setText(const QString &*text*) {#setText}

Sets the action category's descriptive `text`.

> **Note:** Setter function for property [text](kactioncategory.md#text-prop).

*See also* [text](kactioncategory.md#text)()

### QString KActionCategory::text() const {#text}

Returns the action category's descriptive text.

> **Note:** Getter function for property [text](kactioncategory.md#text-prop).

*See also* [setText](kactioncategory.md#setText)()
