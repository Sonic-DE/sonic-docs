---
title: "FormSliderDelegate QML Type"
description: "A form delegate for selecting a value with a slider."
---

# FormSliderDelegate QML Type

A form delegate for selecting a value with a slider. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

Use [valueText](qml-org-kde-kirigamiaddons-formcard-formsliderdelegate.md#valueText-prop) to show a formatted value beside the label. Handle [moved](qml-org-kde-kirigamiaddons-formcard-formsliderdelegate.md#moved-signal) to react only to changes made by the user.

```qml
FormCard.FormSliderDelegate {
    id: transparencyDelegate
    label: i18n("Past event transparency")
    from: 0
    to: 1
    stepSize: 0.05
    value: Config.pastEventsTransparencyLevel
    valueText: i18n("%1%", Math.round(value * 100))
    onMoved: Config.pastEventsTransparencyLevel = value
}
```

## Property Documentation {#property-documentation}

### \[default: ""\] description : string {#description-prop}

Secondary text shown below the slider.

### from : real {#from-prop}

The [minimum value](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html#from-prop) of the slider.

### \[required\] label : string {#label-prop}

The label shown above the slider.

### \[default: null\] leading : Item {#leading-prop}

An item shown before the slider, such as an icon.

### stepSize : real {#stepSize-prop}

The [step size](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html#stepSize-prop) of the slider.

### to : real {#to-prop}

The [maximum value](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html#to-prop) of the slider.

### \[default: null\] trailing : Item {#trailing-prop}

An item shown after the slider, such as an icon.

### value : real {#value-prop}

The [value](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html#value-prop) of the slider.

### \[default: ""\] valueText : string {#valueText-prop}

Optional text shown beside the label, such as a formatted value.

## Signal Documentation {#signal-documentation}

### moved() {#moved-signal}

Emitted when the user moves the slider with a mouse, touch, or keyboard.

> **Note:** The corresponding handler is `onMoved`.
