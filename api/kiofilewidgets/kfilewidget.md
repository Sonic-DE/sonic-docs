---
title: "KFileWidget Class"
description: "File selector widget."
---

# KFileWidget Class

File selector widget. [More...](#details)

- **Header:** `#include <KFileWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kfilewidget-members.md)  
[Deprecated members](kfilewidget-obsolete.md)

## Public Types

- [enum KFileWidget::OperationMode](#OperationMode-enum)

## Public Functions

- [KFileWidget(const QUrl &startDir, QWidget \*parent = nullptr)](#KFileWidget)
- [QUrl baseUrl() const](#baseUrl)
- [QPushButton \*cancelButton() const](#cancelButton)
- [void clearFilter()](#clearFilter)
- [KFileFilter currentFilter() const](#currentFilter) (since 6.0)
- [QSize dialogSizeHint() const](#dialogSizeHint)
- [KDirOperator \*dirOperator()](#dirOperator)
- [KFileFilterCombo \*filterWidget() const](#filterWidget)
- [bool keepsLocation() const](#keepsLocation)
- [KUrlComboBox \*locationEdit() const](#locationEdit)
- [KFile::Modes mode() const](#mode)
- [QPushButton \*okButton() const](#okButton)
- [KFileWidget::OperationMode operationMode() const](#operationMode)
- [QString selectedFile() const](#selectedFile)
- [QStringList selectedFiles() const](#selectedFiles)
- [QUrl selectedUrl() const](#selectedUrl)
- [QList\<QUrl\> selectedUrls() const](#selectedUrls)
- [void setConfirmOverwrite(bool enable)](#setConfirmOverwrite)
- [void setCustomWidget(QWidget \*widget)](#setCustomWidget)
- [void setCustomWidget(const QString &text, QWidget \*widget)](#setCustomWidget-1)
- [void setFilters(const QList\<KFileFilter\> &filters, const KFileFilter &activeFilter = KFileFilter())](#setFilters) (since 6.0)
- [void setInlinePreviewShown(bool show)](#setInlinePreviewShown)
- [void setKeepLocation(bool keep)](#setKeepLocation)
- [void setLocationLabel(const QString &text)](#setLocationLabel)
- [void setMode(KFile::Modes m)](#setMode)
- [void setOperationMode(KFileWidget::OperationMode)](#setOperationMode)
- [void setSelectedUrl(const QUrl &url)](#setSelectedUrl)
- [void setSelectedUrls(const QList\<QUrl\> &urls)](#setSelectedUrls)
- [void setSupportedSchemes(const QStringList &schemes)](#setSupportedSchemes)
- [void setUrl(const QUrl &url, bool clearforward = true)](#setUrl)
- [void setViewMode(KFile::FileView mode)](#setViewMode)
- [QStringList supportedSchemes() const](#supportedSchemes)

## Public Slots

- [void accept()](#accept)
- [void slotCancel()](#slotCancel)
- [void slotOk()](#slotOk)

## Signals

- [void accepted()](#accepted)
- [void fileHighlighted(const QUrl &)](#fileHighlighted)
- [void fileSelected(const QUrl &)](#fileSelected)
- [void filterChanged(const KFileFilter &filter)](#filterChanged) (since 6.0)
- [void selectionChanged()](#selectionChanged)

## Static Public Members

- [QUrl getStartUrl(const QUrl &startDir, QString &recentDirClass)](#getStartUrl)
- [QUrl getStartUrl(const QUrl &startDir, QString &recentDirClass, QString &fileName)](#getStartUrl-1)

## Detailed Description {#details}

This is the contents of the KDE file dialog, without the actual [QDialog](https://doc.qt.io/qt-6/qdialog.html) around it. It can be embedded directly into applications.

## Member Type Documentation {#member-type-documentation}

### enum KFileWidget::OperationMode {#OperationMode-enum}

Defines some default behavior of the filedialog.

E.g. in mode Opening and Saving, the selected files/urls will be added to the "recent documents" list. The Saving mode also implies [setKeepLocation](kfilewidget.md#setKeepLocation)() being set.

Other means that no default actions are performed.

| Constant |   |
| --- | --- |
| `KFileWidget::Other` | `0` |
| `KFileWidget::Opening` | `1` |
| `KFileWidget::Saving` | `2` |

*See also* [setOperationMode](kfilewidget.md#setOperationMode), [operationMode](kfilewidget.md#operationMode)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFileWidget::KFileWidget(const QUrl &*startDir*, QWidget \**parent* = nullptr) {#KFileWidget}

Constructs a file selector widget.

`startDir` This can either be:

- An empty URL (QUrl()) to start in the current working directory, or the last directory where a file has been selected.
- The path or URL of a starting directory.
- An initial file name to select, with the starting directory being the current working directory or the last directory where a file has been selected.
- The path or URL of a file, specifying both the starting directory and an initially selected file name.
- A URL of the form `kfiledialog:///<keyword>`; to start in the directory last used by a filedialog in the same application that specified the same keyword.
- A URL of the form `kfiledialog:///<keyword>/<filename>`; to start in the directory last used by a filedialog in the same application that specified the same keyword, and to initially select the specified filename.
- Deprecated: A URL of the form `kfiledialog:///<keyword>?global` to start in the directory last used by a filedialog in any application that specified the same keyword.
- Deprecated: A URL of the form `kfiledialog:///<keyword>/<filename>?global` to start in the directory last used by a filedialog in any application that specified the same keyword, and to initially select the specified filename.

> **Note:** Since 5.96, the "?global" syntax is deprecated, for lack of usage.

`parent` The parent widget of this widget

### \[slot\] void KFileWidget::accept() {#accept}

### \[signal\] void KFileWidget::accepted() {#accepted}

Emitted by [slotOk](kfilewidget.md#slotOk)() (directly or asynchronously) once everything has been done. Should be used by the caller to call [accept](kfilewidget.md#accept)().

### QUrl KFileWidget::baseUrl() const {#baseUrl}

Returns the currently shown directory.

### QPushButton \*KFileWidget::cancelButton() const {#cancelButton}

Returns a pointer to the Cancel-Button in the filedialog. Note that the button is hidden and unconnected when using [KFileWidget](kfilewidget.md) alone; KFileDialog shows it and connects to it.

### void KFileWidget::clearFilter() {#clearFilter}

Clears any MIME type or name filter. Does not reload the directory.

### \[since 6.0\] KFileFilter KFileWidget::currentFilter() const {#currentFilter}

Returns the current filter as entered by the user or one of the predefined set via [setFilters](kfilewidget.md#setFilters)().

This function was introduced in Qt 6.0.

*See also* [setFilters](kfilewidget.md#setFilters)(), [filterChanged](kfilewidget.md#filterChanged)()

### QSize KFileWidget::dialogSizeHint() const {#dialogSizeHint}

Provides a size hint, useful for dialogs that embed the widget.

Returns a [QSize](https://doc.qt.io/qt-6/qsize.html), calculated to be optimal for a dialog.

### KDirOperator \*KFileWidget::dirOperator() {#dirOperator}

Returns the [KDirOperator](kdiroperator.md) used to navigate the filesystem

### \[signal\] void KFileWidget::fileHighlighted(*const QUrl &*) {#fileHighlighted}

Emitted when the user highlights a file.

### \[signal\] void KFileWidget::fileSelected(*const QUrl &*) {#fileSelected}

Emitted when the user selects a file. It is only emitted in single- selection mode. The best way to get notified about selected file(s) is to connect to the okClicked() signal inherited from KDialog and call [selectedFile](kfilewidget.md#selectedFile)(), [selectedFiles](kfilewidget.md#selectedFiles)(), [selectedUrl](kfilewidget.md#selectedUrl)() or [selectedUrls](kfilewidget.md#selectedUrls)().

### \[signal, since 6.0\] void KFileWidget::filterChanged(const KFileFilter &*filter*) {#filterChanged}

Emitted when the filter changed, i.e. the user entered an own filter or chose one of the predefined set via [setFilters](kfilewidget.md#setFilters)().

`filter` contains the new filter (only the extension part, not the explanation), i.e. "\*.cpp" or "\*.cpp \*.cc".

This function was introduced in Qt 6.0.

*See also* [setFilters](kfilewidget.md#setFilters)(), [currentFilter](kfilewidget.md#currentFilter)()

### KFileFilterCombo \*KFileWidget::filterWidget() const {#filterWidget}

Returns the combobox that contains the filters

### \[static\] QUrl KFileWidget::getStartUrl(const QUrl &*startDir*, QString &*recentDirClass*) {#getStartUrl}

This method implements the logic to determine the user's default directory to be listed. E.g. the documents directory, home directory or a recently used directory.

`startDir` A URL specifying the initial directory, or using the `kfiledialog:///` syntax to specify a last used directory. If this URL specifies a file name, it is ignored. Refer to the [KFileWidget::KFileWidget](kfilewidget.md#KFileWidget)() documentation for the `kfiledialog:///` URL syntax.

`recentDirClass` If the `kfiledialog:///` syntax is used, this will return the string to be passed to [KRecentDirs::dir](../kiocore/krecentdirs.md#dir)() and [KRecentDirs::add](../kiocore/krecentdirs.md#add)().

Returns The URL that should be listed by default (e.g. by KFileDialog or KDirSelectDialog).

*See also* [KFileWidget::KFileWidget](kfilewidget.md#KFileWidget)()

### \[static\] QUrl KFileWidget::getStartUrl(const QUrl &*startDir*, QString &*recentDirClass*, QString &*fileName*) {#getStartUrl-1}

Similar to [getStartUrl](kfilewidget.md#getStartUrl)(const [QUrl](https://doc.qt.io/qt-6/qurl.html)& startDir,[QString](https://doc.qt.io/qt-6/qstring.html)& recentDirClass), but allows both the recent start directory keyword and a suggested file name to be returned.

`startDir` A URL specifying the initial directory and/or filename, or using the `kfiledialog:///` syntax to specify a last used location. Refer to the [KFileWidget::KFileWidget](kfilewidget.md#KFileWidget)() documentation for the `kfiledialog:///` URL syntax.

`recentDirClass` If the `kfiledialog:///` syntax is used, this will return the string to be passed to [KRecentDirs::dir](../kiocore/krecentdirs.md#dir)() and [KRecentDirs::add](../kiocore/krecentdirs.md#add)().

`fileName` The suggested file name, if specified as part of the `startDir` URL.

Returns The URL that should be listed by default (e.g. by KFileDialog or KDirSelectDialog).

*See also* [KFileWidget::KFileWidget](kfilewidget.md#KFileWidget)()

### bool KFileWidget::keepsLocation() const {#keepsLocation}

Returns whether the contents of the location edit are kept when changing directories.

### KUrlComboBox \*KFileWidget::locationEdit() const {#locationEdit}

Returns the combobox used to type the filename or full location of the file.

### KFile::Modes KFileWidget::mode() const {#mode}

Returns the mode of the filedialog.

*See also* [setMode](kfilewidget.md#setMode)()

### QPushButton \*KFileWidget::okButton() const {#okButton}

Returns a pointer to the OK-Button in the filedialog. Note that the button is hidden and unconnected when using [KFileWidget](kfilewidget.md) alone; KFileDialog shows it and connects to it.

### KFileWidget::OperationMode KFileWidget::operationMode() const {#operationMode}

Returns the current operation mode, Opening, Saving or Other. Default is Other.

*See also* [setOperationMode](kfilewidget.md#setOperationMode)(), operationMode, [KFileWidget::OperationMode](kfilewidget.md#OperationMode-enum)

### QString KFileWidget::selectedFile() const {#selectedFile}

Returns the full path of the selected file in the local filesystem. (Local files only)

### QStringList KFileWidget::selectedFiles() const {#selectedFiles}

Returns a list of all selected local files.

### QUrl KFileWidget::selectedUrl() const {#selectedUrl}

Returns The selected fully qualified filename.

*See also* [setSelectedUrl](kfilewidget.md#setSelectedUrl)()

### QList\<QUrl\> KFileWidget::selectedUrls() const {#selectedUrls}

Returns The list of selected URLs.

*See also* [setSelectedUrls](kfilewidget.md#setSelectedUrls)()

### \[signal\] void KFileWidget::selectionChanged() {#selectionChanged}

Emitted when the user highlights one or more files in multiselection mode.

Note: [fileHighlighted](kfilewidget.md#fileHighlighted)() or [fileSelected](kfilewidget.md#fileSelected)() are @em not emitted in multiselection mode. You may use selectedItems() to ask for the current highlighted items.

*See also* [fileSelected](kfilewidget.md#fileSelected)

### void KFileWidget::setConfirmOverwrite(bool *enable*) {#setConfirmOverwrite}

Sets whether the user should be asked for confirmation when an overwrite might occur.

`enable` Set this to true to enable checking.

### void KFileWidget::setCustomWidget(QWidget \**widget*) {#setCustomWidget}

Set a custom widget that should be added to the file dialog.

`widget` A widget, or a widget of widgets, for displaying custom data in the file widget. This can be used, for example, to display a check box with the title "Open as read-only". When creating this widget, you don't need to specify a parent, since the widget's parent will be set automatically by [KFileWidget](kfilewidget.md).

### void KFileWidget::setCustomWidget(const QString &*text*, QWidget \**widget*) {#setCustomWidget-1}

Sets a custom widget that should be added below the location and the filter editors.

`text` Label of the custom widget, which is displayed below the labels "Location:" and "Filter:".

`widget` Any kind of widget, but preferable a combo box or a line editor to be compliant with the location and filter layout. When creating this widget, you don't need to specify a parent, since the widget's parent will be set automatically by [KFileWidget](kfilewidget.md).

### \[since 6.0\] void KFileWidget::setFilters(const QList\<KFileFilter\> &*filters*, const KFileFilter &*activeFilter* = KFileFilter()) {#setFilters}

Set the filters to be used.

Each item of the list corresponds to a selectable filter.

Only one filter is active at a time.

`activeFilter` the initially active filter

This function was introduced in Qt 6.0.

### void KFileWidget::setInlinePreviewShown(bool *show*) {#setInlinePreviewShown}

Forces the inline previews to be shown or hidden, depending on `show`.

`show` Whether to show inline previews or not.

### void KFileWidget::setKeepLocation(bool *keep*) {#setKeepLocation}

Sets whether the filename/url should be kept when changing directories. This is for example useful when having a predefined filename where the full path for that file is searched.

This is implicitly set when [operationMode](kfilewidget.md#operationMode)() is [KFileWidget::Saving](kfilewidget.md#OperationMode-enum)

getSaveFileName() and getSaveUrl() set this to true by default, so that you can type in the filename and change the directory without having to type the name again.

### void KFileWidget::setLocationLabel(const QString &*text*) {#setLocationLabel}

Sets the text to be displayed in front of the selection.

The default is "Location". Most useful if you want to make clear what the location is used for.

### void KFileWidget::setMode(KFile::Modes *m*) {#setMode}

Sets the mode of the dialog.

The mode is defined as (in kfile.h):

```cpp
enum Mode {
     File         = 1,
     Directory    = 2,
     Files        = 4,
     ExistingOnly = 8,
     LocalOnly    = 16,
};
```

You can OR the values, e.g.

```cpp
KFile::Modes mode = KFile::Files |
                    KFile::ExistingOnly |
                    KFile::LocalOnly );
setMode( mode );
```

*See also* [mode](kfilewidget.md#mode)()

### void KFileWidget::setOperationMode(*KFileWidget::OperationMode*) {#setOperationMode}

Sets the operational mode of the filedialog to Saving, Opening or Other. This will set some flags that are specific to loading or saving files. E.g. [setKeepLocation](kfilewidget.md#setKeepLocation)() makes mostly sense for a save-as dialog. So setOperationMode( [KFileWidget::Saving](kfilewidget.md#OperationMode-enum) ); sets [setKeepLocation](kfilewidget.md#setKeepLocation) for example.

The mode Saving, together with a default filter set via setMimeFilter() will make the filter combobox read-only.

The default mode is Opening.

Call this method right after instantiating [KFileWidget](kfilewidget.md).

*See also* [operationMode](kfilewidget.md#operationMode), [KFileWidget::OperationMode](kfilewidget.md#OperationMode-enum)

### void KFileWidget::setSelectedUrl(const QUrl &*url*) {#setSelectedUrl}

Sets the URL to preselect to `url`

This method handles absolute URLs (remember to use fromLocalFile for local paths). It also handles relative URLs, which you should construct like this: [QUrl](https://doc.qt.io/qt-6/qurl.html) relativeUrl; relativeUrl.setPath(fileName);

*See also* [selectedUrl](kfilewidget.md#selectedUrl)()

### void KFileWidget::setSelectedUrls(const QList\<QUrl\> &*urls*) {#setSelectedUrls}

Sets a list of URLs as preselected

*See also* [selectedUrls](kfilewidget.md#selectedUrls)(), [setSelectedUrl](kfilewidget.md#setSelectedUrl)

### void KFileWidget::setSupportedSchemes(const QStringList &*schemes*) {#setSupportedSchemes}

Set the URL schemes that the file widget should allow navigating to.

If the returned list is empty, all schemes are supported.

*See also* [supportedSchemes](kfilewidget.md#supportedSchemes)(), [QFileDialog::setSupportedSchemes](https://doc.qt.io/qt-6/qfiledialog.html#supportedSchemes-prop)

### void KFileWidget::setUrl(const QUrl &*url*, bool *clearforward* = true) {#setUrl}

Sets the directory to view.

`url` URL to show.

`clearforward` Indicates whether the forward queue should be cleared.

### void KFileWidget::setViewMode(KFile::FileView *mode*) {#setViewMode}

Sets how the view should be displayed.

*See also* [KFile::FileView](../kiowidgets/kfile.md#FileView-enum)

### \[slot\] void KFileWidget::slotCancel() {#slotCancel}

### \[slot\] void KFileWidget::slotOk() {#slotOk}

Called when clicking ok (when this widget is used in KFileDialog) Might or might not call [accept](kfilewidget.md#accept)().

### QStringList KFileWidget::supportedSchemes() const {#supportedSchemes}

Returns the URL schemes that the file widget should allow navigating to.

If the returned list is empty, all schemes are supported. Examples for schemes are `"file"` or `"ftp"`.

*See also* [setSupportedSchemes](kfilewidget.md#setSupportedSchemes)(), [QFileDialog::supportedSchemes](https://doc.qt.io/qt-6/qfiledialog.html#supportedSchemes-prop)
