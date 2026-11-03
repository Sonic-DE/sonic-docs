---
title: "ScenePosition QML Type"
description: "An attached property that contains the information about the scene position of the item."
---

# ScenePosition QML Type

An attached property that contains the information about the scene position of the item. [More...](#details)

- Import Statement: import org.kde.kirigami.primitives

## Detailed Description {#details}

Its global x and y coordinates will update automatically and can be binded.

```cpp
import org.kde.kirigami as Kirigami
Text {
   text: ScenePosition.x
}
```

## Attached Property Documentation {#attached-property-documentation}

### ScenePosition.x : double {#x-attached-prop}

The global scene X position

### ScenePosition.y : double {#y-attached-prop}

The global scene Y position
