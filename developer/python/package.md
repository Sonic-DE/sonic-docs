---
title: Creating a Python package
description: Understand the requirements to create your own Python package.
source_url: https://develop.kde.org/docs/getting-started/python/python-package/
source_authors: [Shyamnath Premnadh, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the package built with python -m build (no setuptools warnings), installed editable and from the wheel into a clean environment, and run each way with SonicDE's PySide and Kirigami; appstreamcli validate and desktop-file-validate on the metadata"
---

# Creating a Python package

## Packaging the application

To distribute the application to users we have to package it. We use the [setuptools](https://pypi.org/project/setuptools/) library.

Currently, the project can only be run as a script, by running the file directly with `python3 /path/to/simplemdviewer_app.py`. That's not a convenient way to run a desktop application.

The goal of this page is to make the project available as a console script and as a module:

* It is a console script when you can run it with `simplemdviewer`.
* It is a module when you can run it with `python3 -m simplemdviewer`.

To learn more about Python packaging, see the [Python Packaging User Guide](https://packaging.python.org/en/latest/).

## General structure

Let's recapitulate what the file structure of the project should be:

```text
simplemdviewer
├── README.md
├── LICENSE.txt
├── MANIFEST.in                # To add our QML file to the Python module
├── pyproject.toml             # The main file to manage the project
├── org.kde.simplemdviewer.desktop
├── org.kde.simplemdviewer.svg
├── org.kde.simplemdviewer.metainfo.xml
└── src/
    ├── __init__.py            # To import the src/ directory as a package
    ├── __main__.py            # To signal simplemdviewer_app as the entrypoint
    ├── simplemdviewer_app.py
    ├── md_converter.py
    └── qml/
        └── main.qml
```

Create a `simplemdviewer/pyproject.toml`:

```toml
[build-system]
requires = ["setuptools>=77"]
build-backend = "setuptools.build_meta"

[project]
name = "org.kde.simplemdviewer"
version = "0.1"
authors = [{name = "Example Author", email = "example@author.org"}]
maintainers = [{name = "Example Author", email = "example@author.org"}]
description = "A simple markdown viewer"
license = "GPL-3.0-or-later"
license-files = ["LICENSE.txt"]
classifiers = [
    "Development Status :: 5 - Production/Stable",
    "Intended Audience :: End Users/Desktop",
    "Topic :: Utilities",
    "Programming Language :: Python",
    "Operating System :: POSIX :: Linux",
]
keywords = ["viewer converter markdown"]
urls = {Homepage = "https://example.com/simplemdviewer"}
dependencies = ["markdown"]

[project.readme]
file = "README.md"
content-type = "text/markdown"

[project.scripts]
simplemdviewer = "simplemdviewer.simplemdviewer_app:main"

[tool.setuptools]
packages = ["simplemdviewer", "simplemdviewer.qml"]
package-dir = {simplemdviewer = "src"}
include-package-data = true

[tool.setuptools.data-files]
"share/applications" = ["org.kde.simplemdviewer.desktop"]
"share/icons/hicolor/scalable/apps" = ["org.kde.simplemdviewer.svg"]
"share/metainfo" = ["org.kde.simplemdviewer.metainfo.xml"]
```

Don't worry about the details for now. We will revisit each part as needed.

The following four sections of `pyproject.toml` are fairly straightforward:

* `[build-system]` tells Python to fetch and use setuptools to build the project. Version 77 or later understands the `license` and `license-files` keys.
* `[project]` contains the general metadata of the project.
* `[project.readme]` sets a default README file for the project, in Markdown.
* `[tool.setuptools.data-files]` says where setuptools should install additional data files that aren't typically part of a Python package.

> **Note:** You may see older projects that combine `setup.py` to initialize setuptools, `setup.cfg` for metadata and package information, and `pyproject.toml` for dependencies. [PEP 621](https://peps.python.org/pep-0621/) has since defined `pyproject.toml` as the main way to specify a project's metadata, and setuptools can [use `pyproject.toml` as a declarative way to define package information](https://setuptools.pypa.io/en/latest/userguide/quickstart.html#transitioning-from-setup-py-to-declarative-config). A `setup.py` script is no longer needed: all metadata, package information and dependencies go in `pyproject.toml`.

## App metadata

Let's get the metadata out of the way first, namely what the `[project.readme]` and `[tool.setuptools.data-files]` sections list.

Create a `simplemdviewer/README.md`:

```markdown
# Simple Markdown Viewer

A simple Markdown viewer created with Kirigami, QML and Python.
```

Another important piece is the license of the project. Create a `simplemdviewer/LICENSE.txt` and add the text of the [license](https://www.gnu.org/licenses/gpl-3.0.txt):

```bash
wget https://www.gnu.org/licenses/gpl-3.0.txt --output-document LICENSE.txt
```

Create a `simplemdviewer/MANIFEST.in` file with the following contents:

```text
include src/qml/*.qml
```

This file declares additional source files that should be in the package when the application runs.

A few last pieces and we can start changing the code. We add:

1. The [AppStream](https://www.freedesktop.org/wiki/Distributions/AppStream/) metadata used to show the application in software stores.
2. A [Desktop Entry](https://specifications.freedesktop.org/desktop-entry-spec) file to add the application to the application launcher.
3. An application icon.

Create a new `simplemdviewer/org.kde.simplemdviewer.desktop`. This file shows our Markdown viewer in application menus and launchers.

```ini
[Desktop Entry]
Name=Simple Markdown Viewer
GenericName=Markdown Viewer
Comment=A simple Markdown viewer application
Version=1.0
Exec=simplemdviewer
Icon=org.kde.simplemdviewer
Type=Application
Terminal=false
Categories=Office;
X-KDE-FormFactor=desktop;tablet;handset;
```

Add a new `simplemdviewer/org.kde.simplemdviewer.metainfo.xml`. This file shows the application in software stores.

```xml
<?xml version="1.0" encoding="utf-8"?>
<component type="desktop-application">
  <id>org.kde.simplemdviewer</id>
  <metadata_license>CC0-1.0</metadata_license>
  <project_license>GPL-3.0-or-later</project_license>
  <name>Simple Markdown Viewer</name>
  <summary>A simple markdown viewer application</summary>
  <developer id="com.example">
    <name>Example Author</name>
  </developer>
  <description>
    <p>Simple Markdown Viewer is a showcase application for QML with Python development</p>
  </description>
  <launchable type="desktop-id">org.kde.simplemdviewer.desktop</launchable>
  <content_rating type="oars-1.1"/>
  <url type="homepage">https://example.com/simplemdviewer</url>
  <releases>
    <release version="0.1" date="2026-11-04">
      <description>
        <p>First release</p>
      </description>
    </release>
  </releases>
  <provides>
    <binary>simplemdviewer</binary>
  </provides>
</component>
```

For this tutorial, the well-known Markdown icon is fine.

Get the [Markdown](https://en.wikipedia.org/wiki/Markdown#/media/File:Markdown-mark.svg) icon and save it as `simplemdviewer/org.kde.simplemdviewer.svg`:

```bash
wget https://upload.wikimedia.org/wikipedia/commons/4/48/Markdown-mark.svg --output-document org.kde.simplemdviewer.svg
```

The icon needs to be perfectly square, which you can do with [Inkscape](https://inkscape.org):

1. Open `org.kde.simplemdviewer.svg` in Inkscape.
2. Press Ctrl+A to select everything.
3. In the `W:` text field at the top, type 128 and press Enter.
4. Go to File → Document Properties...
5. Change the `Width:` text field to 128 and press Enter.
6. Save the file.

## Code changes

Before creating a console script or module, we first need to turn our existing code into a package.

Create an empty `simplemdviewer/src/__init__.py` file. It just needs to exist for a directory to be imported as a package:

```bash
touch src/__init__.py
```

Python packages usually keep their source code directly in the root folder. Since we use a custom package directory, `src/`, we pass it as the `package-dir` of our `simplemdviewer` package in `pyproject.toml`. The `qml/` folder is listed as a package too, so that setuptools installs `main.qml`:

```toml
[tool.setuptools]
packages = ["simplemdviewer", "simplemdviewer.qml"]
package-dir = {simplemdviewer = "src"}
include-package-data = true
```

Here, the package name is `simplemdviewer`, and its source code is in `simplemdviewer/src/` instead of the root folder. With a package name, we can import modules through it in our code.

Update `simplemdviewer/src/simplemdviewer_app.py` to:

```python
#!/usr/bin/env python3

import os
import sys
import signal
from PySide6.QtWidgets import QApplication
from PySide6.QtCore import QUrl
from PySide6.QtQml import QQmlApplicationEngine
from simplemdviewer.md_converter import MdConverter  # noqa: F401

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

Create a `__main__.py` file in the `simplemdviewer/src/` directory:

```python
from . import simplemdviewer_app

simplemdviewer_app.main()
```

This imports the `simplemdviewer_app` module from the current package (`src/`), and immediately runs the application's `main()` function.

Make sure you have a project script in your `pyproject.toml`:

```toml
[project.scripts]
simplemdviewer = "simplemdviewer.simplemdviewer_app:main"
```

Now the application can run as an executable package and as a module.

## Running directly, as a module, and as a console script

When you run the script directly with `python3 src/simplemdviewer_app.py`, Python sets its `__name__` to `__main__`. If the same file is imported instead, `__name__` is the name of the module. The `if` condition makes sure `main()` only runs when the script is run, not every time another script imports it:

```python
if __name__ == "__main__":
    main()
```

> **Note:** Since `simplemdviewer_app.py` now imports `simplemdviewer.md_converter`, running it directly only works once the package is installed; otherwise Python can't find the `simplemdviewer` package.

On top of that, we use setuptools to specify the *package*:

```toml
[tool.setuptools]
packages = ["simplemdviewer", "simplemdviewer.qml"]
package-dir = {simplemdviewer = "src"}
```

We specify a package called `simplemdviewer`, whose source code is in `simplemdviewer/src/`. This is needed because we don't want to call the application `simplemdviewer_app` every time, as module or console script: we want the friendlier name `simplemdviewer`.

To let the application run as a module, as in `python3 -m simplemdviewer`, all we need is a `__main__.py` in the same folder as the code:

```python
from . import simplemdviewer_app

simplemdviewer_app.main()
```

When you run the package `simplemdviewer` as a module, Python looks for its `__main__.py`, which in turn calls the `main()` function in our `simplemdviewer_app.py`:

```python
def main():
    """Initializes and manages the application execution"""
    app = QApplication(sys.argv)
    engine = QQmlApplicationEngine()
```

In this case, the module's `__name__` is `simplemdviewer.simplemdviewer_app`, not `__main__` as when running the script directly, so the `if` condition doesn't apply; `__main__.py` calls `main()` itself.

> **Note:** `setuptools` isn't involved in running a script directly or running a module with `python3 -m`. For modules, though, it installs the package under its name, which matters for the module name.

Now, to create a console script:

```toml
[project.scripts]
simplemdviewer = "simplemdviewer.simplemdviewer_app:main"
```

This specifies a *project script*, the entry point that runs the application. It's a console script because it can run in a terminal; a GUI script would always run without a terminal, but this only matters on Windows. A project script is a small wrapper that setuptools creates around the application, so it can be run like an executable.

When you run the command `simplemdviewer` in the terminal, this wrapper imports the module `simplemdviewer_app` from the `simplemdviewer` package and runs its `main()` function directly, bypassing both `__main__` checks.

In other words:

| Method | Handled by | Calls `main()` through | Runs with |
| --- | --- | --- | --- |
| Run directly | Python | the `__name__` check | `python3 simplemdviewer_app.py` |
| Module | Python | `__main__.py` | `python3 -m simplemdviewer` |
| Console script | The wrapper setuptools creates | the project script | `simplemdviewer` |

## Running the application

From inside the `simplemdviewer/` directory, install it in development mode and run it:

```bash
python3 -m pip install --editable .
# As a module
python3 -m simplemdviewer
# As a console script
simplemdviewer
```

If the required files are in the right places, the application should run both as a module and as a console script.

Now that we know it works, let's generate the package for our program.

Make sure the latest version of `build` is installed:

```bash
python3 -m pip install --upgrade build
```

From inside the `simplemdviewer/` directory, run:

```bash
python3 -m build
```

When the build completes, two archives are created in the `dist/` directory:

1. The `org_kde_simplemdviewer-0.1.tar.gz` source archive.
2. The `org_kde_simplemdviewer-0.1-py3-none-any.whl` package, ready for distribution in places such as PyPI.

To test the application properly, install it in a clean virtual environment that has PySide:

```bash
deactivate
python3 -m venv --system-site-packages clean-env/
source clean-env/bin/activate
python3 -m pip install dist/org_kde_simplemdviewer-0.1-py3-none-any.whl
```

Run:

```bash
# As a module
python3 -m simplemdviewer
# As a console script
simplemdviewer
```

At this point you can tag and release the source code. Linux distributions can package it and add the application to their software repositories.

Well done.
