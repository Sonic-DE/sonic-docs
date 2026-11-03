---
title: "KAnimatedButton Class"
description: "An extended version of QToolButton which can display an animation."
---

# KAnimatedButton Class

An extended version of [QToolButton](https://doc.qt.io/qt-6/qtoolbutton.html) which can display an animation. [More...](#details)

- **Header:** `#include <KAnimatedButton>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QToolButton](https://doc.qt.io/qt-6/qtoolbutton.html)

[List of all members, including inherited members](kanimatedbutton-members.md)

## Properties

- [animationPath : QString](#animationPath-prop)

## Public Functions

- [KAnimatedButton(QWidget \*parent = nullptr)](#KAnimatedButton)
- [QString animationPath() const](#animationPath)
- [void setAnimationPath(const QString &path)](#setAnimationPath)

## Public Slots

- [void start()](#start)
- [void stop()](#stop)

## Detailed Description {#details}

This widget extends [QToolButton](https://doc.qt.io/qt-6/qtoolbutton.html) with the ability to display an animation. All you need to do is pass along a path to a file containing an animation, it can be anything supported by [QMovie](https://doc.qt.io/qt-6/qmovie.html), or a picture containing all the frames of the animation next to each other (each frame being assumed of having the same size).

## Property Documentation {#property-documentation}

### animationPath : QString {#animationPath-prop}

**Access functions:**

- `QString` **[animationPath](kanimatedbutton.md#animationPath)**() const
- `void` **[setAnimationPath](kanimatedbutton.md#setAnimationPath)**(const `QString` &*path*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAnimatedButton::KAnimatedButton(QWidget \**parent* = nullptr) {#KAnimatedButton}

Construct an animated tool button.

`parent` The parent widget

### QString KAnimatedButton::animationPath() const {#animationPath}

Returns the path used to load the animation

> **Note:** Getter function for property [animationPath](kanimatedbutton.md#animationPath-prop).

*See also* [setAnimationPath](kanimatedbutton.md#setAnimationPath)()

### void KAnimatedButton::setAnimationPath(const QString &*path*) {#setAnimationPath}

Sets the path to the file which contains the animation to load.

`path` The path of the file containing the animation

> **Note:** Setter function for property [animationPath](kanimatedbutton.md#animationPath-prop).

*See also* [animationPath](kanimatedbutton.md#animationPath)()

### \[slot\] void KAnimatedButton::start() {#start}

Starts the animation from frame 1

### \[slot\] void KAnimatedButton::stop() {#stop}

Stops the animation. This will also reset the widget to frame 1.
