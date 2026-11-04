---
title: Next steps
description: What to do after your first Kirigami application.
source_url: https://develop.kde.org/docs/getting-started/kirigami/introduction-next_steps/
source_authors: [Alessio Mattiazzi, Carl Schwan, Claudio Cambra, Felipe Kinoshita, Heqro Iglens, Martin Frueh, Mikhail Zolotukhin, Petre Tudor, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "SonicDE's repositories (which use Kirigami: QML imports of org.kde.kirigami), sonic-docs home.md, sonicde.org footer (community channels)"
---

# Next steps

## What we have built

In the last few steps you built a basic but working Kirigami application that adds date countdowns. Along the way you learned about Kirigami and Qt Quick components, how QML works, basic application layouts, and more. Not bad at all!

You now know the basics behind many of SonicDE's applications. What now? Here are some pointers.

## Contributing to SonicDE

One of the best ways to improve your skills is to use them. SonicDE welcomes new developers.

[Building Sonic-DE](../building.md) explains how to build the whole desktop from source. SonicDE's code is on GitHub, in the [Sonic-DE organization](https://github.com/Sonic-DE): report issues and propose changes there. To talk with other developers, join SonicDE's [Matrix room](https://matrix.to/#/#sonicdesktop:matrix.org) or [Discord server](https://discord.gg/cNZMQ62u5S).

With what you have learned, you can work on SonicDE's Kirigami applications. Several SonicDE components are built with it, for example:

| Component | What it is | Repository |
| --- | --- | --- |
| Welcome Center | The welcome application for new users | [sonic-welcome-center](https://github.com/Sonic-DE/sonic-welcome-center) |
| System Monitor | Shows and manages processes and system resources | [sonic-system-monitor](https://github.com/Sonic-DE/sonic-system-monitor) |
| Screenies | The screenshot tool | [sonic-screenies](https://github.com/Sonic-DE/sonic-screenies) |
| Network management | Network settings and the network widget | [sonic-network-manager](https://github.com/Sonic-DE/sonic-network-manager) |
| Print management | Printer settings | [sonic-print-management](https://github.com/Sonic-DE/sonic-print-management) |
| TV interface | SonicDE's interface for TVs | [sonic-tv-interface](https://github.com/Sonic-DE/sonic-tv-interface) |

## Learning more

Not quite ready yet? That's fine too.

The applications above are valuable learning resources: read their code to see how experienced developers built complete applications, and use their techniques yourself.

For a gentler start, here are some resources.

### The backend and C++

We learned a lot about QML, but little about the code behind it, which is an essential part of application development.

#### C++ and Qt with Kirigami

The advanced part of this tutorial has pages to get you started:

| Page | Topic |
| --- | --- |
| [Understanding CMakeLists](understanding-cmakelists.md) | CMake and how to build your application. |
| [Figuring out main.cpp](main-cpp.md) | The central C++ file that starts your application. |
| [Connect logic to your QML user interface](connect-backend.md) | Add functionality in C++ and connect it to your user interface. |
| [About page](about-page.md) | Add an About page to your application. |

#### C++ for beginners

If you are new to C++, there are many resources on the web. Some that may help:

| Resource | Topic |
| --- | --- |
| [LearnCpp](https://www.learncpp.com/) | Tutorials for getting to grips with C++ |
| [cppreference](https://en.cppreference.com/w/) | A C++ reference site |
| [Wikibooks C++](https://en.wikibooks.org/wiki/C%2B%2B_Programming) | A comprehensive wikibook with C++ lessons and exercises |
| [W3Schools C++](https://www.w3schools.com/cpp/cpp_intro.asp) | C++ tutorials and other resources for beginners |

### Classic applications with QtWidgets

To work on applications such as the Ecco file manager or the terminal, you need QtWidgets, a completely different way of building user interfaces with Qt. Complex applications and those with a traditional design are often built with QtWidgets.

QtWidgets is somewhat more daunting than QML (and *much* more C++-intensive). The [KXmlGui tutorial](../kxmlgui/index.md) helps you get familiar with it.

### More QML and Qt Quick

Qt is large, and so are QML and Qt Quick. Much of their functionality isn't covered here, but there is plenty of documentation:

- To look up what a component does, see [Qt's QML documentation](https://doc.qt.io/qt-6/qtquick-index.html).
- For a guided way to learn, [the QML Book](https://www.qt.io/product/qt6/qml-book) is a great place to start.

### More Kirigami

This documentation has much more about Kirigami: the component pages of this tutorial describe more of the QML components it provides, and the [Kirigami API reference](/docs/api/kirigami/kirigami-index) documents all of them.

## The sky's the limit!

Don't be intimidated by all this material! Nobody starts out able to build a whole desktop. As long as you are nice, you will be welcome.

Good luck!
