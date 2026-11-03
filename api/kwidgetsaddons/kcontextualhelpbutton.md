---
title: "KContextualHelpButton Class"
description: "An icon-only button for showing contextually relevant help or explanations. This class was introduced in Qt 6.2."
---

# KContextualHelpButton Class

An icon-only button for showing contextually relevant help or explanations. This class was introduced in Qt 6.2. [More...](#details)

- **Header:** `#include <KContextualHelpButton>`
- **Since:** Qt 6.2
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QToolButton](https://doc.qt.io/qt-6/qtoolbutton.html)

[List of all members, including inherited members](kcontextualhelpbutton-members.md)

## Public Functions

- [KContextualHelpButton(QWidget \*parent = nullptr)](#KContextualHelpButton)
- [KContextualHelpButton(const QString &contextualHelpText, const QWidget \*heightHintWidget, QWidget \*parent)](#KContextualHelpButton-1)
- [QString contextualHelpText() const](#contextualHelpText)
- [const QWidget \*heightHintWidget() const](#heightHintWidget)
- [void setContextualHelpText(const QString &contextualHelpText)](#setContextualHelpText)
- [void setHeightHintWidget(const QWidget \*heightHintWidget)](#setHeightHintWidget)

## Detailed Description {#details}

[KContextualHelpButton](kcontextualhelpbutton.md) allows hiding text of any length behind a small icon-only button. Hovering over the button with a mouse cursor or pressing the button will show the text. It can contain images and links. It is accessible by keyboard and to screen readers.

When to Use

Sometimes users require help or an explanation, even experts. This help should be readily available exactly where and when a user needs it. A [KContextualHelpButton](kcontextualhelpbutton.md) makes clear that inline help is available without really cluttering up the user interface. In that sense it is superior to setting tooltips which are completely invisible until invoked and therefore easy to miss. Especially for touch users the [KContextualHelpButton](kcontextualhelpbutton.md) is preferable.

When Not to Use

If the text is important for the user to understand and can be kept very short, place it inline below the control it affects. If there is no room to put this [KContextualHelpButton](kcontextualhelpbutton.md), use [QWidget::setToolTip](https://doc.qt.io/qt-6/qwidget.html#toolTip-prop)() for shorter texts and QWidget::SetWhatsThis() for longer text or text that should contain hyperlinks. If your software is not already using the KXmlGui framework, consider using KToolTipHelper from KXmlGui to make the [whatsThis](https://doc.qt.io/qt-6/qwidget.html#whatsThis-prop)() help more discoverable.

How to Use

The most simple way is creating it like any other button and then setting the help text:

```cpp
auto contextualHelpButton = new KContextualHelpButton{this};
contextualHelpButton->setContextualHelpText(xi18nc("@info", "<para>A nicely formatted help text. Notice the 'para' tags at the side!</para>"));
```

The most common use of this component might be on settings pages which oftentimes use a [QFormLayout](https://doc.qt.io/qt-6/qformlayout.html). Here is an example on how to use it next to a [QCheckBox](https://doc.qt.io/qt-6/qcheckbox.html). Unfortunately we need to make the [KContextualHelpButton](kcontextualhelpbutton.md) aware of the [QCheckBox](https://doc.qt.io/qt-6/qcheckbox.html) here or it will increase the height of the row in the [QFormLayout](https://doc.qt.io/qt-6/qformlayout.html) which might look bad. The help text in this example contains an image and a working hyperlink:

```cpp
auto formLayout = new QFormLayout(this);
auto checkBox = new QCheckBox(i18nc("@option:check", "Check this box"), this);
auto contextualHelpButton = new KContextualHelpButton{
     xi18nc("@info",
            "<para>A help text containing an icon <img src=':/icon.png'> and a <a href=\"http://www.kde.org\">link</a>.</para>"),
     checkBox,
     this};
auto rowLayout = new QHBoxLayout{this};
rowLayout->addWidget(checkBox);
rowLayout->addWidget(contextualHelpButton);
formLayout->addRow(i18nc("@title:group", "Row label:"), rowLayout);
```

This class is meant to be kept somewhat consistent with the QML equivalent which is also called ContextualHelpButton.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KContextualHelpButton::KContextualHelpButton(QWidget \**parent* = nullptr) {#KContextualHelpButton}

*See also* KContextualHelpButton::ContextualHelpButton()

### \[explicit\] KContextualHelpButton::KContextualHelpButton(const QString &*contextualHelpText*, const QWidget \**heightHintWidget*, QWidget \**parent*) {#KContextualHelpButton-1}

`contextualHelpText` The text to show when hovering or clicking this button. Consider formatting this nicely using xi18nc().

`heightHintWidget` The [KContextualHelpButton](kcontextualhelpbutton.md) will report the `heightHintWidget` 's [sizeHint](https://doc.qt.io/qt-6/qtoolbutton.html#sizeHint)().[height](https://doc.qt.io/qt-6/qwidget.html#height-prop)() as its own [sizeHint](https://doc.qt.io/qt-6/qtoolbutton.html#sizeHint)().[height](https://doc.qt.io/qt-6/qwidget.html#height-prop)(). This is useful to make sure that adding this [KContextualHelpButton](kcontextualhelpbutton.md) to a layout will not increase the layout's total height.

`parent` The parent widget that gets ownership over the lifetime of this [KContextualHelpButton](kcontextualhelpbutton.md).

### QString KContextualHelpButton::contextualHelpText() const {#contextualHelpText}

Returns the help text which is shown when hovering or pressing this button.

> **Note:** Getter function for property contextualHelpText.

*See also* [setContextualHelpText](kcontextualhelpbutton.md#setContextualHelpText)()

### const QWidget \*KContextualHelpButton::heightHintWidget() const {#heightHintWidget}

*See also* [setHeightHintWidget](kcontextualhelpbutton.md#setHeightHintWidget)()

### void KContextualHelpButton::setContextualHelpText(const QString &*contextualHelpText*) {#setContextualHelpText}

Sets the text to show when hovering or pressing this button. Consider formatting the text nicely using xi18nc().

> **Note:** Setter function for property contextualHelpText.

*See also* [contextualHelpText](kcontextualhelpbutton.md#contextualHelpText)()

### void KContextualHelpButton::setHeightHintWidget(const QWidget \**heightHintWidget*) {#setHeightHintWidget}

The [KContextualHelpButton](kcontextualhelpbutton.md) will report the `heightHintWidget` 's [sizeHint](https://doc.qt.io/qt-6/qtoolbutton.html#sizeHint)().[height](https://doc.qt.io/qt-6/qwidget.html#height-prop)() as its own [sizeHint](https://doc.qt.io/qt-6/qtoolbutton.html#sizeHint)().[height](https://doc.qt.io/qt-6/qwidget.html#height-prop)(). This is useful to make sure that adding this [KContextualHelpButton](kcontextualhelpbutton.md) to a layout will not increase the layout's total height.

*See also* [heightHintWidget](kcontextualhelpbutton.md#heightHintWidget)()
