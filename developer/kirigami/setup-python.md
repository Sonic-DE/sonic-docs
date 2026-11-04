---
title: Setup with Python
description: Create your first Kirigami application with PySide.
source_url: https://develop.kde.org/docs/getting-started/kirigami/setup-python/
source_authors: [Josep M. Ferrer, Nicolas Fella, Phu Nguyen, Thiago Sueto, Tomasz Snopek]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-pyside (PySide6 6.12.0 built against Qt 6.11.3), sonic-frameworks-quick-ui (Kirigami); the example was run as a module with SonicDE's PySide and Kirigami, offscreen, without QML errors
---

# Setup with Python

## Prerequisites

You need Kirigami and PySide, Qt for Python. SonicDE ships both: Kirigami in `sonic-frameworks-quick-ui`, and PySide 6 in `sonic-pyside`, built against the same Qt as the rest of SonicDE. Install SonicDE from your distribution or build it with sonicde-builder (see [Building Sonic-DE](../building.md)). You also need `pipx` to run and install the application.

## Project structure

Create the project folder, `kirigami_python/`:

```text
kirigami_python/
├── README.md
├── LICENSE.txt
├── MANIFEST.in                        # To add our QML files
├── pyproject.toml                     # The main file to manage the project
├── org.kde.kirigami_python.desktop
└── src/
    ├── __init__.py                    # To import the src/ directory as a package
    ├── __main__.py                    # To signal app as the entrypoint
    ├── app.py
    └── qml/
        └── Main.qml
```

The package is called `kirigami_python`, the "executable" (console script) `kirigami_hello`, and the entry point is `app`.

> **Tip:** Create the folders with `mkdir -p kirigami_python/src/qml/`.

### pyproject.toml

