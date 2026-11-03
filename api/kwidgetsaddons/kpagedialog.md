---
title: "KPageDialog Class"
description: "A dialog base class which can handle multiple pages."
---

# KPageDialog Class

A dialog base class which can handle multiple pages. [More...](#details)

- **Header:** `#include <KPageDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)
- **Inherited By:** [KAssistantDialog](kassistantdialog.md)

[List of all members, including inherited members](kpagedialog-members.md)

## Public Types

- [enum KPageDialog::FaceType](#FaceType-enum)

## Public Functions

- [KPageDialog(QWidget \*parent = nullptr, Qt::WindowFlags flags = WindowFlags())](#KPageDialog)
- [void addActionButton(QAbstractButton \*button)](#addActionButton)
- [void addPage(KPageWidgetItem \*item)](#addPage)
- [KPageWidgetItem \*addPage(QWidget \*widget, const QString &name)](#addPage-1)
- [void addSubPage(KPageWidgetItem \*parent, KPageWidgetItem \*item)](#addSubPage)
- [KPageWidgetItem \*addSubPage(KPageWidgetItem \*parent, QWidget \*widget, const QString &name)](#addSubPage-1)
- [QPushButton \*button(QDialogButtonBox::StandardButton which) const](#button)
- [KPageWidgetItem \*currentPage() const](#currentPage)
- [void insertPage(KPageWidgetItem \*before, KPageWidgetItem \*item)](#insertPage)
- [KPageWidgetItem \*insertPage(KPageWidgetItem \*before, QWidget \*widget, const QString &name)](#insertPage-1)
- [void removePage(KPageWidgetItem \*item)](#removePage)
- [void setCurrentPage(KPageWidgetItem \*item)](#setCurrentPage)
- [void setFaceType(KPageDialog::FaceType faceType)](#setFaceType)
- [void setStandardButtons(QDialogButtonBox::StandardButtons buttons)](#setStandardButtons)

## Signals

- [void currentPageChanged(KPageWidgetItem \*current, KPageWidgetItem \*before)](#currentPageChanged)
- [void pageRemoved(KPageWidgetItem \*page)](#pageRemoved)

## Protected Functions

- [KPageDialog(KPageWidget \*widget, QWidget \*parent, Qt::WindowFlags flags = WindowFlags())](#KPageDialog-1)
- [QDialogButtonBox \*buttonBox()](#buttonBox)
- [const QDialogButtonBox \*buttonBox() const](#buttonBox-1)
- [KPageWidget \*pageWidget()](#pageWidget)
- [const KPageWidget \*pageWidget() const](#pageWidget-1)
- [void setButtonBox(QDialogButtonBox \*box)](#setButtonBox)
- [void setPageWidget(KPageWidget \*widget)](#setPageWidget)

## Detailed Description {#details}

This class provides a dialog base class which handles multiple pages and allows the user to switch between these pages in different ways.

Currently, Auto, Plain, List, Tree and Tabbed face types are available (cmp. [KPageView](kpageview.md)).

By default a [QDialogButtonBox](https://doc.qt.io/qt-6/qdialogbuttonbox.html) is added to the dialog with two buttons, OK ([QDialogButtonBox::Ok](https://doc.qt.io/qt-6/qdialogbuttonbox.html#StandardButton-enum)) and Cancel ([QDialogButtonBox::Cancel](https://doc.qt.io/qt-6/qdialogbuttonbox.html#StandardButton-enum)). You can customize which buttons are added to the dialog by using any of the available buttons-related methods.

Note that if there is a [QDialogButtonBox](https://doc.qt.io/qt-6/qdialogbuttonbox.html) (either the one added by default, or one you added manually) some logical connections are created:

- [QDialogButtonBox::accepted](https://doc.qt.io/qt-6/qdialogbuttonbox.html#accepted)() is connected to [QDialog::accept](https://doc.qt.io/qt-6/qdialog.html#accept)()
- [QDialogButtonBox::rejected](https://doc.qt.io/qt-6/qdialogbuttonbox.html#rejected)() is connected to [QDialog::reject](https://doc.qt.io/qt-6/qdialog.html#reject)()

this means that you shouldn't create these connections again (otherwise you would end up receiving two duplicate [accepted](https://doc.qt.io/qt-6/qdialog.html#accepted)() signals for example).

Example:

```cpp
UrlDialog::UrlDialog( QWidget *parent )
  : KPageDialog( parent )
{
  setFaceType(List);

  QLabel *label = new QLabel("Test Page");
  addPage(label, i18n("My Test Page"));

  label = new QLabel("Second Test Page");
  KPageWidgetItem *page = new KPageWidgetItem(label, i18n("My Second Test Page"));
  page->setHeader(i18n("My header string"));
  page->setIcon(QIcon::fromTheme("file"));

  addPage(page);

  // Change the buttons added to the dialog
  setStandardButtons(QDialogButtonBox::Ok | QDialogButtonBox::Apply | QDialogButtonBox::Cancel);

  // Alternatively you can create a QDialogButtonBox, add the buttons you want to it,
  // then add that button box to the dialog
  QDialogButtonBox *btnBox = new QDialogButtonBox(QDialogButtonBox::Ok | QDialogButtonBox::Apply | QDialogButtonBox::Cancel,
                                                  Qt::Horizontal,
                                                  this);
  setButtonBox(btnBox);
}
```

## Member Type Documentation {#member-type-documentation}

### enum KPageDialog::FaceType {#FaceType-enum}

The face types supported.

| Constant | Value | Description |
| --- | --- | --- |
| `KPageDialog::Auto` | `KPageView::Auto` | A dialog with a face based on the structure of the available pages. If only a single page is added, the dialog behaves like in Plain mode, with multiple pages without sub pages it behaves like in List mode and like in Tree mode otherwise. |
| `KPageDialog::Plain` | `KPageView::Plain` | A normal dialog |
| `KPageDialog::List` | `KPageView::List` | A dialog with an icon list on the left side and a representation of the contents on the right side |
| `KPageDialog::Tree` | `KPageView::Tree` | A dialog with a tree on the left side and a representation of the contents on the right side |
| `KPageDialog::Tabbed` | `KPageView::Tabbed` | A dialog with a tab bar above the representation of the contents |
| `KPageDialog::FlatList` | `KPageView::FlatList` | A dialog with an flat list with small icons on the left side and a representation of the contents on the right side |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPageDialog::KPageDialog(QWidget \**parent* = nullptr, Qt::WindowFlags *flags* = Qt::WindowFlags()) {#KPageDialog}

Creates a new page dialog.

### \[protected\] KPageDialog::KPageDialog(KPageWidget \**widget*, QWidget \**parent*, Qt::WindowFlags *flags* = Qt::WindowFlags()) {#KPageDialog-1}

This constructor can be used by subclasses to provide a custom page widget.

`widget` The [KPageWidget](kpagewidget.md) object will be reparented to this object, so you can create it without parent and you are not allowed to delete it.

### void KPageDialog::addActionButton(QAbstractButton \**button*) {#addActionButton}

Set an action button.

### void KPageDialog::addPage(KPageWidgetItem \**item*) {#addPage}

Adds a new top level page to the dialog.

`item` The [KPageWidgetItem](kpagewidgetitem.md) which describes the page.

### KPageWidgetItem \*KPageDialog::addPage(QWidget \**widget*, const QString &*name*) {#addPage-1}

Adds a new top level page to the dialog.

`widget` The widget of the page.

`name` The name which is displayed in the navigation view.

Returns the associated [KPageWidgetItem](kpagewidgetitem.md).

### void KPageDialog::addSubPage(KPageWidgetItem \**parent*, KPageWidgetItem \**item*) {#addSubPage}

Inserts a new sub page in the dialog.

`parent` The new page will be insert as child of this [KPageWidgetItem](kpagewidgetitem.md).

`item` The [KPageWidgetItem](kpagewidgetitem.md) which describes the page.

### KPageWidgetItem \*KPageDialog::addSubPage(KPageWidgetItem \**parent*, QWidget \**widget*, const QString &*name*) {#addSubPage-1}

Inserts a new sub page in the dialog.

`parent` The new page will be insert as child of this [KPageWidgetItem](kpagewidgetitem.md).

`widget` The widget of the page.

`name` The name which is displayed in the navigation view.

Returns the associated [KPageWidgetItem](kpagewidgetitem.md).

### QPushButton \*KPageDialog::button(QDialogButtonBox::StandardButton *which*) const {#button}

Returns the [QPushButton](https://doc.qt.io/qt-6/qpushbutton.html) corresponding to the standard button which, or a null pointer if the standard button doesn't exist in this dialog.

### \[protected\] QDialogButtonBox \*KPageDialog::buttonBox() {#buttonBox}

Returns the button box of the dialog or a null pointer if no button box is set.

*See also* [setButtonBox](kpagedialog.md#setButtonBox)()

### \[protected\] const QDialogButtonBox \*KPageDialog::buttonBox() const {#buttonBox-1}

Returns the button box of the dialog or a null pointer if no button box is set.

### KPageWidgetItem \*KPageDialog::currentPage() const {#currentPage}

Returns the [KPageWidgetItem](kpagewidgetitem.md) for the current page or a null pointer if there is no current page.

*See also* [setCurrentPage](kpagedialog.md#setCurrentPage)()

### \[signal\] void KPageDialog::currentPageChanged(KPageWidgetItem \**current*, KPageWidgetItem \**before*) {#currentPageChanged}

This signal is emitted whenever the current page has changed.

`current` The new current page or a null pointer if no current page is available.

`before` The page that was current before the new current page has changed.

### void KPageDialog::insertPage(KPageWidgetItem \**before*, KPageWidgetItem \**item*) {#insertPage}

Inserts a new page in the dialog.

`before` The new page will be insert before this [KPageWidgetItem](kpagewidgetitem.md) on the same level in hierarchy.

`item` The [KPageWidgetItem](kpagewidgetitem.md) which describes the page.

### KPageWidgetItem \*KPageDialog::insertPage(KPageWidgetItem \**before*, QWidget \**widget*, const QString &*name*) {#insertPage-1}

Inserts a new page in the dialog.

`before` the new page will be insert before this [KPageWidgetItem](kpagewidgetitem.md) on the same level in hierarchy.

`widget` the widget of the page.

`name` the name which is displayed in the navigation view.

Returns the associated [KPageWidgetItem](kpagewidgetitem.md).

### \[signal\] void KPageDialog::pageRemoved(KPageWidgetItem \**page*) {#pageRemoved}

This signal is emitted whenever a page has been removed.

`page` The page which has been removed

### \[protected\] KPageWidget \*KPageDialog::pageWidget() {#pageWidget}

Returns the page widget of the dialog or a null pointer if no page widget is set.

*See also* [setPageWidget](kpagedialog.md#setPageWidget)()

### \[protected\] const KPageWidget \*KPageDialog::pageWidget() const {#pageWidget-1}

Returns the page widget of the dialog or a null pointer if no page widget is set.

### void KPageDialog::removePage(KPageWidgetItem \**item*) {#removePage}

Removes the page associated with the given [KPageWidgetItem](kpagewidgetitem.md).

### \[protected\] void KPageDialog::setButtonBox(QDialogButtonBox \**box*) {#setButtonBox}

Set the button box of the dialog

> **Note:** the previous [buttonBox](kpagedialog.md#buttonBox) will be deleted.

`box` The [QDialogButtonBox](https://doc.qt.io/qt-6/qdialogbuttonbox.html) object will be reparented to this object, so you can create it without parent and you are not allowed to delete it.

*See also* [buttonBox](kpagedialog.md#buttonBox)()

### void KPageDialog::setCurrentPage(KPageWidgetItem \**item*) {#setCurrentPage}

Sets the page which is associated with the given [KPageWidgetItem](kpagewidgetitem.md) to be the current page and emits the [currentPageChanged](kpagedialog.md#currentPageChanged)() signal.

*See also* [currentPage](kpagedialog.md#currentPage)()

### void KPageDialog::setFaceType(KPageDialog::FaceType *faceType*) {#setFaceType}

Sets the face type of the dialog.

### \[protected\] void KPageDialog::setPageWidget(KPageWidget \**widget*) {#setPageWidget}

Set the page widget of the dialog.

> **Note:** the previous [pageWidget](kpagedialog.md#pageWidget) will be deleted.

`widget` The [KPageWidget](kpagewidget.md) object will be reparented to this object, so you can create it without parent and you are not allowed to delete it.

*See also* [pageWidget](kpagedialog.md#pageWidget)()

### void KPageDialog::setStandardButtons(QDialogButtonBox::StandardButtons *buttons*) {#setStandardButtons}

Sets the collection of standard buttons displayed by this dialog.
