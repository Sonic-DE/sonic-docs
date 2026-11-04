---
title: A full Python + Kirigami application
description: Learn how to write an application with PySide.
source_url: https://develop.kde.org/docs/getting-started/python/python-app/
source_authors: [Dan MacLeod, Kunda Ki, Robert French, Shyamnath Premnadh, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-pyside (PySide6 6.12.0, Python 3.14), sonic-frameworks-quick-ui (Kirigami), sonic-frameworks-quick-desktop-style; both stages run in a virtual environment, and a test script typed Markdown and pressed Format and Clear"
---

# A full Python + Kirigami application

## Prerequisites

To use Python together with QML, we use [PySide](https://doc.qt.io/qtforpython-6/), the official Python bindings for the Qt framework.

You need Python, which any major Linux distribution has, and SonicDE's PySide (`sonic-pyside`) and Kirigami (`sonic-frameworks-quick-ui`). Don't install PySide and Kirigami with `pip`: use the ones from your SonicDE installation (see [Building Sonic-DE](../building.md)), so that they are built for the same Qt version. Any other dependency can be installed with `pip` in a [Python virtual environment](https://docs.python.org/3/library/venv.html) later.

## Structure

The application is a simple Markdown viewer called `simplemdviewer`.

By the end of the tutorial, the project will look like this:

```text
simplemdviewer/
├── README.md
├── LICENSE.txt
├── MANIFEST.in                        # To add our QML file
├── pyproject.toml                     # The main file to manage the project
├── org.kde.simplemdviewer.desktop
├── org.kde.simplemdviewer.svg
├── org.kde.simplemdviewer.metainfo.xml
└── src/
    ├── __init__.py                    # To import the src/ directory as a package
    ├── __main__.py                    # To signal simplemdviewer_app as the entrypoint
    ├── simplemdviewer_app.py
    ├── md_converter.py
    └── qml/
        └── main.qml
```

All the metadata is in the root folder, while the actual code is in `src/`:

```text
simplemdviewer/
└── src/
    ├── simplemdviewer_app.py
    ├── md_converter.py
    └── qml/
        └── main.qml
```

> **Tip:** To quickly generate this folder structure, run `mkdir -p simplemdviewer/src/qml/`.

## Setting up the project

The user interface is created in QML and the logic in Python. Users write some Markdown text, press a button, and the formatted text is shown below it.

It is recommended to use a virtual environment. The `venv` module provides virtual environments with their own site directories, optionally isolated from the system site directories.

Create a directory and a virtual environment for the project:

```bash
mkdir simplemdviewer
cd simplemdviewer
python3 -m venv --system-site-packages env/
```

A new virtual environment is created in `env/`, which takes the required Python modules straight from your system.

> **Note:** The environment must use the Python version SonicDE's PySide was built for. If your system's `python3` is a different version, importing PySide6 fails; call that version explicitly, for example `python3.14 -m venv`.

Activate it with the activate script:

```bash
source env/bin/activate
```

To check that you are working in a virtual environment, look for the `VIRTUAL_ENV` environment variable with `env | grep VIRTUAL_ENV`.

Time to write some code. At first the application consists of two files: a file with the QML description of the user interface, and a Python file that loads the QML file.

Create a new directory `simplemdviewer/src/` and add a new `simplemdviewer_app.py` file to it:

```python
#!/usr/bin/env python3

import os
import sys
import signal
from PySide6.QtWidgets import QApplication
from PySide6.QtCore import QUrl
from PySide6.QtQml import QQmlApplicationEngine

def main():
    """Initializes and manages the application execution"""
    app = QApplication(sys.argv)
    engine = QQmlApplicationEngine()

    """Needed to close the app with Ctrl+C"""
    signal.signal(signal.SIGINT, signal.SIG_DFL)

    """Use the desktop's Qt Quick Controls style unless another one is set"""
    if not os.environ.get("QT_QUICK_CONTROLS_STYLE"):
        os.environ["QT_QUICK_CONTROLS_STYLE"] = "org.kde.desktop"

    base_path = os.path.abspath(os.path.dirname(__file__))
    url = QUrl(f"file://{base_path}/qml/main.qml")
    engine.load(url)

    if len(engine.rootObjects()) == 0:
        quit()

    app.exec()


if __name__ == "__main__":
    main()
```

We have just created a [QApplication](https://doc.qt.io/qtforpython-6/PySide6/QtWidgets/QApplication.html) object, which initializes the application and contains the main event loop. It is a `QApplication` rather than a `QGuiApplication` because the `org.kde.desktop` style needs one. The [QQmlApplicationEngine](https://doc.qt.io/qtforpython-6/PySide6/QtQml/QQmlApplicationEngine.html) object loads the `main.qml` file.

Create a new `src/qml/main.qml` file that specifies the user interface of the application:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    id: root

    title: qsTr("Simple Markdown viewer")

    minimumWidth: Kirigami.Units.gridUnit * 20
    minimumHeight: Kirigami.Units.gridUnit * 20
    width: minimumWidth
    height: minimumHeight

    pageStack.initialPage: initPage

    Component {
        id: initPage

        Kirigami.Page {
            title: qsTr("Markdown Viewer")

            ColumnLayout {
                anchors {
                    top: parent.top
                    left: parent.left
                    right: parent.right
                }
                Controls.TextArea {
                    id: sourceArea

                    placeholderText: qsTr("Write some Markdown code here")
                    wrapMode: Text.WrapAnywhere
                    Layout.fillWidth: true
                    Layout.minimumHeight: Kirigami.Units.gridUnit * 5
                }

                RowLayout {
                    Layout.fillWidth: true

                    Controls.Button {
                        text: qsTr("Format")

                        onClicked: formattedText.text = sourceArea.text
                    }

                    Controls.Button {
                        text: qsTr("Clear")

                        onClicked: {
                            sourceArea.text = ""
                            formattedText.text = ""
                        }
                    }
                }

                Text {
                    id: formattedText

                    textFormat: Text.RichText
                    wrapMode: Text.WordWrap

                    Layout.fillWidth: true
                    Layout.minimumHeight: Kirigami.Units.gridUnit * 5
                }
            }
        }
    }
}
```

### First test run

We have just created a new QML-Kirigami-Python application. Run it from the `src/` directory:

```bash
python3 simplemdviewer_app.py
```

So far we haven't used any interesting Python. In fact, the application can also run as a standalone QML application, from the `src/qml/` directory:

```bash
QT_QUICK_CONTROLS_STYLE=org.kde.desktop qml6 main.qml
```

> **About the qml binary:** Some distributions name the `qml` binary differently: for example `qml6` or `qml-qt6`, or only `qml` in Qt's own directory, such as `/usr/lib64/qt6/bin/`. Use the Qt 6 variant, so that your application runs with Qt 6.

It doesn't format anything: if we click "Format", it just puts the unformatted text into a text element.

### Adding Markdown functionality

Let's add some Python logic: a simple Markdown converter in a Python class derived from [QObject](https://doc.qt.io/qtforpython-6/PySide6/QtCore/QObject.html).

It has to derive from QObject to use Qt's powerful [signals and slots](https://doc.qt.io/qtforpython-6/tutorials/basictutorial/signals_and_slots.html).

Create a new `md_converter.py` file in the `simplemdviewer/src/` directory:

```python
from markdown import markdown
from PySide6.QtCore import QObject, Signal, Slot, Property
from PySide6.QtQml import QmlElement

QML_IMPORT_NAME = "org.kde.simplemdviewer"
QML_IMPORT_MAJOR_VERSION = 1

@QmlElement
class MdConverter(QObject):
    """A simple markdown converter"""

    sourceTextChanged = Signal()

    def __init__(self, _source_text=""):
        super().__init__()
        self._source_text = _source_text

    @Property(str, notify=sourceTextChanged)
    def sourceText(self):
        return self._source_text

    @sourceText.setter
    def sourceText(self, val):
        self._source_text = val
        self.sourceTextChanged.emit()

    @Slot(result=str)
    def mdFormat(self):
        return markdown(self._source_text)
```

The `MdConverter` class contains the `_source_text` member variable. The `sourceText` property exposes `_source_text` to the QML system with a getter and a setter.

We use a [Property decorator](https://realpython.com/python-property/#using-property-as-a-decorator) (beginning with `@`) on lines 18 and 22. The function has the same name for both getter and setter: the getter is marked with `@Property` and the setter with `functionName.setter`.

When the `sourceText` property is set, the `sourceTextChanged` [signal](https://doc.qt.io/qtforpython-6/tutorials/basictutorial/signals_and_slots.html#the-signal-class) is emitted to let QML know that the property has changed. `sourceTextChanged` needs to be marked with `notify=` before it can be emitted with `.emit()`.

The `mdFormat()` function returns the Markdown-formatted text. It is declared as a [slot](https://doc.qt.io/qtforpython-6/tutorials/basictutorial/signals_and_slots.html#the-slot-class) so that QML code can call it.

The `markdown` Python package takes care of the formatting. Let's install it in our virtual environment:

```bash
python3 -m pip install markdown
```

Now update the `simplemdviewer_app.py` file to:

```python
#!/usr/bin/env python3

import os
import sys
import signal
from PySide6.QtWidgets import QApplication
from PySide6.QtCore import QUrl
from PySide6.QtQml import QQmlApplicationEngine
from md_converter import MdConverter  # noqa: F401

def main():
    """Initializes and manages the application execution"""
    app = QApplication(sys.argv)
    engine = QQmlApplicationEngine()

    """Needed to close the app with Ctrl+C"""
    signal.signal(signal.SIGINT, signal.SIG_DFL)

    """Use the desktop's Qt Quick Controls style unless another one is set"""
    if not os.environ.get("QT_QUICK_CONTROLS_STYLE"):
        os.environ["QT_QUICK_CONTROLS_STYLE"] = "org.kde.desktop"

    base_path = os.path.abspath(os.path.dirname(__file__))
    url = QUrl(f"file://{base_path}/qml/main.qml")
    engine.load(url)

    if len(engine.rootObjects()) == 0:
        quit()

    app.exec()


if __name__ == "__main__":
    main()
```

The import `from md_converter import MdConverter` in `simplemdviewer_app.py` makes both Python and the QML engine aware of the new `MdConverter`. We add `# noqa: F401` just so linters don't complain about the unused import later.

The class is registered with QML in the file where it is defined, with the `@QmlElement` decorator in `md_converter.py`. Let's look at it again:

```python
from markdown import markdown
from PySide6.QtCore import QObject, Signal, Slot, Property
from PySide6.QtQml import QmlElement

QML_IMPORT_NAME = "org.kde.simplemdviewer"
QML_IMPORT_MAJOR_VERSION = 1

@QmlElement
class MdConverter(QObject):
    """A simple markdown converter"""
```

The variables `QML_IMPORT_NAME` and `QML_IMPORT_MAJOR_VERSION` set the import name and version of the `MdConverter` type.

Change `main.qml` to:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.simplemdviewer

Kirigami.ApplicationWindow {
    id: root

    title: qsTr("Simple Markdown viewer")

    minimumWidth: Kirigami.Units.gridUnit * 20
    minimumHeight: Kirigami.Units.gridUnit * 20
    width: minimumWidth
    height: minimumHeight

    pageStack.initialPage: initPage

    Component {
        id: initPage

        Kirigami.Page {
            title: qsTr("Markdown Viewer")

            MdConverter {
                id: mdconverter

                sourceText: sourceArea.text
            }
 
            ColumnLayout {
                anchors {
                    top: parent.top
                    left: parent.left
                    right: parent.right
                }
                Controls.TextArea {
                    id: sourceArea

                    placeholderText: qsTr("Write some Markdown code here")
                    wrapMode: Text.WrapAnywhere
                    Layout.fillWidth: true
                    Layout.minimumHeight: Kirigami.Units.gridUnit * 5
                }

                RowLayout {
                    Layout.fillWidth: true

                    Controls.Button {
                        text: qsTr("Format")

                        onClicked: formattedText.text = mdconverter.mdFormat()
                    }

                    Controls.Button {
                        text: qsTr("Clear")

                        onClicked: {
                            sourceArea.text = ""
                            formattedText.text = ""
                        }
                    }
                }

                Text {
                    id: formattedText

                    textFormat: Text.RichText
                    wrapMode: Text.WordWrap

                    Layout.fillWidth: true
                    Layout.minimumHeight: Kirigami.Units.gridUnit * 5
                }
            }
        }
    }
}
```

The updated QML code:

1. imports the `org.kde.simplemdviewer` module
2. creates an `MdConverter` object
3. updates the `onClicked` signal handler of the "Format" button to call the `mdFormat()` function of the converter object

### Final test run

At last, test your new application, from the `src/` directory:

```bash
python3 simplemdviewer_app.py
```

Play with adding some Markdown text. Hooray!

To package and distribute it, continue with [Python package](package.md).
