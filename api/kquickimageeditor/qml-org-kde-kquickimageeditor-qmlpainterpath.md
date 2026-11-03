---
title: "QmlPainterPath QML Type"
description: "A class for making QPainterPaths available in QML."
---

# QmlPainterPath QML Type

A class for making QPainterPaths available in QML. [More...](#details)

- Import Statement: import org.kde.kquickimageeditor

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### boundingRect : rect {#boundingRect-prop}

### elementCount : int {#elementCount-prop}

### empty : bool {#empty-prop}

### end : point {#end-prop}

### start : point {#start-prop}

### svgPath : string {#svgPath-prop}

The path in the form of an SVG path string for use with a Qt Quick SvgPath.

## Method Documentation {#method-documentation}

### string contains(point *point*) {#contains-method}

### string contains(rect *rect*) {#contains-method-1}

### string intersects(rect *rect*) {#intersects-method}

### string map(matrix4x4 *transform*) {#map-method}

### string mapBoundingRect(matrix4x4 *transform*) {#mapBoundingRect-method}

### string toString() {#toString-method}
