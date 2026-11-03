---
title: "KFileItemDelegate Class"
description: "KFileItemDelegate is intended to be used to provide a KDE file system view, when using one of the standard item views in Qt with KDirModel."
---

# KFileItemDelegate Class

[KFileItemDelegate](kfileitemdelegate.md) is intended to be used to provide a KDE file system view, when using one of the standard item views in Qt with [KDirModel](kdirmodel.md). [More...](#details)

- **Header:** `#include <KFileItemDelegate>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QAbstractItemDelegate](https://doc.qt.io/qt-6/qabstractitemdelegate.html)

[List of all members, including inherited members](kfileitemdelegate-members.md)

## Public Types

- [enum KFileItemDelegate::Information](#Information-enum)
- [KFileItemDelegate::InformationList](#InformationList-typedef)

## Properties

- [information : InformationList](#information-prop)
- [jobTransfersVisible : bool](#jobTransfersVisible-prop)
- [maximumSize : QSize](#maximumSize-prop)
- [shadowBlur : qreal](#shadowBlur-prop)
- [shadowColor : QColor](#shadowColor-prop)
- [shadowOffset : QPointF](#shadowOffset-prop)
- [showToolTipWhenElided : bool](#showToolTipWhenElided-prop)

## Public Functions

- [KFileItemDelegate(QObject \*parent = nullptr)](#KFileItemDelegate)
- [~KFileItemDelegate()](#dtor.KFileItemDelegate)
- [KFileItem fileItem(const QModelIndex &index) const](#fileItem) (since 6.14)
- [QRect iconRect(const QStyleOptionViewItem &option, const QModelIndex &index) const](#iconRect)
- [bool jobTransfersVisible() const](#jobTransfersVisible)
- [QSize maximumSize() const](#maximumSize)
- [void paint(QPainter \*painter, const QStyleOptionViewItem &option, const QModelIndex &index) const](#paint)
- [QRect selectionEmblemRect() const](#selectionEmblemRect) (since 6.14)
- [void setJobTransfersVisible(bool jobTransfersVisible)](#setJobTransfersVisible)
- [void setMaximumSize(const QSize &size)](#setMaximumSize)
- [void setSelectionEmblemRect(QRect rect, int iconSize)](#setSelectionEmblemRect) (since 6.14)
- [void setShadowBlur(qreal radius)](#setShadowBlur)
- [void setShadowColor(const QColor &color)](#setShadowColor)
- [void setShadowOffset(const QPointF &offset)](#setShadowOffset)
- [void setShowInformation(KFileItemDelegate::Information information)](#setShowInformation)
- [void setShowInformation(const KFileItemDelegate::InformationList &list)](#setShowInformation-1)
- [void setShowToolTipWhenElided(bool showToolTip)](#setShowToolTipWhenElided)
- [void setWrapMode(QTextOption::WrapMode wrapMode)](#setWrapMode)
- [qreal shadowBlur() const](#shadowBlur)
- [QColor shadowColor() const](#shadowColor)
- [QPointF shadowOffset() const](#shadowOffset)
- [KFileItemDelegate::InformationList showInformation() const](#showInformation)
- [bool showToolTipWhenElided() const](#showToolTipWhenElided)
- [QSize sizeHint(const QStyleOptionViewItem &option, const QModelIndex &index) const](#sizeHint)
- [QTextOption::WrapMode wrapMode() const](#wrapMode)

## Public Slots

- [QRegion shape(const QStyleOptionViewItem &option, const QModelIndex &index)](#shape)

## Detailed Description {#details}

While primarily intended to be used with [KDirModel](kdirmodel.md), it uses [Qt::DecorationRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) and [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) for the icons and text labels, just like [QItemDelegate](https://doc.qt.io/qt-6/qitemdelegate.html), and can thus be used with any standard model.

When used with [KDirModel](kdirmodel.md) however, [KFileItemDelegate](kfileitemdelegate.md) can change the way the display and/or decoration roles are drawn, based on properties of the file items. For example, if the file item is a symbolic link, it will use an italic font to draw the file name.

[KFileItemDelegate](kfileitemdelegate.md) also supports showing additional information about the file items below the icon labels.

Which information should be shown, if any, is controlled by the information property, which is a list that can be set by calling [setShowInformation](kfileitemdelegate.md#setShowInformation)(), and read by calling [showInformation](kfileitemdelegate.md#showInformation)(). By default this list is empty.

To use [KFileItemDelegate](kfileitemdelegate.md), instantiate an object from the delegate, and call setItemDelegate() in one of the standard item views in Qt:

```cpp
QListView *listview = new QListView(this);
KFileItemDelegate *delegate = new KFileItemDelegate(this);
listview->setItemDelegate(delegate);
```

## Member Type Documentation {#member-type-documentation}

### enum KFileItemDelegate::Information {#Information-enum}

This enum defines the additional information that can be displayed below item labels in icon views.

The information will only be shown for indexes for which the model provides a valid value for [KDirModel::FileItemRole](kdirmodel.md#AdditionalRoles-enum), and only when there's sufficient vertical space to display at least one line of the information, along with the display label.

For the number of items to be shown for folders, the model must provide a valid value for KDirMode::ChildCountRole, in addition to [KDirModel::FileItemRole](kdirmodel.md#AdditionalRoles-enum).

Note that [KFileItemDelegate](kfileitemdelegate.md) will not call [KFileItem::determineMimeType](../kiocore/kfileitem.md#determineMimeType)() if [KFileItem::isMimeTypeKnown](../kiocore/kfileitem.md#isMimeTypeKnown)() returns false, so if you want to display MIME types you should call [KFileItem::determineMimeType](../kiocore/kfileitem.md#determineMimeType)() yourself, to ensure that MIME types are resolved. If the MIME type isn't known, "Unknown" will be displayed until the MIME type has been successfully resolved.

| Constant | Value | Description |
| --- | --- | --- |
| `KFileItemDelegate::NoInformation` | `0` | No additional information will be shown for items. |
| `KFileItemDelegate::Size` | `1` | The file size for files, and the number of items for folders. |
| `KFileItemDelegate::Permissions` | `2` | A UNIX permissions string, e.g. -rwxr-xr-x. |
| `KFileItemDelegate::OctalPermissions` | `3` | The permissions as an octal value, e.g. 0644. |
| `KFileItemDelegate::Owner` | `4` | The user name of the file owner, e.g. root |
| `KFileItemDelegate::OwnerAndGroup` | `5` | The user and group that owns the file, e.g. root:root |
| `KFileItemDelegate::CreationTime` | `6` | The date and time the file/folder was created. |
| `KFileItemDelegate::ModificationTime` | `7` | The date and time the file/folder was last modified. |
| `KFileItemDelegate::AccessTime` | `8` | The date and time the file/folder was last accessed. |
| `KFileItemDelegate::MimeType` | `9` | The MIME type for the item, e.g. text/html. |
| `KFileItemDelegate::FriendlyMimeType` | `10` | The descriptive name for the MIME type, e.g. HTML Document. |
| `KFileItemDelegate::LinkDest (since Qt 4.5)` | `11` | The destination of a symbolic link. |
| `KFileItemDelegate::LocalPathOrUrl (since Qt 4.5)` | `12` | The local path to the file or the URL in case it is not a local file. |
| `KFileItemDelegate::Comment (since Qt 4.6)` | `13` | A simple comment that can be displayed to the user as is. |

*See also* [setShowInformation](kfileitemdelegate.md#setShowInformation)(), [showInformation](kfileitemdelegate.md#showInformation)(), [information](kfileitemdelegate.md#information-prop)

### KFileItemDelegate::InformationList {#InformationList-typedef}

## Property Documentation {#property-documentation}

### information : InformationList {#information-prop}

This property holds which additional information (if any) should be shown below items in icon views.

**Access functions:**

- `KFileItemDelegate::InformationList` **[showInformation](kfileitemdelegate.md#showInformation)**() const
- `void` **[setShowInformation](kfileitemdelegate.md#setShowInformation-1)**(const `KFileItemDelegate::InformationList` &*list*)
- `void` **[setShowInformation](kfileitemdelegate.md#setShowInformation)**(`KFileItemDelegate::Information` *information*)

### jobTransfersVisible : bool {#jobTransfersVisible-prop}

This property determines if there are KIO jobs on a destination URL visible, then they will have a small animation overlay displayed on them.

**Access functions:**

- `bool` **[jobTransfersVisible](kfileitemdelegate.md#jobTransfersVisible)**() const
- `void` **[setJobTransfersVisible](kfileitemdelegate.md#setJobTransfersVisible)**(`bool` *jobTransfersVisible*)

### maximumSize : QSize {#maximumSize-prop}

This property holds the maximum size that can be returned by [KFileItemDelegate::sizeHint](kfileitemdelegate.md#sizeHint)(). If the maximum size is empty, it will be ignored.

**Access functions:**

- `QSize` **[maximumSize](kfileitemdelegate.md#maximumSize)**() const
- `void` **[setMaximumSize](kfileitemdelegate.md#setMaximumSize)**(const `QSize` &*size*)

### shadowBlur : qreal {#shadowBlur-prop}

This property holds the blur radius for the text shadow. The default value for this property is 2.

**Access functions:**

- `qreal` **[shadowBlur](kfileitemdelegate.md#shadowBlur)**() const
- `void` **[setShadowBlur](kfileitemdelegate.md#setShadowBlur)**(`qreal` *radius*)

### shadowColor : QColor {#shadowColor-prop}

This property holds the color used for the text shadow.

The alpha value in the color determines the opacity of the shadow. Shadows are only rendered when the alpha value is non-zero. The default value for this property is [Qt::transparent](https://doc.qt.io/qt-6/qt.html#GlobalColor-enum).

**Access functions:**

- `QColor` **[shadowColor](kfileitemdelegate.md#shadowColor)**() const
- `void` **[setShadowColor](kfileitemdelegate.md#setShadowColor)**(const `QColor` &*color*)

### shadowOffset : QPointF {#shadowOffset-prop}

This property holds the horizontal and vertical offset for the text shadow. The default value for this property is (1, 1).

**Access functions:**

- `QPointF` **[shadowOffset](kfileitemdelegate.md#shadowOffset)**() const
- `void` **[setShadowOffset](kfileitemdelegate.md#setShadowOffset)**(const `QPointF` &*offset*)

### showToolTipWhenElided : bool {#showToolTipWhenElided-prop}

This property determines whether a tooltip will be shown by the delegate if the display role is elided. This tooltip will contain the full display role information. The tooltip will only be shown if the [Qt::ToolTipRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) differs from [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum), or if they match, [showToolTipWhenElided](kfileitemdelegate.md#showToolTipWhenElided) flag is set and the display role information is elided.

**Access functions:**

- `bool` **[showToolTipWhenElided](kfileitemdelegate.md#showToolTipWhenElided)**() const
- `void` **[setShowToolTipWhenElided](kfileitemdelegate.md#setShowToolTipWhenElided)**(`bool` *showToolTip*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFileItemDelegate::KFileItemDelegate(QObject \**parent* = nullptr) {#KFileItemDelegate}

Constructs a new [KFileItemDelegate](kfileitemdelegate.md).

`parent` The parent object for the delegate.

### \[override virtual noexcept\] KFileItemDelegate::~KFileItemDelegate() {#dtor.KFileItemDelegate}

Destroys the item delegate.

### \[since 6.14\] KFileItem KFileItemDelegate::fileItem(const QModelIndex &*index*) const {#fileItem}

This function was introduced in Qt 6.14.

### QRect KFileItemDelegate::iconRect(const QStyleOptionViewItem &*option*, const QModelIndex &*index*) const {#iconRect}

Returns the rectangle of the icon that is aligned inside the decoration rectangle.

### bool KFileItemDelegate::jobTransfersVisible() const {#jobTransfersVisible}

Returns whether or not the displaying of job transfers is enabled.

> **Note:** Getter function for property [jobTransfersVisible](kfileitemdelegate.md#jobTransfersVisible-prop).

*See also* [setJobTransfersVisible](kfileitemdelegate.md#setJobTransfersVisible)()

### QSize KFileItemDelegate::maximumSize() const {#maximumSize}

Returns the maximum size for [KFileItemDelegate::sizeHint](kfileitemdelegate.md#sizeHint)().

> **Note:** Getter function for property [maximumSize](kfileitemdelegate.md#maximumSize-prop).

*See also* [setMaximumSize](kfileitemdelegate.md#setMaximumSize)()

### \[override virtual\] void KFileItemDelegate::paint(QPainter \**painter*, const QStyleOptionViewItem &*option*, const QModelIndex &*index*) const {#paint}

Reimplements: [QAbstractItemDelegate::paint(QPainter \*painter, const QStyleOptionViewItem &option, const QModelIndex &index) const](https://doc.qt.io/qt-6/qabstractitemdelegate.html#paint).

Paints the item indicated by `index`, using `painter`.

The item will be drawn in the rectangle specified by option.rect. The correct size for that rectangle can be obtained by calling [sizeHint](kfileitemdelegate.md#sizeHint)().

This function will use the following data values if the model provides them for the item, in place of the values in `option`:

- [Qt::FontRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) The font that should be used for the display role.
- [Qt::TextAlignmentRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) The alignment of the display role.
- [Qt::ForegroundRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) The text color for the display role.
- [Qt::BackgroundRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) The background color for the item.

This function is reimplemented from [QAbstractItemDelegate](https://doc.qt.io/qt-6/qabstractitemdelegate.html).

`painter` The painter with which to draw the item.

`option` The style options that should be used when painting the item.

`index` The index to the item that should be painted.

### \[since 6.14\] QRect KFileItemDelegate::selectionEmblemRect() const {#selectionEmblemRect}

Returns the rectangle where selectionEmblem is being drawn

This function was introduced in Qt 6.14.

*See also* [setSelectionEmblemRect](kfileitemdelegate.md#setSelectionEmblemRect)()

### void KFileItemDelegate::setJobTransfersVisible(bool *jobTransfersVisible*) {#setJobTransfersVisible}

Enable/Disable the displaying of an animated overlay that is shown for any destination urls (in the view). When enabled, the animations (if any) will be drawn automatically.

Only the files/folders that are visible and have jobs associated with them will display the animation. You would likely not want this enabled if you perform some kind of custom painting that takes up a whole item, and will just make this(and what you paint) look funky.

Default is disabled.

Note: The model ([KDirModel](kdirmodel.md)) needs to have it's method called with the same value, when you make the call to this method.

> **Note:** Setter function for property [jobTransfersVisible](kfileitemdelegate.md#jobTransfersVisible-prop).

*See also* [jobTransfersVisible](kfileitemdelegate.md#jobTransfersVisible)()

### void KFileItemDelegate::setMaximumSize(const QSize &*size*) {#setMaximumSize}

Sets the maximum size for [KFileItemDelegate::sizeHint](kfileitemdelegate.md#sizeHint)().

> **Note:** Setter function for property [maximumSize](kfileitemdelegate.md#maximumSize-prop).

*See also* [maximumSize](kfileitemdelegate.md#maximumSize)()

### \[since 6.14\] void KFileItemDelegate::setSelectionEmblemRect(QRect *rect*, int *iconSize*) {#setSelectionEmblemRect}

Set the rectangle where selectionEmblem should be drawn in.

This function was introduced in Qt 6.14.

*See also* [selectionEmblemRect](kfileitemdelegate.md#selectionEmblemRect)()

### void KFileItemDelegate::setShadowBlur(qreal *radius*) {#setShadowBlur}

Sets the blur radius for the text shadow.

> **Note:** Setter function for property [shadowBlur](kfileitemdelegate.md#shadowBlur-prop).

*See also* [shadowBlur](kfileitemdelegate.md#shadowBlur)()

### void KFileItemDelegate::setShadowColor(const QColor &*color*) {#setShadowColor}

Sets the color used for drawing the text shadow.

To enable text shadows, set the shadow color to a non-transparent color. To disable text shadows, set the color to [Qt::transparent](https://doc.qt.io/qt-6/qt.html#GlobalColor-enum).

> **Note:** Setter function for property [shadowColor](kfileitemdelegate.md#shadowColor-prop).

*See also* [shadowColor](kfileitemdelegate.md#shadowColor)()

### void KFileItemDelegate::setShadowOffset(const QPointF &*offset*) {#setShadowOffset}

Sets the horizontal and vertical offset for the text shadow.

> **Note:** Setter function for property [shadowOffset](kfileitemdelegate.md#shadowOffset-prop).

*See also* [shadowOffset](kfileitemdelegate.md#shadowOffset)()

### void KFileItemDelegate::setShowInformation(KFileItemDelegate::Information *information*) {#setShowInformation}

Sets a single information line that is shown below the icon label in list views.

This is a convenience function for when you only want to show a single line of information.

`information` The information that should be shown

> **Note:** Setter function for property [information](kfileitemdelegate.md#information-prop).

*See also* [showInformation](kfileitemdelegate.md#showInformation)()

### void KFileItemDelegate::setShowInformation(const KFileItemDelegate::InformationList &*list*) {#setShowInformation-1}

Sets the list of information lines that are shown below the icon label in list views.

You will typically construct the list like this:

```cpp
KFileItemDelegate::InformationList list;
list << KFileItemDelegate::FriendlyMimeType << KFileItemDelegate::Size;
delegate->setShowInformation(list);
```

The information lines will be displayed in the list order. The delegate will first draw the item label, and then as many information lines as will fit in the available space.

`list` A list of information items that should be shown

> **Note:** Setter function for property [information](kfileitemdelegate.md#information-prop).

### void KFileItemDelegate::setShowToolTipWhenElided(bool *showToolTip*) {#setShowToolTipWhenElided}

Sets whether a tooltip should be shown if the display role is elided containing the full display role information.

> **Note:** The tooltip will only be shown if the [Qt::ToolTipRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) differs from [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum), or if they match, [showToolTipWhenElided](kfileitemdelegate.md#showToolTipWhenElided) flag is set and the display role information is elided.

> **Note:** Setter function for property [showToolTipWhenElided](kfileitemdelegate.md#showToolTipWhenElided-prop).

*See also* [showToolTipWhenElided](kfileitemdelegate.md#showToolTipWhenElided)()

### void KFileItemDelegate::setWrapMode(QTextOption::WrapMode *wrapMode*) {#setWrapMode}

When the contents text needs to be wrapped, `wrapMode` strategy will be followed.

*See also* [wrapMode](kfileitemdelegate.md#wrapMode)()

### qreal KFileItemDelegate::shadowBlur() const {#shadowBlur}

Returns the blur radius for the text shadow.

> **Note:** Getter function for property [shadowBlur](kfileitemdelegate.md#shadowBlur-prop).

*See also* [setShadowBlur](kfileitemdelegate.md#setShadowBlur)()

### QColor KFileItemDelegate::shadowColor() const {#shadowColor}

Returns the color used for the text shadow.

> **Note:** Getter function for property [shadowColor](kfileitemdelegate.md#shadowColor-prop).

*See also* [setShadowColor](kfileitemdelegate.md#setShadowColor)()

### QPointF KFileItemDelegate::shadowOffset() const {#shadowOffset}

Returns the offset used for the text shadow.

> **Note:** Getter function for property [shadowOffset](kfileitemdelegate.md#shadowOffset-prop).

*See also* [setShadowOffset](kfileitemdelegate.md#setShadowOffset)()

### \[slot\] QRegion KFileItemDelegate::shape(const QStyleOptionViewItem &*option*, const QModelIndex &*index*) {#shape}

Returns the shape of the item as a region.

The returned region can be used for precise hit testing of the item.

### KFileItemDelegate::InformationList KFileItemDelegate::showInformation() const {#showInformation}

Returns the file item information that should be shown below item labels in list views.

> **Note:** Getter function for property [information](kfileitemdelegate.md#information-prop).

*See also* [setShowInformation](kfileitemdelegate.md#setShowInformation)()

### bool KFileItemDelegate::showToolTipWhenElided() const {#showToolTipWhenElided}

Returns whether a tooltip should be shown if the display role is elided containing the full display role information.

> **Note:** The tooltip will only be shown if the [Qt::ToolTipRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) differs from [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum), or if they match, showToolTipWhenElided flag is set and the display role information is elided.

> **Note:** Getter function for property [showToolTipWhenElided](kfileitemdelegate.md#showToolTipWhenElided-prop).

*See also* [setShowToolTipWhenElided](kfileitemdelegate.md#setShowToolTipWhenElided)()

### \[override virtual\] QSize KFileItemDelegate::sizeHint(const QStyleOptionViewItem &*option*, const QModelIndex &*index*) const {#sizeHint}

Reimplements: [QAbstractItemDelegate::sizeHint(const QStyleOptionViewItem &option, const QModelIndex &index) const](https://doc.qt.io/qt-6/qabstractitemdelegate.html#sizeHint).

Returns the nominal size for the item referred to by `index`, given the provided options.

If the model provides a valid [Qt::FontRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) and/or [Qt::TextAlignmentRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) for the item, those will be used instead of the ones specified in the style options.

This function is reimplemented from [QAbstractItemDelegate](https://doc.qt.io/qt-6/qabstractitemdelegate.html).

`option` The style options that should be used when painting the item.

`index` The index to the item for which to return the size hint.

### QTextOption::WrapMode KFileItemDelegate::wrapMode() const {#wrapMode}

Returns the wrapping strategy followed to show text when it needs wrapping.

*See also* [setWrapMode](kfileitemdelegate.md#setWrapMode)()
