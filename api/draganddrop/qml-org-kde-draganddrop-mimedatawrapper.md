---
title: "MimeDataWrapper QML Type"
description: "Exposes a const QMimeData instance."
---

# MimeDataWrapper QML Type

Exposes a const [QMimeData](https://doc.qt.io/qt-6/qmimedata.html) instance. [More...](#details)

- Import Statement: import org.kde.draganddrop

## Detailed Description {#details}

In contrast to [MimeData](qml-org-kde-draganddrop-mimedata.md), doesn't create a copy of the [QMimeData](https://doc.qt.io/qt-6/qmimedata.html) instance.

## Property Documentation {#property-documentation}

### color : var {#color-prop}

A color if the data stored in the object represents a color (MIME type application/x-color); otherwise QVariant().

### formats : list\<string\> {#formats-prop}

Mimetypes provided by the mime data instance

*See also* [QMimeData::formats](https://doc.qt.io/qt-6/qmimedata.html#formats)

### hasUrls : bool {#hasUrls-prop}

*See also* [QMimeData::hasUrls](https://doc.qt.io/qt-6/qmimedata.html#hasUrls)

### html : string {#html-prop}

A string if the data stored in the object is HTML (MIME type text/html); otherwise returns an empty string.

### mimeData : QMimeData\* {#mimeData-prop}

Returns the wrapped object

### source : var {#source-prop}

The graphical item on the scene that started the drag event. It may be null.

### text : string {#text-prop}

A plain text (MIME type text/plain) representation of the data.

### url : url {#url-prop}

Url contained in the mimedata

### urls : QJsonArray {#urls-prop}

A list of URLs contained within the MIME data object. URLs correspond to the MIME type text/uri-list.

## Method Documentation {#method-documentation}

### QByteArray getDataAsByteArray(string *format*) {#getDataAsByteArray-method}
