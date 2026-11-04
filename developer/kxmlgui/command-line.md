---
title: Command line interface
description: Let the text editor open the file given on the command line.
source_url: https://develop.kde.org/docs/getting-started/kxmlgui/commandline/
source_authors: [Albert Astals Cid, Alexander Lohnau, Andrew Shark, Burak Hancerli, Carl Schwan, Claudio Cambra, Enzo Barcelos, Mikhail Zolotukhin, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: Qt 6.11 (QCommandLineParser, QUrl::fromUserInput), sonic-frameworks-io; the code was built against SonicDE's frameworks without warnings
---

# Command line interface

## Introduction

The text editor can open and save files. Now let's make it behave more like a desktop application: open a file given on the command line, which also lets the file manager's "Open With" use it.

## Code and explanation

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
    void openFileFromUrl(const QUrl &inputFileName);

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

The only addition is a public function `openFileFromUrl()` that takes a [QUrl](https://doc.qt.io/qt-6/qurl.html). Again we use URLs rather than strings, so remote files work like local ones.

### mainwindow.cpp

Only `openFile()` changes: it now passes the URL from the dialog to the new `openFileFromUrl()`, which contains the rest of the old `openFile()`:

```cpp
void MainWindow::openFile()
{
    openFileFromUrl(QFileDialog::getOpenFileUrl(this, i18n("Open File")));
}

void MainWindow::openFileFromUrl(const QUrl &inputFileName)
{
    if (!inputFileName.isEmpty()) {
        KIO::Job *job = KIO::storedGet(inputFileName);
        fileName = inputFileName.toLocalFile();
        connect(job, &KJob::result, this, &MainWindow::downloadFinished);
        job->exec();
    }
}
```

The rest of `mainwindow.cpp` is as in [Saving and loading](saving-and-loading.md#mainwindowcpp). There's no new code, only rearranging: we call `openFile()` to show a dialog, or `openFileFromUrl()` when we already know the file, as we do when it is given on the command line.

### main.cpp

```cpp
#include <QApplication>
#include <QCommandLineParser>
#include <QDir>
#include <QUrl>
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
        i18n("A simple text area which can load and save."),
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
    parser.addPositionalArgument(u"file"_s, i18n("Document to open"));

    parser.process(app);
    aboutData.processCommandLine(&parser);

    MainWindow *window = new MainWindow();
    window->show();

    if (parser.positionalArguments().count() > 0) {
        window->openFileFromUrl(QUrl::fromUserInput(
            parser.positionalArguments().at(0),
            QDir::currentPath()));
    }

    return app.exec();
}
```

This is where [QCommandLineParser](https://doc.qt.io/qt-6/qcommandlineparser.html) does its work. So far we only used it to give the application options like `--version` and `--author`; now it processes arguments too.

First we tell it about a positional argument. Positional arguments are the arguments that aren't options: `-h` and `--version` are options, `file` is an argument.

```c++
parser.addPositionalArgument(u"file"_s, i18n("Document to open"));
```

After processing, if there is an argument, we open it; otherwise we carry on as before. The editor opens one file at a time, so only the first argument matters. We pass `openFileFromUrl()` the URL of the file, whether local, like `$HOME/foo`, or remote, like `ftp://ftp.example.com/bar`. The form of [QUrl::fromUserInput()](https://doc.qt.io/qt-6/qurl.html#fromUserInput) with a working directory resolves relative paths such as `../baz` against the current directory.

```c++
if (parser.positionalArguments().count() > 0) {
    window->openFileFromUrl(QUrl::fromUserInput(parser.positionalArguments().at(0), QDir::currentPath()));
}
```

### CMakeLists.txt

Nothing changes; it is the same as in [Saving and loading](saving-and-loading.md#cmakeliststxt).

## Running the application

Build and install it as in [Hello World](hello-world.md#building-and-running).

Then check that the application opens files from the command line. Create a simple file:

```bash
echo "It works!" > testfile.txt
```

and pass it as an argument:

```bash
texteditor testfile.txt
```

The editor starts and shows "It works!" in the text area.

This was the last step of the tutorial. You now have a small text editor that loads and saves local and remote files, with menus, a toolbar, shortcuts and a command line.
