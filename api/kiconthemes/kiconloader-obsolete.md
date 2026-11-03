---
title: "Obsolete Members for KIconLoader"
description: "Deprecated members of KIconLoader."
parent: "kiconthemes/kiconloader"
---

# Obsolete Members for KIconLoader

**The following members of class [KIconLoader](kiconloader.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void drawOverlays(const QStringList &overlays, QPixmap &pixmap, KIconLoader::Group group, int state = KIconLoader::DefaultState) const](#drawOverlays) (deprecated in 6.5)
- [KIconEffect \*iconEffect() const](#iconEffect) (deprecated in 6.5)
- [QStringList loadAnimated(const QString &name, KIconLoader::Group group, int size = 0) const](#loadAnimated) (deprecated in 6.5)
- [QMovie \*loadMovie(const QString &name, KIconLoader::Group group, int size = 0, QObject \*parent = nullptr) const](#loadMovie) (deprecated in 6.5)
- [QPixmap loadScaledIcon(const QString &name, KIconLoader::Group group, qreal scale, int size = 0, int state = KIconLoader::DefaultState, const QStringList &overlays = QStringList(), QString \*path\_store = nullptr, bool canReturnNull = false) const](#loadScaledIcon-1) (deprecated in 6.31)
- [QString moviePath(const QString &name, KIconLoader::Group group, int size = 0) const](#moviePath) (deprecated in 6.5)

## Public Slots

- [void newIconLoader()](#newIconLoader) (deprecated in 5.0)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.5\] void KIconLoader::drawOverlays(const QStringList &*overlays*, QPixmap &*pixmap*, KIconLoader::Group *group*, int *state* = KIconLoader::DefaultState) const {#drawOverlays}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Draws overlays on the specified pixmap, it takes the width and height of the pixmap into consideration

`overlays` List of up to 4 overlays to blend over the pixmap. The first overlay will be in the bottom right corner, followed by bottom left, top left and top right. An empty [QString](https://doc.qt.io/qt-6/qstring.html) can be used to leave the specific position blank.

`pixmap` to draw on Use KIconUtils::addOverlays from KGuiAddons

### \[deprecated in 6.5\] KIconEffect \*KIconLoader::iconEffect() const {#iconEffect}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Returns a pointer to the [KIconEffect](kiconeffect.md) object used by the icon loader. Returns the [KIconEffect](kiconeffect.md).

use the static [KIconEffect](kiconeffect.md) API

### \[deprecated in 6.5\] QStringList KIconLoader::loadAnimated(const QString &*name*, KIconLoader::Group *group*, int *size* = 0) const {#loadAnimated}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Loads an animated icon as a series of still frames. If you want to load a .mng animation as [QMovie](https://doc.qt.io/qt-6/qmovie.html) instead, please use [loadMovie](kiconloader-obsolete.md#loadMovie)() instead.

`name` The name of the icon.

`group` The icon group. See [loadIcon](kiconloader.md#loadIcon)().

`size` Override the default size for `group`. See [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum).

Returns a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) containing the absolute path of all the frames making up the animation.

use [QMovie](https://doc.qt.io/qt-6/qmovie.html) API

### \[deprecated in 6.5\] QMovie \*KIconLoader::loadMovie(const QString &*name*, KIconLoader::Group *group*, int *size* = 0, QObject \**parent* = nullptr) const {#loadMovie}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Loads an animated icon.

`name` The name of the icon.

`group` The icon group. See [loadIcon](kiconloader.md#loadIcon)().

`size` Override the default size for `group`. See [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum).

`parent` The parent object of the returned [QMovie](https://doc.qt.io/qt-6/qmovie.html).

Returns A [QMovie](https://doc.qt.io/qt-6/qmovie.html) object. Can be null if not found or not valid. Ownership is passed to the caller. use [QMovie](https://doc.qt.io/qt-6/qmovie.html) API

### \[deprecated in 6.31\] QPixmap KIconLoader::loadScaledIcon(const QString &*name*, KIconLoader::Group *group*, qreal *scale*, int *size* = 0, int *state* = KIconLoader::DefaultState, const QStringList &*overlays* = QStringList(), QString \**path\_store* = nullptr, bool *canReturnNull* = false) const {#loadScaledIcon-1}

This function is deprecated since 6.31. We strongly advise against using it in new code.

Loads an icon. It will try very hard to find an icon which is suitable. If no exact match is found, a close match is searched. If neither an exact nor a close match is found, a null pixmap or the "unknown" pixmap is returned, depending on the value of the `canReturnNull` parameter.

`name` The name of the icon, without extension.

`group` The icon group. This will specify the size of and effects to be applied to the icon.

`scale` The scale of the icon group to use. If no icon exists in the scaled group, a 1x icon with its size multiplied by the scale will be loaded instead.

`size` If nonzero, this overrides the size specified by `group`. See [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum).

`state` The icon state: `DefaultState`, `ActiveState` or `DisabledState`. Depending on the user's preferences, the iconloader may apply a visual effect to hint about its state.

`overlays` a list of emblem icons to overlay, by name

`path_store` If not null, the path of the icon is stored here, if the icon was found. If the icon was not found `path_store` is unaltered even if the "unknown" pixmap was returned.

`canReturnNull` Can return a null pixmap? If false, the "unknown" pixmap is returned when no appropriate icon has been found. Note: a null pixmap can still be returned in the event of invalid parameters, such as empty names, negative sizes, and etc.

Returns the [QPixmap](https://doc.qt.io/qt-6/qpixmap.html). Can be null when not found, depending on `canReturnNull`. use the overload with [QSize](https://doc.qt.io/qt-6/qsize.html) type size argument

*See also* [drawOverlays](kiconloader-obsolete.md#drawOverlays)

### \[deprecated in 6.5\] QString KIconLoader::moviePath(const QString &*name*, KIconLoader::Group *group*, int *size* = 0) const {#moviePath}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Returns the path to an animated icon.

`name` The name of the icon.

`group` The icon group. See [loadIcon](kiconloader.md#loadIcon)().

`size` Override the default size for `group`. See [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum).

Returns the full path to the movie, ready to be passed to [QMovie](https://doc.qt.io/qt-6/qmovie.html)'s constructor.

Empty string if not found. use [QMovie](https://doc.qt.io/qt-6/qmovie.html) API

### \[slot, deprecated in 5.0\] void KIconLoader::newIconLoader() {#newIconLoader}

This function is deprecated since 5.0. We strongly advise against using it in new code.

Re-initialize the global icon loader

Use [emitChange](kiconloader.md#emitChange)(Group)
