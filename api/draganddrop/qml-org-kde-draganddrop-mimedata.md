---
title: "MimeData QML Type"
description: "This is a wrapper class around QMimeData with a few extensions to provide better support for in-qml drag & drops."
---

# MimeData QML Type

This is a wrapper class around [QMimeData](https://doc.qt.io/qt-6/qmimedata.html) with a few extensions to provide better support for in-qml drag & drops. [More...](#details)

- Import Statement: import org.kde.draganddrop

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### color : color {#color-prop}

A color if the data stored in the object represents a color (MIME type application/x-color); otherwise QColor().

### formats : list\<string\> {#formats-prop}

*See also* [QMimeData::formats](https://doc.qt.io/qt-6/qmimedata.html#formats)

### hasUrls : bool {#hasUrls-prop}

*See also* [QMimeData::hasUrls](https://doc.qt.io/qt-6/qmimedata.html#hasUrls)

### html : string {#html-prop}

A string if the data stored in the object is HTML (MIME type text/html); otherwise returns an empty string.

### source : Item {#source-prop}

The graphical item on the scene that started the drag event. It may be null.

Setting source to any existing qml item will enable the receiver of the drag and drop operation to know in which item the operation originated.

In the case of inter-application drag and drop operations, the source will not be available, and will be 0. Be sure to test it in your QML code, before using it, or it will generate errors in the console.

### text : string {#text-prop}

A plain text (MIME type text/plain) representation of the data.

### url : url {#url-prop}

The first URL from the urls property of [QMimeData](https://doc.qt.io/qt-6/qmimedata.html).

### urls : QJsonArray {#urls-prop}

A list of URLs contained within the MIME data object. URLs correspond to the MIME type text/uri-list.

## Method Documentation {#method-documentation}

### getDataAsByteArray(string *format*) {#getDataAsByteArray-method}

### hasColor() {#hasColor-method}

### setData(string *mimeType*, variant *data*) {#setData-method}
