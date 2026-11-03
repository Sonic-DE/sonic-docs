---
title: "KImageFilePreview Class"
description: "Image preview widget for the file dialog."
---

# KImageFilePreview Class

Image preview widget for the file dialog. [More...](#details)

- **Header:** `#include <KImageFilePreview>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [KPreviewWidgetBase](kpreviewwidgetbase.md)

[List of all members, including inherited members](kimagefilepreview-members.md)

## Public Functions

- [KImageFilePreview(QWidget \*parent = nullptr)](#KImageFilePreview)

## Public Slots

- [void clearPreview()](#clearPreview)
- [void gotPreview(const KFileItem &, const QPixmap &)](#gotPreview)
- [void showPreview()](#showPreview)
- [void showPreview(const QUrl &url)](#showPreview-1)
- [void showPreview(const QUrl &url, bool force)](#showPreview-2)

## Protected Functions

- [KIO::PreviewJob \*createJob(const QUrl &url, int width, int height)](#createJob)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KImageFilePreview::KImageFilePreview(QWidget \**parent* = nullptr) {#KImageFilePreview}

Creates a new image file preview.

`parent` The parent widget.

### \[override virtual slot\] void KImageFilePreview::clearPreview() {#clearPreview}

Reimplements: [KPreviewWidgetBase::clearPreview()](kpreviewwidgetbase.md#clearPreview).

Clears the preview.

### \[virtual protected\] KIO::PreviewJob \*KImageFilePreview::createJob(const QUrl &*url*, int *width*, int *height*) {#createJob}

### \[virtual protected slot\] void KImageFilePreview::gotPreview(*const KFileItem &*, *const QPixmap &*) {#gotPreview}

### \[protected slot\] void KImageFilePreview::showPreview() {#showPreview}

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kImageFilePreview, qOverload<>(&KImageFilePreview::showPreview));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kImageFilePreview, [receiver = kImageFilePreview]() { receiver->showPreview(); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[override virtual slot\] void KImageFilePreview::showPreview(const QUrl &*url*) {#showPreview-1}

Reimplements: [KPreviewWidgetBase::showPreview(const QUrl &url)](kpreviewwidgetbase.md#showPreview).

Shows a preview for the given `url`.

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kImageFilePreview, qOverload<const QUrl &>(&KImageFilePreview::showPreview));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kImageFilePreview, [receiver = kImageFilePreview](const QUrl &url) { receiver->showPreview(url); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).

### \[protected slot\] void KImageFilePreview::showPreview(const QUrl &*url*, bool *force*) {#showPreview-2}

> **Note:** This slot is overloaded. To connect to this slot:
>
> ```
> // Connect using qOverload:
> connect(sender, &SenderClass::signal,
>         kImageFilePreview, qOverload<const QUrl &, bool>(&KImageFilePreview::showPreview));
>
> // Or using a lambda as wrapper:
> connect(sender, &SenderClass::signal,
>         kImageFilePreview, [receiver = kImageFilePreview](const QUrl &url, bool force) { receiver->showPreview(url, force); });
> ```
>
> For more examples and approaches, see [connecting to overloaded slots](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-slots).
