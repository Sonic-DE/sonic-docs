---
title: "AnnotationTool QML Type"
description: "The data structure that controls the creation of the next item."
---

# AnnotationTool QML Type

The data structure that controls the creation of the next item. [More...](#details)

- Import Statement: import org.kde.kquickimageeditor

## Detailed Description {#details}

From QML its parameter will be set by the app toolbars, and then drawing on the screen with the mouse will lead to the creation of a new item based on those parameters.

## Property Documentation {#property-documentation}

### Option : enumeration {#Option-prop}

These options are meant to help control which options are visible in the UI and what kinds of traits a drawable object should have.

| Constant |
| --- |
| NoOptions |
| StrokeOption |
| FillOption |
| StrengthOption |
| FontOption |
| TextOption |
| NumberOption |
| ShadowOption |

### Tool : enumeration {#Tool-prop}

These tools are meant to be shown as selectable tool types in the UI. They can also affect the types of traits a drawable object is allowed to have.

| Constant |
| --- |
| NoTool |
| SelectTool |
| FreehandTool |
| HighlighterTool |
| LineTool |
| ArrowTool |
| RectangleTool |
| EllipseTool |
| BlurTool |
| PixelateTool |
| TextTool |
| NumberTool |
| NTools |

### fillColor : color {#fillColor-prop}

### font : font {#font-prop}

### fontColor : color {#fontColor-prop}

### isCreationTool : bool {#isCreationTool-prop}

### isMetaTool : bool {#isMetaTool-prop}

### isNoTool : bool {#isNoTool-prop}

### number : int {#number-prop}

### options : Options {#options-prop}

### shadow : bool {#shadow-prop}

### strength : real {#strength-prop}

### strokeColor : color {#strokeColor-prop}

### strokeWidth : int {#strokeWidth-prop}

### type : Tool {#type-prop}
