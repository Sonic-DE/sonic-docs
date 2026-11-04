---
title: Saving and loading
description: Add loading and saving to the text editor, using KIO.
source_url: https://develop.kde.org/docs/getting-started/kxmlgui/saving_and_loading/
source_authors: [Alexander Lohnau, Andrew Shark, Arpan Patelia, Burak Hancerli, Carl Schwan, Claudio Cambra, Frederik Schwarzer, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-io (KIO::storedGet, StoredTransferJob), sonic-frameworks-settings-ui (KStandardAction), Qt 6.11 (QSaveFile::open is [[nodiscard]]); the code was built against SonicDE's frameworks without warnings
---

# Saving and loading

## Introduction

With a basic text editor interface in place, let's make it useful. At the very least, a text editor must load files, save new and changed files, and create new ones.

SonicDE's libraries have classes that make working with files much easier. [KIO](/docs/api/kiocore/kio-index) (`sonic-frameworks-io`) accesses files through network-transparent protocols, and Qt provides standard file dialogs for opening and saving.

## The code

### main.cpp

Nothing changes here, apart from the texts in [KAboutData](/docs/api/kcoreaddons/kaboutdata):

```cpp
#include <QApplication>
#include <QCommandLineParser>
#include <KAboutData>
#include <KLocalizedString>
#include "mainwindow.h"

int main (int argc, char *argv[])
{
    using namespace Qt::Literals::StringLiterals;

    QApplication app(argc, argv);
    KLocalizedString::setApplicationDomain("texteditor");

    KAboutData aboutData(
        u"texteditor"_s,
        i18n("Text Editor"),
        u"1.0"_s,
        i18n("A simple editor capable of saving and loading"),
        KAboutLicense::GPL,
        i18n("(c) 2024"),
        i18n("Educational application..."),
        u"https://example.com/texteditor/"_s,
        u"https://example.com/texteditor/bugs/"_s);

    aboutData.addAuthor(
        i18n("John Doe"),
        i18n("Tutorial learner"),
        u"john.doe@example.com"_s,
        u"https://john-doe.example.com"_s,
        u"johndoe"_s);

    KAboutData::setApplicationData(aboutData);

    QCommandLineParser parser;
    aboutData.setupCommandLine(&parser);
    parser.process(app);
    aboutData.processCommandLine(&parser);

    MainWindow *window = new MainWindow();
    window->show();

    return app.exec();
}
```

### mainwindow.h

```cpp
#ifndef MAINWINDOW_H
#define MAINWINDOW_H

#include <KXmlGuiWindow>

class KTextEdit;
class KJob;

class MainWindow : public KXmlGuiWindow
{
    Q_OBJECT

public:
    explicit MainWindow(QWidget *parent = nullptr);

private:
    void setupActions();
    void saveFileToDisk(const QString &outputFileName);

private Q_SLOTS:
    void newFile();
    void openFile();
    void saveFile();
    void saveFileAs();

    void downloadFinished(KJob *job);

private:
    KTextEdit *textArea;
    QString fileName;
};

#endif // MAINWINDOW_H
```

To load and save files we add the functions that do the work. They are called through [Qt's signals and slots](https://doc.qt.io/qt-6/signalsandslots.html), so we declare them as slots with `Q_SLOTS`, which also needs the [Q_OBJECT](https://doc.qt.io/qt-6/qobject.html#Q_OBJECT) macro: only classes with it can have signals and slots.

We also keep the name of the open file, in the [QString](https://doc.qt.io/qt-6/qstring.html) `fileName`.

### mainwindow.cpp

```cpp
#include <QApplication>
#include <QAction>
#include <QSaveFile>
#include <QFileDialog>
#include <QTextStream>
#include <QByteArray>
#include <KTextEdit>
#include <KLocalizedString>
#include <KActionCollection>
#include <KStandardAction>
#include <KMessageBox>
#include <KIO/StoredTransferJob>
#include "mainwindow.h"

MainWindow::MainWindow(QWidget *parent) : KXmlGuiWindow(parent), fileName(QString())
{
    textArea = new KTextEdit();
    setCentralWidget(textArea);
    setupActions();
}

void MainWindow::setupActions()
{
    using namespace Qt::Literals::StringLiterals;

    QAction *clearAction = new QAction(this);
    clearAction->setText(i18n("&Clear"));
    clearAction->setIcon(QIcon::fromTheme(u"document-new-symbolic"_s));
    actionCollection()->addAction(u"clear"_s, clearAction);
    actionCollection()->setDefaultShortcut(clearAction, Qt::CTRL | Qt::Key_L);
    connect(clearAction, &QAction::triggered, textArea, &KTextEdit::clear);

    KStandardAction::quit(qApp, &QCoreApplication::quit, actionCollection());
    KStandardAction::open(this, &MainWindow::openFile, actionCollection());
    KStandardAction::save(this, &MainWindow::saveFile, actionCollection());
    KStandardAction::saveAs(this, &MainWindow::saveFileAs, actionCollection());
    KStandardAction::openNew(this, &MainWindow::newFile, actionCollection());

    setupGUI(Default, u"texteditorui.rc"_s);
}

void MainWindow::newFile()
{
    fileName.clear();
    textArea->clear();
}

void MainWindow::saveFileToDisk(const QString &outputFileName)
{
    if (!outputFileName.isNull()) {
        QSaveFile file(outputFileName);
        if (!file.open(QIODevice::WriteOnly)) {
            KMessageBox::error(this, file.errorString());
            return;
        }

        QByteArray outputByteArray;
        outputByteArray.append(textArea->toPlainText().toUtf8());

        file.write(outputByteArray);
        if (!file.commit()) {
            KMessageBox::error(this, file.errorString());
            return;
        }

        fileName = outputFileName;
    }
}

void MainWindow::saveFileAs()
{
    saveFileToDisk(QFileDialog::getSaveFileName(this, i18n("Save File As")));
}

void MainWindow::saveFile()
{
    if (!fileName.isEmpty()) {
        saveFileToDisk(fileName);
    } else {
        saveFileAs();
    }
}

void MainWindow::openFile()
{
    const QUrl fileNameFromDialog = QFileDialog::getOpenFileUrl(this, i18n("Open File"));

    if (!fileNameFromDialog.isEmpty()) {
        KIO::Job *job = KIO::storedGet(fileNameFromDialog);
        fileName = fileNameFromDialog.toLocalFile();
        connect(job, &KJob::result, this, &MainWindow::downloadFinished);
        job->exec();
    }
}

void MainWindow::downloadFinished(KJob *job)
{
    if (job->error()) {
        KMessageBox::error(this, job->errorString());
        fileName.clear();
        return;
    }

    const KIO::StoredTransferJob *storedJob = qobject_cast<KIO::StoredTransferJob *>(job);

    if (storedJob) {
        textArea->setPlainText(QTextStream(storedJob->data(), QIODevice::ReadOnly).readAll());
    }
}
```

The details follow below.

### texteditorui.rc

The same `texteditorui.rc` as in the [previous step](using-actions.md#xmlgui). The [KStandardAction](/docs/api/kconfigwidgets/kstandardaction) actions need no entries in it: KXmlGui places them automatically.

## Explanation

Now to the code that loads and saves, all in `mainwindow.cpp`.

```cpp
MainWindow::MainWindow(QWidget *parent) : KXmlGuiWindow(parent), fileName(QString())
```

First, `fileName(QString())` in the constructor's [initializer list](https://en.cppreference.com/w/cpp/language/constructor) makes sure `fileName` is empty from the start.

### Adding the actions

Next, the user needs a way to tell the application to load and save. As with the Quit action in the [previous step](using-actions.md#kstandardaction), we use [KStandardAction](/docs/api/kconfigwidgets/kstandardaction): we add the actions the same way and connect each to its slot declared in the header.

### Creating a new document

The first function is `newFile()`:

```cpp
void MainWindow::newFile()
{
  fileName.clear();
  textArea->clear();
}
```

`fileName.clear()` empties `fileName`, since the new document isn't stored anywhere yet. `textArea->clear()` clears the text area with the same function the Clear action is connected to in the [previous step](using-actions.md#creating-the-qaction).

> **Warning:** This example clears the text area without checking whether the document was saved. It only demonstrates file input and output; it is *not* an example of good practice.

### Saving a file

> **Note:** To keep the tutorial simple, the program only saves to local storage, even though it can open files from anywhere, including remote locations.

### saveFileToDisk(const QString &)

Now the first file handling code: a function that saves the content of the text area to the file name it is given. Qt provides [QSaveFile](https://doc.qt.io/qt-6/qsavefile.html) for saving files safely.

The function's signature is:

```cpp
void MainWindow::saveFileToDisk(const QString &outputFileName)
```

We create the QSaveFile and open it. If it can't be opened (for example because the folder isn't writable), we show the error and stop. Qt 6 also warns when the result of `open()` isn't checked.

```cpp
QSaveFile file(outputFileName);
if (!file.open(QIODevice::WriteOnly)) {
    KMessageBox::error(this, file.errorString());
    return;
}
```

Next, the text must be turned into something that can be written to a file. We create a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) as a buffer and fill it with the plain text of the text area, as UTF-8:

```cpp
QByteArray outputByteArray;
outputByteArray.append(textArea->toPlainText().toUtf8());
```

Then we write it with [QSaveFile::write()](https://doc.qt.io/qt-6/qiodevice.html#write). With a normal [QFile](https://doc.qt.io/qt-6/qfile.html), the file would change right away, and a problem halfway through would leave it damaged. QSaveFile writes to a temporary file first; [QSaveFile::commit()](https://doc.qt.io/qt-6/qsavefile.html#commit) then replaces the real file and closes it, and returns `false` if that fails.

```cpp
file.write(outputByteArray);
if (!file.commit()) {
    KMessageBox::error(this, file.errorString());
    return;
}
```

Finally, `fileName` is set to the name we saved to:

```cpp
fileName = outputFileName;
```

### saveFileAs()

The Save As action is connected to this function. It calls `saveFileToDisk()` with the file name returned by [QFileDialog::getSaveFileName()](https://doc.qt.io/qt-6/qfiledialog.html#getSaveFileName):

```cpp
void MainWindow::saveFileAs()
{
    saveFileToDisk(QFileDialog::getSaveFileName(this, i18n("Save File As")));
}
```

[QFileDialog](https://doc.qt.io/qt-6/qfiledialog.html) has static functions that show the standard file dialog, which in SonicDE is the desktop's own file dialog. `getSaveFileName()` lets the user pick or type the file to save to, and returns its full path (or an empty string if the dialog was cancelled, which `saveFileToDisk()` ignores).

### saveFile()

```c++
void MainWindow::saveFile()
{
    if(!fileName.isEmpty()) {
        saveFileToDisk(fileName);
    } else {
        saveFileAs();
    }
}
```

Nothing new here: if `fileName` isn't empty, the document is saved there; otherwise the Save As dialog lets the user choose a file name.

### Loading a file

Finally, loading a file, from local storage or a remote location such as an FTP server. That is all in `MainWindow::openFile()`.

First, ask the user which file to open, with [QFileDialog::getOpenFileUrl()](https://doc.qt.io/qt-6/qfiledialog.html#getOpenFileUrl):

```c++
const QUrl fileNameFromDialog = QFileDialog::getOpenFileUrl(this, i18n("Open File"));
```

[QUrl](https://doc.qt.io/qt-6/qurl.html) lets us handle remote files.

Then the [KIO](/docs/api/kiocore/kio-index) library gets the file, wherever it is, even on an SFTP server. [KIO::storedGet()](/docs/api/kiocore/kio-storedtransferjob#storedGet) takes the URL of the file to open or download:

```c++
KIO::Job *job = KIO::storedGet(fileNameFromDialog);
```

It returns a [KIO::Job](/docs/api/kiocore/kio-job). We connect the job's `result` signal to our `downloadFinished()` slot, then run the job. `exec()` runs it and waits until it has finished, emitting `result` on the way:

```c++
connect(job, &KJob::result, this, &MainWindow::downloadFinished);
job->exec();
```

The rest happens in `downloadFinished()`. First we check the job for errors. If it failed, we show the error in a message box and clear `fileName`, since no file was opened:

```c++
KMessageBox::error(this, job->errorString());
fileName.clear();
```

Otherwise we go on with opening the file.

The data `storedGet()` downloaded, here the content of our text file, is in the [KIO::StoredTransferJob](/docs/api/kiocore/kio-storedtransferjob). To show it as text, we read it with a [QTextStream](https://doc.qt.io/qt-6/qtextstream.html): we create one on the job's data and call [QTextStream::readAll()](https://doc.qt.io/qt-6/qtextstream.html#readAll) to get the text, which we pass to the text area's `setPlainText()`:

```c++
const KIO::StoredTransferJob *storedJob = qobject_cast<KIO::StoredTransferJob *>(job);

if (storedJob) {
    textArea->setPlainText(QTextStream(storedJob->data(), QIODevice::ReadOnly).readAll());
}
```

> **Note:** Again for simplicity, the program only saves text files to local storage. If you open a remote file and save it, `fileName` is empty (`toLocalFile()` of a remote URL is empty), so the program behaves as if you chose Save As for a new file.

### CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.20)

project(texteditor)

set(QT_MIN_VERSION "6.6.0")
set(KF_MIN_VERSION "6.0.0")

find_package(ECM ${KF_MIN_VERSION} REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)
include(FeatureSummary)

find_package(Qt6 ${QT_MIN_VERSION} CONFIG REQUIRED COMPONENTS
    Core    # QCommandLineParser, QStringLiteral, QSaveFile, QTextStream, QByteArray
    Widgets # QApplication, QAction, QFileDialog
)

find_package(KF6 ${KF_MIN_VERSION} REQUIRED COMPONENTS
    CoreAddons      # KAboutData
    I18n            # KLocalizedString
    XmlGui          # KXmlGuiWindow, KActionCollection
    TextWidgets     # KTextEdit
    ConfigWidgets   # KStandardActions
    WidgetsAddons   # KMessageBox
    KIO             # KIO
)

add_executable(texteditor)

target_sources(texteditor
    PRIVATE
    main.cpp
    mainwindow.cpp
)

target_link_libraries(texteditor
    Qt6::Widgets
    KF6::CoreAddons
    KF6::I18n
    KF6::XmlGui
    KF6::TextWidgets
    KF6::ConfigWidgets
    KF6::WidgetsAddons
    KF6::KIOCore
)

install(TARGETS texteditor ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})
install(FILES texteditorui.rc DESTINATION ${KDE_INSTALL_KXMLGUIDIR}/texteditor)
```

Since we now use the [KIO](/docs/api/kiocore/kio-index) library, CMake must link against it: add `KIO` to [`find_package()`](https://cmake.org/cmake/help/latest/command/find_package.html) and `KF6::KIOCore` to [`target_link_libraries()`](https://cmake.org/cmake/help/latest/command/target_link_libraries.html).

## Running the application

Build and install it as in [Hello World](hello-world.md#building-and-running), then run:

```bash
texteditor
```

Next: [Command line interface](command-line.md).
