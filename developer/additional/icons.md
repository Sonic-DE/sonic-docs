---
title: Icons
description: Use icons from the user's icon theme in your application.
source_url: https://develop.kde.org/docs/features/additional-features/icons/
source_authors: [Carl Schwan, Kunda Ki, Marius P, Mikhail Zolotukhin, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: Qt 6.11 documentation (QIcon::fromTheme), sonic-frameworks-icon-themes (KIconLoader), sonic-frameworks-quick-ui (Kirigami Icon, KF6KirigamiMacros.cmake), sonic-theme-sdk (iconexplorer), sonic-silver (look-and-feel defaults)
---

# Icons

Your application will probably want icons that follow the user's icon theme. In SonicDE the default icon theme is Silver (`silver`).

Use [QIcon::fromTheme()](https://doc.qt.io/qt-6/qicon.html#fromTheme) in QtWidgets applications, or Kirigami's [Icon](/docs/api/kirigami/qml-org-kde-kirigami-primitives-icon) in QtQuick applications. Both take the icon's name in the icon theme.

SonicDE and the other major Linux desktops follow the freedesktop.org [Icon Theme Specification](https://specifications.freedesktop.org/icon-theme-spec/latest/) and [Icon Naming Specification](https://specifications.freedesktop.org/icon-naming-spec/latest/). Names fall back to more general ones: if there is no `document-open-recent` icon, the `document-open` icon is used, and if that doesn't exist either, the `document` icon.

## Finding the right icons

SonicDE's Icon Explorer (`iconexplorer`, in `sonic-theme-sdk`) searches the icons of your icon theme. You can search for icons by name and by category, see an icon with different color schemes, and compare it with other icon themes.

- **Color scheme:**, in the toolbar, previews the icons with another color scheme, so you can check that they follow it.
- For the selected icon: **Open with External Program**, **Open Containing Folder**, **Copy Name to Clipboard** and **View in Other Icon Themes**.
- **Take Screenshot…** saves an image of the selected icon at every size, in **Breeze Colors**, **Breeze Dark Colors**, **Breeze (Normal) and Breeze Dark**, or the **Active Color Scheme**. **File > Export Montage with Color Scheme…** in the global menu does the same.

## Example

In a QtWidgets application:

```cpp
QIcon undoicon = QIcon::fromTheme("edit-undo");
```

In a QtQuick application:

```qml
import org.kde.kirigami as Kirigami

Kirigami.Icon {
    source: "edit-undo"
}
```

Since Qt 6.7, `QIcon::fromTheme()` also takes a [QIcon::ThemeIcon](https://doc.qt.io/qt-6/qicon.html#ThemeIcon-enum), for example `QIcon::fromTheme(QIcon::ThemeIcon::EditUndo)`, and accepts a fallback icon used when the theme has none.

## Platforms other than Linux

Other platforms have no icon theme.

### Android

On Android, package the Breeze icons you use with Kirigami's `kirigami_package_breeze_icons()` CMake function:

```cmake
if(ANDROID)
    kirigami_package_breeze_icons(ICONS
        edit-undo
        edit-redo
    )
endif()
```
