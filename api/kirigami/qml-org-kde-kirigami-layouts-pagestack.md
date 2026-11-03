---
title: "PageStack QML Type"
description: "This attached property makes possible to access from anywhere the page stack this page was pushed into. This type was introduced in Qt 6.10."
---

# PageStack QML Type

This attached property makes possible to access from anywhere the page stack this page was pushed into. This type was introduced in Qt 6.10. [More...](#details)

- Import Statement: import org.kde.kirigami.layouts
- Since: Qt 6.10

## Detailed Description {#details}

It can be an instance of [PageRow](qml-org-kde-kirigami-pagerow.md) or a [StackView](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html) from [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) Controls.

```qml
Kirigami.Page {
    id: root

    Button {
        text: "Push Page"
        onClicked: Kirigami.PageStack.push(Qt.resolvedurl("AnotherPage"));
    }
}
```

## Attached Property Documentation {#attached-property-documentation}

### PageStack.pageStack : Item {#pageStack-attached-prop}

This property holds the pageStack where this page was pushed.

It will point to the proper instance in the parent hierarchy and normally is not necessary to explicitly write it.

Write on this property only if it's desired this attached property and those of all the children to point to a different [PageRow](qml-org-kde-kirigami-pagerow.md) or [StackView](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html)

## Attached Signal Documentation {#attached-signal-documentation}

### \[since 6.20\] closeDialog() {#closeDialog-signal}

Close the currently opened dialog, which was opened with [PageRow::pushDialogLayer](qml-org-kde-kirigami-pagerow.md#pushDialogLayer-method).

> **Note:** The corresponding handler is `onCloseDialog`.

This signal was introduced in Qt 6.20.

## Attached Method Documentation {#attached-method-documentation}

### void clear() {#clear-method}

### void pop(variant *page*) {#pop-method}

### void push(variant *page*, object *properties*) {#push-method}

### void replace(variant *page*, object *properties*) {#replace-method}
