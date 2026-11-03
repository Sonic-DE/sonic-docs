---
title: "SpellCheck QML Type"
description: "This attached property contains hints for spell checker."
---

# SpellCheck QML Type

This attached property contains hints for spell checker. [More...](#details)

- Import Statement: import org.kde.kirigami

## Detailed Description {#details}

> **Warning:** Kirigami doesn't provide any spell checker per se, this is just a hint for QQC2 style implementation and other downstream components. If you want to add spell checking to your custom application theme check out Sonnet.

```cpp
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

QQC2.TextArea {
   Kirigami.SpellCheck.enabled: true
}
```

## Attached Property Documentation {#attached-property-documentation}

### SpellCheck.enabled : bool {#enabled-attached-prop}

This property holds whether the spell checking should be enabled on the [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html)/[TextArea](https://doc.qt.io/qt-6/qml-qtquick-controls-textarea.html).

> **Note:** By default, false. This might change in KF6, so if you don't want spellcheck in your application, explicitly set it to false.