Since [PEP 621](https://peps.python.org/pep-0621/), a modern Python application needs only one TOML file for all its metadata, package information and dependencies. This one is a good start and can be extended later.

```toml
[build-system]
requires = ["setuptools>=77"]
build-backend = "setuptools.build_meta"

[project]
name = "kirigami_python"
version = "0.1"
authors = [
    {name = "Konqi", email = "konqi@example.com"}
]
license = "GPL-3.0-or-later"
classifiers = [
    "Development Status :: 5 - Production/Stable",
    "Intended Audience :: End Users/Desktop",
    "Topic :: Utilities",
    "Programming Language :: Python",
    "Operating System :: POSIX :: Linux",
]

[project.scripts]
kirigami_hello = "kirigami_python.app:main"

[tool.setuptools]
packages = ["kirigami_python", "kirigami_python.qml"]
package-dir = {kirigami_python = "src"}
include-package-data = true

[tool.setuptools.data-files]
"share/applications" = ["org.kde.kirigami_python.desktop"]
```

As described under [Project structure](#project-structure), the package is `kirigami_python`, the executable `kirigami_hello`, and the entry point `app`. In particular:

- `[project.scripts]` defines a console script that setuptools generates for running the application, here `kirigami_hello`.
- `kirigami_hello` runs the `main()` function of `app.py` in the `kirigami_python` package.
- Python projects usually have their package in the root folder. `package-dir` makes the `src/` folder act as the package's root instead.
- That is why the console script runs `kirigami_python → app`, not `kirigami_python → src → app`,
- and why `importlib.resources.files()` in [app.py](#srcapppy) uses `kirigami_python → qml → Main.qml`, not `kirigami_python → src → qml → Main.qml`.

### org.kde.kirigami_python.desktop

[Desktop entry files](https://specifications.freedesktop.org/desktop-entry-spec/latest/) mainly show your application in the application launcher. Name it in reverse-DNS form with the `.desktop` extension, such as `org.kde.kirigami_python.desktop`:

```ini
[Desktop Entry]
Name=Kirigami Tutorial in Python
Exec=kirigami_hello
Icon=kde
Type=Application
Terminal=false
Categories=Utility
```

(The original file also has translations of `Name`; see [Desktop file](../additional/desktop-file.md).)

### MANIFEST.in

This file lists additional files the package must contain for the application to run. Python doesn't put QML files in packages by default, but the application needs them.

```text
include src/qml/*.qml
```

### src/app.py

```python
#!/usr/bin/env python3

import os
import sys
import signal
from importlib.resources import files

from PySide6.QtWidgets import QApplication
from PySide6.QtCore import QUrl
from PySide6.QtQml import QQmlApplicationEngine

def main():
    app = QApplication(sys.argv)
    engine = QQmlApplicationEngine()

    """Needed to close the app with Ctrl+C"""
    signal.signal(signal.SIGINT, signal.SIG_DFL)

    """Use the desktop's Qt Quick Controls style unless another one is set"""
    if not os.environ.get("QT_QUICK_CONTROLS_STYLE"):
        os.environ["QT_QUICK_CONTROLS_STYLE"] = "org.kde.desktop"

    base_path = files('kirigami_python').joinpath('qml', 'Main.qml')
    url = QUrl(f"{base_path}")
    engine.load(url)

    app.exec()

if __name__ == "__main__":
    main()
```

It is a graphical application, so `main()` should only run when the script is run, not when it is imported: hence `if __name__ == "__main__"` at the end.

We create a `QApplication` (the `org.kde.desktop` style needs one rather than a `QGuiApplication`) and the QML engine; `app.exec()` keeps the application running until it is closed. `importlib.resources.files()` gets the path of a file in the package, here `Main.qml`, which we load into the QML engine as the entry point of the user interface.

### src/\_\_init\_\_.py

Create an empty `kirigami_python/src/__init__.py`. It only has to exist for Python to import the folder as a package:

```bash
touch __init__.py
```

### src/\_\_main\_\_.py

Create `kirigami_python/src/__main__.py` with:

```python
from . import app

app.main()
```

This imports `app` from the package and runs the application's `main()` function.

### src/qml/Main.qml

```qml
// Includes relevant modules used by the QML
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

// Provides basic features needed for all kirigami applications
Kirigami.ApplicationWindow {
    // Unique identifier to reference this object
    id: root

    width: 400
    height: 300

    // Window title
    title: "Hello World"

    // Set the first page that will be loaded when the app opens
    // This can also be set to an id of a Kirigami.Page
    pageStack.initialPage: Kirigami.Page {
        Controls.Label {
            // Center label horizontally and vertically within parent object
            anchors.centerIn: parent
            text: "Hello World!"
        }
    }
}
```

This is the application's user interface. It is the same as in [Setup with C++](setup-cpp.md#mainqml), which explains it in detail, except that the strings aren't translated here: the C++ version sets up `i18n()` in `main.cpp`.

## Running the application

You can run the `kirigami_hello` console script without installing it first:

```bash
pipx run --system-site-packages --spec . kirigami_hello
```

`--system-site-packages` gives Python access to the Python packages installed on your system, here SonicDE's PySide. That is required because Kirigami and PySide must be built against the same Qt, which they are when both come from SonicDE.

`--spec` gives the path of the source code or wheel package that contains the program, and `kirigami_hello` is the script to run.

To build and install the Python package:

```bash
pipx install --force --system-site-packages .
```

The package is installed to `~/.local/share/pipx/venvs/kirigami-python`, and the script to `~/.local/bin/kirigami_hello`.

> **pipx and pip:** This tutorial uses `pipx` to make the project easy to run and install. [PEP 668](https://peps.python.org/pep-0668/) recommends `pipx` for running Python applications; `pip` is multi-purpose and also installs importable modules. The same can be done by hand with `venv`, `build` and `pip`.

Then start the application:

```bash
kirigami_hello
```

To run it in mobile mode, set `QT_QUICK_CONTROLS_MOBILE=1`:

```bash
QT_QUICK_CONTROLS_MOBILE=1 kirigami_hello
```

Voilà! Your first Kirigami application appears.
