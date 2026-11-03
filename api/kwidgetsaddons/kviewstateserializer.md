---
title: "KViewStateSerializer Class"
description: "Object for saving and restoring state in QTreeViews and QItemSelectionModels."
---

# KViewStateSerializer Class

Object for saving and restoring state in QTreeViews and QItemSelectionModels. [More...](#details)

- **Header:** `#include <KViewStateSerializer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kviewstateserializer-members.md)

## Public Functions

- [KViewStateSerializer(QObject \*parent = nullptr)](#KViewStateSerializer)
- [QString currentIndexKey() const](#currentIndexKey)
- [QStringList expansionKeys() const](#expansionKeys)
- [void restoreCurrentItem(const QString &indexString)](#restoreCurrentItem)
- [void restoreExpanded(const QStringList &indexStrings)](#restoreExpanded)
- [void restoreScrollState(int verticalScoll, int horizontalScroll)](#restoreScrollState)
- [void restoreSelection(const QStringList &indexStrings)](#restoreSelection)
- [QPair\<int, int\> scrollState() const](#scrollState)
- [QStringList selectionKeys() const](#selectionKeys)
- [QItemSelectionModel \*selectionModel() const](#selectionModel)
- [void setSelectionModel(QItemSelectionModel \*selectionModel)](#setSelectionModel)
- [void setView(QAbstractItemView \*view)](#setView)
- [QAbstractItemView \*view() const](#view)

## Protected Functions

- [QModelIndex indexFromConfigString(const QAbstractItemModel \*model, const QString &key) const](#indexFromConfigString)
- [QString indexToConfigString(const QModelIndex &index) const](#indexToConfigString)

## Detailed Description {#details}

Implement the [indexFromConfigString](kviewstateserializer.md#indexFromConfigString) and [indexToConfigString](kviewstateserializer.md#indexToConfigString) methods to handle the model in the view whose state is being saved. These implementations can be quite trivial:

```cpp
QModelIndex DynamicTreeStateSaver::indexFromConfigString(const QAbstractItemModel* model,
                                                         const QString& key) const
{
    QModelIndexList list = model->match(model->index(0, 0),
                                        DynamicTreeModel::DynamicTreeModelId,
                                        key.toInt(), 1, Qt::MatchRecursive);
    if (list.isEmpty()) {
        return QModelIndex();
    }
    return list.first();
}

QString DynamicTreeStateSaver::indexToConfigString(const QModelIndex& index) const
{
    return index.data(DynamicTreeModel::DynamicTreeModelId).toString();
}
```

It is possible to restore the state of a [QTreeView](https://doc.qt.io/qt-6/qtreeview.html) (that is, the expanded state and selected state of all indexes as well as the horizontal and vertical scroll state) by using [setView](kviewstateserializer.md#setView).

If there is no tree view state to restore (for example if using QML), the selection state of a [QItemSelectionModel](https://doc.qt.io/qt-6/qitemselectionmodel.html) can be saved or restored instead.

The state of any [QAbstractScrollArea](https://doc.qt.io/qt-6/qabstractscrollarea.html) can also be saved and restored.

A [KViewStateSerializer](kviewstateserializer.md) should be created on the stack when saving and on the heap when restoring. The model may be populated dynamically between several event loops, so it may not be immediate for the indexes that should be selected to be in the model. The saver should \*not\* be persisted as a member. The saver will destroy itself when it has completed the restoration specified in the config group, or a small amount of time has elapsed.

```cpp
MyWidget::MyWidget(Qobject *parent)
  : QWidget(parent)
{
    ...

    m_view = new QTreeView(splitter);
    m_view->setModel(model);

    connect(model, &QAbstractItemModel::modelAboutToBeReset, this, [this]() { saveState(); });
    connect(model, &QAbstractItemModel::modelReset, [this]() { restoreState(); });
    connect(qApp, &QApplication::aboutToQuit, this, [this]() { saveState(); });

    restoreState();
}

void StateSaverWidget::saveState()
{
    ConcreteStateSaver saver;
    saver.setView(m_view);

    KConfigGroup cfg(KSharedConfig::openConfig(), "ExampleViewState");
    saver.saveState(cfg);
    cfg.sync();
}

void StateSaverWidget::restoreState()
{
    // Will delete itself.
    ConcreteTreeStateSaver *saver = new ConcreteStateSaver();
    saver->setView(m_view);
    KConfigGroup cfg(KSharedConfig::openConfig(), "ExampleViewState");
    saver->restoreState(cfg);
}
```

After creating a saver, the state can be saved using a KConfigGroup.

It is also possible to save and restore state directly by using the [restoreSelection](kviewstateserializer.md#restoreSelection), [restoreExpanded](kviewstateserializer.md#restoreExpanded) etc methods. Note that the implementation of these methods should return strings that the [indexFromConfigString](kviewstateserializer.md#indexFromConfigString) implementation can handle.

```cpp
class DynamicTreeStateSaver : public KViewStateSerializer
{
    Q_OBJECT
public:
  // ...

    void selectItems(const QList<qint64> &items)
    {
        QStringList itemStrings;
        for (qint64 item : items) {
            itemStrings << QString::number(item);
        }
        restoreSelection(itemStrings);
    }

    void expandItems(const QList<qint64> &items)
    {
        QStringList itemStrings;
        for (qint64 item : items) {
            itemStrings << QString::number(item);
        }
        restoreSelection(itemStrings);
    }
};
```

Note that a single instance of this class should be used with only one widget. That is don't do this:

```cpp
saver->setView(treeView1);
saver->setSelectionModel(treeView2->selectionModel());
saver->setScrollArea(treeView3);
```

To save the state of 3 different widgets, use three savers, even if they operate on the same root model.

```cpp
saver1->setView(treeView1);
saver2->setSelectionModel(treeView2->selectionModel());
saver3->setScrollArea(treeView3);
```

> **Note:** The [KViewStateSerializer](kviewstateserializer.md) does not take ownership of any widgets set on it.

It is recommended to restore the state on application startup and after the model has been reset, and to save the state on application close and before the model has been reset.

*See also* [QAbstractItemModel::modelAboutToBeReset](https://doc.qt.io/qt-6/qabstractitemmodel.html#modelAboutToBeReset)(), [QAbstractItemModel::modelReset](https://doc.qt.io/qt-6/qabstractitemmodel.html#modelReset)()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KViewStateSerializer::KViewStateSerializer(QObject \**parent* = nullptr) {#KViewStateSerializer}

Constructor

### QString KViewStateSerializer::currentIndexKey() const {#currentIndexKey}

Returns a [QString](https://doc.qt.io/qt-6/qstring.html) describing the current index in the selection model.

### QStringList KViewStateSerializer::expansionKeys() const {#expansionKeys}

Returns a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) representing the expanded indexes in the [QTreeView](https://doc.qt.io/qt-6/qtreeview.html).

### \[pure virtual protected\] QModelIndex KViewStateSerializer::indexFromConfigString(const QAbstractItemModel \**model*, const QString &*key*) const {#indexFromConfigString}

Reimplement to return an index in the `model` described by the unique key `key`

### \[pure virtual protected\] QString KViewStateSerializer::indexToConfigString(const QModelIndex &*index*) const {#indexToConfigString}

Reimplement to return a unique string for the `index`.

### void KViewStateSerializer::restoreCurrentItem(const QString &*indexString*) {#restoreCurrentItem}

Make the index described by `indexString` the currentIndex in the [selectionModel](kviewstateserializer.md#selectionModel).

### void KViewStateSerializer::restoreExpanded(const QStringList &*indexStrings*) {#restoreExpanded}

Expand the indexes described by `indexStrings` in the [QTreeView](https://doc.qt.io/qt-6/qtreeview.html).

### void KViewStateSerializer::restoreScrollState(int *verticalScoll*, int *horizontalScroll*) {#restoreScrollState}

Restores the scroll state of the [QAbstractScrollArea](https://doc.qt.io/qt-6/qabstractscrollarea.html) to the `verticalScoll` and `horizontalScroll`

### void KViewStateSerializer::restoreSelection(const QStringList &*indexStrings*) {#restoreSelection}

Select the indexes described by `indexStrings`

### QPair\<int, int\> KViewStateSerializer::scrollState() const {#scrollState}

Returns the vertical and horizontal scroll of the [QAbstractScrollArea](https://doc.qt.io/qt-6/qabstractscrollarea.html).

### QStringList KViewStateSerializer::selectionKeys() const {#selectionKeys}

Returns a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) describing the selection in the [selectionModel](kviewstateserializer.md#selectionModel).

### QItemSelectionModel \*KViewStateSerializer::selectionModel() const {#selectionModel}

The [QItemSelectionModel](https://doc.qt.io/qt-6/qitemselectionmodel.html) whose state is persisted.

*See also* [setSelectionModel](kviewstateserializer.md#setSelectionModel)()

### void KViewStateSerializer::setSelectionModel(QItemSelectionModel \**selectionModel*) {#setSelectionModel}

Sets the [QItemSelectionModel](https://doc.qt.io/qt-6/qitemselectionmodel.html) whose state is persisted.

*See also* [selectionModel](kviewstateserializer.md#selectionModel)()

### void KViewStateSerializer::setView(QAbstractItemView \**view*) {#setView}

Sets the view whose state is persisted.

*See also* [view](kviewstateserializer.md#view)()

### QAbstractItemView \*KViewStateSerializer::view() const {#view}

The view whose state is persisted.

*See also* [setView](kviewstateserializer.md#setView)()
