---
title: "AlternativesView QML Type"
description: "Framework for providing abstractions to get the developer's purposes fulfilled.."
---

# AlternativesView QML Type

Framework for providing abstractions to get the developer's purposes fulfilled.. [More...](#details)

- Import Statement: import org.kde.purpose
- Inherits: [StackView](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html)

## Detailed Description {#details}

[AlternativesView](qml-org-kde-purpose-alternativesview.md)

## Property Documentation {#property-documentation}

### delegate : Component {#delegate-prop}

### \[since 6.29\] disabledPlugins : var {#disabledPlugins-prop}

This property was introduced in Qt 6.29.

### footer : Component {#footer-prop}

### header : Component {#header-prop}

### highlight : Component {#highlight-prop}

### inputData : var {#inputData-prop}

### pluginType : string {#pluginType-prop}

### running : bool {#running-prop}

### verticalLayoutDirection : enumeration {#verticalLayoutDirection-prop}

## Signal Documentation {#signal-documentation}

### finished(var *output*, int *error*, string *message*) {#finished-signal}

Signals when the job finishes, reports the `error` code and a text `message`.

`output` will specify the output offered by the job

> **Note:** The corresponding handler is `onFinished`.

## Method Documentation {#method-documentation}

### createJob(*listViewIndex*) {#createJob-method}

Adopts the job at the `listViewIndex`.

### reset() {#reset-method}

Clears and returns back to the initial view.
