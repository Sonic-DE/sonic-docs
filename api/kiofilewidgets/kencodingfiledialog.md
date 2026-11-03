---
title: "KEncodingFileDialog Class"
description: "Provides a user (and developer) friendly way to select files with support for choosing encoding. This class is deprecated since 6.19. We strongly advise against using it in new code."
---

# KEncodingFileDialog Class

Provides a user (and developer) friendly way to select files with support for choosing encoding. **This class is deprecated since 6.19. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <KEncodingFileDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)
- **Status:** Deprecated since 6.19

[List of all members, including inherited members](kencodingfiledialog-members.md)

## Static Public Members

- [KEncodingFileDialog::Result getOpenFileNameAndEncoding(const QString &encoding = QString(), const QUrl &startDir = QUrl(), const QString &filter = QString(), QWidget \*parent = nullptr, const QString &title = QString())](#getOpenFileNameAndEncoding)
- [KEncodingFileDialog::Result getOpenFileNamesAndEncoding(const QString &encoding = QString(), const QUrl &startDir = QUrl(), const QString &filter = QString(), QWidget \*parent = nullptr, const QString &title = QString())](#getOpenFileNamesAndEncoding)
- [KEncodingFileDialog::Result getOpenUrlAndEncoding(const QString &encoding = QString(), const QUrl &startDir = QUrl(), const QString &filter = QString(), QWidget \*parent = nullptr, const QString &title = QString())](#getOpenUrlAndEncoding)
- [KEncodingFileDialog::Result getOpenUrlsAndEncoding(const QString &encoding = QString(), const QUrl &startDir = QUrl(), const QString &filter = QString(), QWidget \*parent = nullptr, const QString &title = QString())](#getOpenUrlsAndEncoding)
- [KEncodingFileDialog::Result getSaveFileNameAndEncoding(const QString &encoding = QString(), const QUrl &startDir = QUrl(), const QString &filter = QString(), QWidget \*parent = nullptr, const QString &title = QString())](#getSaveFileNameAndEncoding)
- [KEncodingFileDialog::Result getSaveUrlAndEncoding(const QString &encoding = QString(), const QUrl &startDir = QUrl(), const QString &filter = QString(), QWidget \*parent = nullptr, const QString &title = QString())](#getSaveUrlAndEncoding)

**This class is deprecated since 6.19. We strongly advise against using it in new code.**

## Detailed Description {#details}

This class comes with a private constructor, the only way to show a file dialog is through its static methods.

Use [QFileDialog](https://doc.qt.io/qt-6/qfiledialog.html) instead.

## Member Function Documentation {#member-function-documentation}

### \[static\] KEncodingFileDialog::Result KEncodingFileDialog::getOpenFileNameAndEncoding(const QString &*encoding* = QString(), const QUrl &*startDir* = QUrl(), const QString &*filter* = QString(), QWidget \**parent* = nullptr, const QString &*title* = QString()) {#getOpenFileNameAndEncoding}

Creates a modal file dialog and return the selected filename or an empty string if none was chosen additionally a chosen encoding value is returned.

Note that with this method the user must select an existing filename.

`encoding` The encoding shown in the encoding combo.

`startDir` This can either be

- The URL of the directory to start in.
- QString() to start in the current working directory, or the last directory where a file has been selected.
- ':\<keyword\>' to start in the directory last used by a filedialog in the same application that specified the same keyword.
- '::\<keyword\>' to start in the directory last used by a filedialog in any application that specified the same keyword.

`filter` A shell glob or a MIME type filter that specifies which files to display. see [KFileFilter::KFileFilter](../kiocore/kfilefilter.md)(const [QString](https://doc.qt.io/qt-6/qstring.html) &label, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &filePatterns, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &mimePatterns) for examples of patterns.

`parent` The widget the dialog will be centered on initially.

`title` The name of the dialog widget.

### \[static\] KEncodingFileDialog::Result KEncodingFileDialog::getOpenFileNamesAndEncoding(const QString &*encoding* = QString(), const QUrl &*startDir* = QUrl(), const QString &*filter* = QString(), QWidget \**parent* = nullptr, const QString &*title* = QString()) {#getOpenFileNamesAndEncoding}

Creates a modal file dialog and returns the selected encoding and the selected filenames or an empty list if none was chosen.

Note that with this method the user must select an existing filename.

`encoding` The encoding shown in the encoding combo.

`startDir` This can either be

- The URL of the directory to start in.
- QString() to start in the current working directory, or the last directory where a file has been selected.
- ':\<keyword\>' to start in the directory last used by a filedialog in the same application that specified the same keyword.
- '::\<keyword\>' to start in the directory last used by a filedialog in any application that specified the same keyword.

`filter` A shell glob or a MIME type filter that specifies which files to display. see [KFileFilter::KFileFilter](../kiocore/kfilefilter.md)(const [QString](https://doc.qt.io/qt-6/qstring.html) &label, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &filePatterns, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &mimePatterns) for examples of patterns.

`parent` The widget the dialog will be centered on initially.

`title` The name of the dialog widget.

### \[static\] KEncodingFileDialog::Result KEncodingFileDialog::getOpenUrlAndEncoding(const QString &*encoding* = QString(), const QUrl &*startDir* = QUrl(), const QString &*filter* = QString(), QWidget \**parent* = nullptr, const QString &*title* = QString()) {#getOpenUrlAndEncoding}

Creates a modal file dialog and returns the selected encoding and URL or an empty string if none was chosen.

Note that with this method the user must select an existing URL.

`encoding` The encoding shown in the encoding combo.

`startDir` This can either be

- The URL of the directory to start in.
- QString() to start in the current working directory, or the last directory where a file has been selected.
- ':\<keyword\>' to start in the directory last used by a filedialog in the same application that specified the same keyword.
- '::\<keyword\>' to start in the directory last used by a filedialog in any application that specified the same keyword.

`filter` A shell glob or a MIME type filter that specifies which files to display. see [KFileFilter::KFileFilter](../kiocore/kfilefilter.md)(const [QString](https://doc.qt.io/qt-6/qstring.html) &label, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &filePatterns, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &mimePatterns) for examples of patterns.

`parent` The widget the dialog will be centered on initially.

`title` The name of the dialog widget.

### \[static\] KEncodingFileDialog::Result KEncodingFileDialog::getOpenUrlsAndEncoding(const QString &*encoding* = QString(), const QUrl &*startDir* = QUrl(), const QString &*filter* = QString(), QWidget \**parent* = nullptr, const QString &*title* = QString()) {#getOpenUrlsAndEncoding}

Creates a modal file dialog and returns the selected encoding URLs or an empty list if none was chosen.

Note that with this method the user must select an existing filename.

`encoding` The encoding shown in the encoding combo.

`startDir` This can either be

- The URL of the directory to start in.
- QString() to start in the current working directory, or the last directory where a file has been selected.
- ':\<keyword\>' to start in the directory last used by a filedialog in the same application that specified the same keyword.
- '::\<keyword\>' to start in the directory last used by a filedialog in any application that specified the same keyword.

`filter` A shell glob or a MIME type filter that specifies which files to display. see [KFileFilter::KFileFilter](../kiocore/kfilefilter.md)(const [QString](https://doc.qt.io/qt-6/qstring.html) &label, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &filePatterns, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &mimePatterns) for examples of patterns.

`parent` The widget the dialog will be centered on initially.

`title` The name of the dialog widget.

### \[static\] KEncodingFileDialog::Result KEncodingFileDialog::getSaveFileNameAndEncoding(const QString &*encoding* = QString(), const QUrl &*startDir* = QUrl(), const QString &*filter* = QString(), QWidget \**parent* = nullptr, const QString &*title* = QString()) {#getSaveFileNameAndEncoding}

Creates a modal file dialog and returns the selected encoding and filename or an empty string if none was chosen.

Note that with this method the user need not select an existing filename.

`encoding` The encoding shown in the encoding combo. `startDir` This can either be

- The URL of the directory to start in.
- a relative path or a filename determining the directory to start in and the file to be selected.
- QString() to start in the current working directory, or the last directory where a file has been selected.
- ':\<keyword\>' to start in the directory last used by a filedialog in the same application that specified the same keyword.
- '::\<keyword\>;' to start in the directory last used by a filedialog in any application that specified the same keyword.

`filter` A shell glob or a MIME type filter that specifies which files to display. see [KFileFilter::KFileFilter](../kiocore/kfilefilter.md)(const [QString](https://doc.qt.io/qt-6/qstring.html) &label, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &filePatterns, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &mimePatterns) for examples of patterns.

`parent` The widget the dialog will be centered on initially.

`title` The name of the dialog widget.

### \[static\] KEncodingFileDialog::Result KEncodingFileDialog::getSaveUrlAndEncoding(const QString &*encoding* = QString(), const QUrl &*startDir* = QUrl(), const QString &*filter* = QString(), QWidget \**parent* = nullptr, const QString &*title* = QString()) {#getSaveUrlAndEncoding}

Creates a modal file dialog and returns the selected encoding and filename or an empty string if none was chosen.

Note that with this method the user need not select an existing filename.

`encoding` The encoding shown in the encoding combo.

`startDir` This can either be

- The URL of the directory to start in.
- a relative path or a filename determining the directory to start in and the file to be selected.
- QString() to start in the current working directory, or the last directory where a file has been selected.
- ':\<keyword\>' to start in the directory last used by a filedialog in the same application that specified the same keyword.
- '::\<keyword\>' to start in the directory last used by a filedialog in any application that specified the same keyword.

`filter` A shell glob or a MIME type filter that specifies which files to display. see [KFileFilter::KFileFilter](../kiocore/kfilefilter.md)(const [QString](https://doc.qt.io/qt-6/qstring.html) &label, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &filePatterns, const [QStringList](https://doc.qt.io/qt-6/qstringlist.html) &mimePatterns) for examples of patterns.

`parent` The widget the dialog will be centered on initially.

`title` The name of the dialog widget.
