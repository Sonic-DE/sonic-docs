---
title: "PageRow QML Type"
description: "A row-based navigation model that can be used with a set of interlinked information pages."
---

# PageRow QML Type

A row-based navigation model that can be used with a set of interlinked information pages. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Control](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html)

## Detailed Description {#details}

Pages are pushed in the back of the row and the view scrolls until that row is visualized. A [PageRow](qml-org-kde-kirigami-pagerow.md) can show a single page or a multiple set of columns, depending on the window width: on a phone a single column should be fullscreen, while on a tablet or a desktop more than one column should be visible.

## Property Documentation {#property-documentation}

### columnView : ColumnView {#columnView-prop}

This property holds the [ColumnView](qml-org-kde-kirigami-layouts-columnview.md) that this [PageRow](qml-org-kde-kirigami-pagerow.md) owns.

Generally, you shouldn't need to change the value of this property.

### currentIndex : int {#currentIndex-prop}

This property holds the index of the currently active page.

*See also* [currentItem](qml-org-kde-kirigami-pagerow.md#currentItem-prop)

### \[read-only\] currentItem : Page {#currentItem-prop}

This property holds the currently visible/active page.

Because of the ability to display multiple pages, it will hold the currently active page.

### defaultColumnWidth : int {#defaultColumnWidth-prop}

This property holds the default width for a column.

default: `20 * Kirigami.Units.gridUnit`

> **Note:** Pages can override it using implicitWidth, Layout.fillWidth, Layout.minimumWidth etc.

### \[read-only\] depth : int {#depth-prop}

This property holds the number of pages currently pushed onto the view.

### \[read-only\] globalToolBar : var {#globalToolBar-prop}

This property sets the appearance of an optional global toolbar for the whole [PageRow](qml-org-kde-kirigami-pagerow.md).

It's a grouped property comprised of the following properties:

- style (Kirigami.ApplicationHeaderStyle): can have the following values:
   
   - Auto: Depending on application formfactor, it can behave automatically like other values, such as a Breadcrumb on mobile and [ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html) on desktop.
   - Breadcrumb: It will show a breadcrumb of all the page titles in the stack, for easy navigation.
   - Titles: Each page will only have its own title on top.
   - [ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html): Each page will have the title on top together buttons and menus to represent all of the page actions. Not available on Mobile systems.
   - None: No global toolbar will be shown.
- actualStyle: This will represent the actual style of the toolbar; it can be different from style in the case style is Auto.
- showNavigationButtons: OR flags combination of Kirigami.ApplicationHeaderStyle.ShowBackButton and Kirigami.ApplicationHeaderStyle.ShowForwardButton.
- toolbarActionAlignment ([Qt::Alignment](https://doc.qt.io/qt-6/qt.html#AlignmentFlag-enum)): How to horizontally align the actions when using the [ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html) style. Note that anything but Qt.AlignRight will cause the title to be hidden (default: Qt.AlignRight).
- minimumHeight: int Minimum height of the header, which will be resized when scrolling. Only in Mobile mode (default: preferredHeight, sliding but no scaling).
- preferredHeight: int The height the toolbar will usually have.
- leftReservedSpace: int, readonly How many pixels of extra space are reserved at the left of the page toolbar (typically for navigation buttons or a drawer handle).
- rightReservedSpace: int, readonly How many pixels of extra space are reserved at the right of the page toolbar (typically for a drawer handle).

### initialPage : Page {#initialPage-prop}

This property sets the initial page for this [PageRow](qml-org-kde-kirigami-pagerow.md).

### interactive : bool {#interactive-prop}

This property sets whether it is possible to go back/forward by swiping with a gesture on the content view.

default: `true`, except on Android where it conflicts with native back/forward swipe gestures.

### \[read-only\] items : Page {#items-prop}

This property holds the present pages in the [PageRow](qml-org-kde-kirigami-pagerow.md).

### \[read-only\] lastItem : Page {#lastItem-prop}

This property holds the last page in the row.

### layers : QtQuick.Controls.StackView {#layers-prop}

This property holds the modal layers.

Sometimes an application needs a modal page that always covers all the rows. For instance the full screen image of an image viewer or a settings page.

### \[read-only\] leadingVisibleItem : Item {#leadingVisibleItem-prop}

This property holds the first page in the [PageRow](qml-org-kde-kirigami-pagerow.md) that is at least partially visible.

> **Note:** Pages before that one (the one contained in the property) will be out of the viewport.

*See also* [ColumnView::leadingVisibleItem](qml-org-kde-kirigami-layouts-columnview.md#leadingVisibleItem-prop)

### leftSidebar : OverlayDrawer {#leftSidebar-prop}

This property assigns a drawer as an internal left sidebar for this [PageRow](qml-org-kde-kirigami-pagerow.md).

In this case, when open and not modal, the drawer contents will be in the same layer as the base pagerow. Pushing any other layer on top will cover the sidebar.

### popHiddenPages : bool {#popHiddenPages-prop}

This property holds whether to automatically pop pages at the top of the stack if they are not visible.

If a user navigates to a previous page on the stack (ex. pressing back button) and pages above it on the stack are not visible, they will be popped if this property is true.

### separatorVisible : bool {#separatorVisible-prop}

This property sets whether the separators between pages should be displayed.

default: `true`

### \[read-only\] trailingVisibleItem : Item {#trailingVisibleItem-prop}

This property holds the last page in the [PageRow](qml-org-kde-kirigami-pagerow.md) that is at least partially visible.

> **Note:** Pages after that one (the one contained in the property) will be out of the viewport.

*See also* [ColumnView::trailingVisibleItem](qml-org-kde-kirigami-layouts-columnview.md#trailingVisibleItem-prop)

### \[read-only\] visibleItems : Page {#visibleItems-prop}

This property holds all visible pages in the [PageRow](qml-org-kde-kirigami-pagerow.md), excluding those which are scrolled away.

### \[read-only\] wideMode : bool {#wideMode-prop}

This property tells whether the [PageRow](qml-org-kde-kirigami-pagerow.md) is wide enough to show multiple pages.

## Signal Documentation {#signal-documentation}

### pageInserted(int *position*, Item *page*) {#pageInserted-signal}

Emitted when a page has been inserted anywhere. `position` where the page has been inserted `page` the new page

> **Note:** The corresponding handler is `onPageInserted`.

### pagePushed(Item *page*) {#pagePushed-signal}

Emitted when a page has been pushed to the bottom. `page` the new page

> **Note:** The corresponding handler is `onPagePushed`.

### pageRemoved(Item *page*) {#pageRemoved-signal}

Emitted when a page has been removed from the row. `page` the page that has been removed: at this point it's still valid, but may be auto deleted soon.

> **Note:** The corresponding handler is `onPageRemoved`.

## Method Documentation {#method-documentation}

### void clear() {#clear-method}

Clears the page stack.

Destroy (or reparent) all the pages contained.

### void flickBack() {#flickBack-method}

Go back to the previous index and scroll to the left to show one more column.

### Page get(int *idx*) {#get-method}

`idx` the depth of the page we want

Returns the page at idx

### void goBack(var *event* = null) {#goBack-method}

Acts as if you had pressed the "back" button on Android or did Alt-Left on desktop, "going back" in the layers and page row. Results in a layer being popped if available, or the [currentIndex](qml-org-kde-kirigami-pagerow.md#currentIndex-prop) being set to [currentIndex](qml-org-kde-kirigami-pagerow.md#currentIndex-prop)-1 if not available.

`event` Optional, an event that will be accepted if a page is successfully "backed" on

### void goForward() {#goForward-method}

Acts as if you had pressed the "forward" shortcut on desktop, "going forward" in the page row. Results in the active page becoming the next page in the row from the current active page, i.e. [currentIndex](qml-org-kde-kirigami-pagerow.md#currentIndex-prop) + 1.

### Page insertPage(int *position*, var *page*, var *properties*) {#insertPage-method}

Inserts a new page or a list of new pages at an arbitrary `position`.

A single page can be defined as an url, a component, or an object. It can also be an array of the above said types, but in that case, the properties' array length must match pages' array length or it must be empty. Failing to comply with the following rules will make the method return null before doing anything.

`page` A single page or an array of pages.

`properties` A single property object or an array of property objects.

Returns the new created page (or the last one if it was an array).

### void movePage(int *fromPos*, int *toPos*) {#movePage-method}

Move the page at position `fromPos` to the new position `toPos`.

If needed, [currentIndex](qml-org-kde-kirigami-pagerow.md#currentIndex-prop) will be adjusted in order to keep the same current page.

### Page pop(var *page*) {#pop-method}

Pops a page off the stack. `page` If page is specified then the stack is unwound to that page, to unwind to the first page specify page as null.

Returns the page instance that was popped off the stack.

### Page push(var *page*, var *properties*) {#push-method}

This method pushes a page on the stack.

A single page can be defined as an url, a component, or an object. It can also be an array of the above said types, but in that case, the properties' array length must match pages' array length or it must be empty. Failing to comply with the following rules will make the method return null before doing anything.

`page` A single page or an array of pages.

`properties` A single property object or an array of property objects.

Returns The new created page (or the last one if it was an array).

### Page pushDialogLayer(var *page*, var *properties*, var *windowProperties*) {#pushDialogLayer-method}

Pushes a page as a new dialog on desktop and as a layer on mobile.

`page` A single page defined as either a string url, a component or an object (which will be reparented). The following page can then be closed by calling \`Kirigami.[PageStack](qml-org-kde-kirigami-layouts-pagestack.md).closeDialog()\` at most once to close/hide it when in desktop or mobile mode.

> **Note:** : You can also call a closeDialog() method directly on the page to close/hide it but this behavior is deprecated since 6.18 and replaced with the attached property.

`properties` The properties given when initializing the page.

`windowProperties` The properties given to the initialized window on desktop.

Returns a newly created page.

### Page removePage(var *page*) {#removePage-method}

Remove the given page.

`page` The page can be given both as integer position or by reference

Returns the page that has just been removed

### Page replace(var *page*, var *properties*) {#replace-method}

Replaces a page on the current index.

A single page can be defined as an url, a component, or an object. It can also be an array of the above said types, but in that case, the properties' array length must match pages' array length or it must be empty. Failing to comply with the following rules will make the method return null before doing anything.

`page` A single page or an array of pages.

`properties` A single property object or an array of property objects.

Returns the new created page (or the last one if it was an array). See [push](qml-org-kde-kirigami-pagerow.md#push-method)() for details.
