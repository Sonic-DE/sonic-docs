---
title: Using KConfig XT
description: The main concepts of the KConfig XT configuration framework and how to use it in applications.
source_url: https://develop.kde.org/docs/features/configuration/kconfig_xt/
source_authors: [Zack Rusin, Alexander Lohnau, Carl Schwan, Chris Holland, Claudio Cambra, David Faure, Fushan Wen, Luis Büchi, Mikhail Zolotukhin, Nicolas Fella, Smit Patil, Thiago Sueto, Tobias Fella, Tomaz Canabrava, Yuki Schlarb]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-settings (kconfig_compiler, kcfg.xsd, KF6ConfigMacros.cmake, KCoreConfigSkeleton, autotests), sonic-frameworks-settings-utils (KQuickManagedConfigModule, org.kde.kcmutils), sonic-workspace d0b84fd142 (kcms/feedback)
---

# Using KConfig XT

KConfig XT generates a C++ class for your configuration from an XML description of its settings. The description is the single source of truth for the configuration's structure, and it prevents mistakes such as misspelled keys.

## The .kcfg file

A `.kcfg` file is an XML file that describes your application's configuration keys. Here is one with a single group and a few entries:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<kcfg xmlns="http://www.kde.org/standards/kcfg/1.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.kde.org/standards/kcfg/1.0
                          http://www.kde.org/standards/kcfg/1.0/kcfg.xsd" >
  <group name="General">
    <entry name="SplitterSizes" type="IntList">
      <label>How the main window is divided.</label>
    </entry>
    <entry name="Width" type="Int">
      <label>Width of the main window.</label>
      <default>600</default>
    </entry>
    <entry name="Platform" type="Enum">
      <label>Last operating system used.</label>
      <choices>
        <choice name="Linux">
          <label>Linux</label>
        </choice>
        <choice name="FreeBSD">
          <label>FreeBSD</label>
        </choice>
        <choice name="Windows">
          <label>Windows</label>
        </choice>
      </choices>
      <default>0</default> <!-- Linux -->
    </entry>
  </group>
</kcfg>
```

`SplitterSizes` stores the sizes of the application's QSplitter widgets, `Width` the width of the main window, and `Platform` the last operating system used: an enum whose value is Linux, FreeBSD or Windows.

Each entry needs at least a `name` or a `key` attribute. The key is the key in the configuration file; the name is used for the generated getter and setter. Without `key`, the name is the key. With `key` but without `name`, the name is the key with its spaces removed.

Every entry has a type. The basic types are `String`, `StringList`, `Font`, `Rect`, `RectF`, `Size`, `SizeF`, `Color`, `Point`, `PointF`, `Int`, `UInt`, `Bool`, `Double`, `DateTime`, `Time`, `LongLong`, `ULongLong`, `Url`, `UrlList` and `Password`. There are also these special types:

- **Path:** a string handled as a file path. Paths in the home directory are stored with `$HOME` in the configuration file.
- **Enum:** an enumeration. List its values in a `<choices>` tag. The application uses the values as integers, but the configuration file stores them as text, so values can be added later without breaking compatibility. A choice's `value` attribute sets the text stored for it.
- **IntList:** a list of integers, given to the application as `QList<int>`. Useful, for example, for `QSplitter` sizes.
- **PathList:** a list of paths.
- **Color:** isn't really special, but accepts special input. It becomes a `QColor`, and its default can be anything `QColor(QString)` accepts (hex or SVG color names) or `r,g,b,a` (the alpha `a` may be left out).

Always add `<label>` and `<tooltip>` tags that describe the setting: `<label>` is a short description, `<tooltip>` a longer one. Tools that let administrators set up machines use them (the old `KConfigEditor` is unmaintained). The generated class only uses these texts when the `SET_USER_TEXTS` option (`SetUserTexts=true` in a `.kcfgc` file) is set; see below.

`<min>` and `<max>` set inclusive lower and upper limits for integer settings.

An `<emit>` tag names a signal to emit when the setting changes.

An entry can have a default value, used when no configuration file sets it. Defaults are literal constants. For an enum the default is either a choice's name or its index.

### Computing the default value

Sometimes a default should be computed by a C++ expression. Add `code="true"` to the `<default>` tag. The expression is evaluated each time the generated class is created. Like every default, it isn't written to the configuration file while the setting has the default value, so a changed expression changes the setting for users who never changed it.

The code is used as a function argument, so this is valid:

`<default code="true"> true </default>`

but this isn't:

`<default code="true"> return true </default>`

For longer calculations, define and call a lambda in one go. Remember that the code runs in the constructor, so it can't rely on other settings' defaults.

```xml
<default code="true">
      [this] {
         int someValue = OtherLibrary::precalculate();
         if (someValue % 2 == 0) {
           return "Even";
         }
           return "Odd";
      } ()
   </default>
```

If the default needs a C++ header, add an `<include>` tag with it to the `.kcfg` file; you can add as many as you need.

A `<code>` tag adds code for computing defaults. Its content is inserted as it is; typically it computes a value that several entries then use as their default.

## Parameters in the configuration description

Sometimes the same settings appear in several groups, or under a group chosen at run time. Parameters, passed to the constructor of the generated class, handle that:

```xml
<kcfg>
    <kcfgfile name="rc_file_for_the_setting">
        <parameter name="masterGroup"/>
    </kcfgfile>

    <group name="Global" parentGroupName="$(masterGroup)">
      <entry> ... </entry>
    </group>
</kcfg>
```

The generated class is then created like this:

```cpp
auto *settings = new Settings("MyMasterGroup");
```

and the configuration file stores the `Global` group inside the group `MyMasterGroup`.

## Generating the class with CMake

The `.kcfg` file lists the settings. How the C++ code for them is generated is set in the `kconfig_target_kcfg_file()` CMake call (from the `KF6Config` package's `KF6ConfigMacros.cmake`):

```cmake
kconfig_target_kcfg_file(myapp
  FILE config.kcfg
  CLASS_NAME Config
  MUTATORS
  DEFAULT_VALUE_GETTERS
  SINGLETON
)
```

`FILE` and `CLASS_NAME` are required; everything else is optional. A keyword on its own, such as `MUTATORS`, switches that option on. The options are `MUTATORS`, `SINGLETON`, `CUSTOM_ADDITIONS`, `NOTIFIERS`, `DEFAULT_VALUE_GETTERS`, `ITEM_ACCESSORS`, `SET_USER_TEXTS`, `GLOBAL_ENUMS`, `USE_ENUM_TYPES`, `FORCE_STRING_FILENAME`, `GENERATE_PROPERTIES`, `PARENT_IN_CONSTRUCTOR`, `GENERATE_MOC`, `QML_REGISTRATION`, `QML_UNCREATABLE` and `KCONFIG_CONSTRUCTOR`; the arguments with a value are `VISIBILITY`, `HEADER_EXTENSION`, `SOURCE_EXTENSION`, `NAME_SPACE`, `INHERITS`, `MEMBER_VARIABLES`, `TRANSLATION_SYSTEM`, `TRANSLATION_DOMAIN`, `INCLUDE_FILES` and `SOURCE_INCLUDE_FILES`. Each corresponds to an option of a `.kcfgc` file, described in [The KDE Configuration Compiler](/docs/api/kconfigcore/kconfigcompiler).

`FILE config.kcfg` names the file that describes your settings, and `CLASS_NAME Config` the class generated from it.

Building the project then generates `config.h` and `config.cpp`, named after the class, which you include in your code.

You can also write the options into a `.kcfgc` file and add it with `kconfig_add_kcfg_files()`, as many SonicDE modules do. The feedback settings module in `sonic-workspace`, for example, has this `feedbacksettings.kcfgc`:

```ini
File=feedbacksettings.kcfg
ClassName=FeedbackSettings
IncludeFiles="KUserFeedback/Provider"
Mutators=true
DefaultValueGetters=true
GenerateProperties=true
ParentInConstructor=true
```

and adds it with `kconfig_add_kcfg_files(kcm_feedback feedbacksettings.kcfgc GENERATE_MOC)`.

## Reading and setting values

### C++

To use the settings, get the generated class's instance:

```cpp
#include "config.h"

...

auto config = Config::self();
```

Each entry gets a getter and, with `MUTATORS`, a setter, named after the entry's `name` (or `key`).

Using them is as simple as you would expect:

```cpp
auto config = Config::self();

int currentWidth = config->width();

if(currentWidth != 720)
  config->setWidth(720);
```

### QML

To use the configuration in QML, add `GENERATE_PROPERTIES` to the CMake call and register the `Config` instance as a singleton in `main.cpp`:

```cpp
auto config = Config::self();
qmlRegisterSingletonInstance("org.foo.myapp.private", 1, 0, "Config", config);
```

`Config` is then available throughout your QML, and every entry is a property of it (QML uses the properties, not the getters and setters):

```qml
import org.foo.myapp.private

Kirigami.ApplicationWindow {
  width: Config.width

  onWidthChanged: Config.width = width
}
```

Alternatively, the `QML_REGISTRATION` option adds `QML_ELEMENT` (and with `SINGLETON` also `QML_SINGLETON`) to the generated class, for registration through a QML module built with `qt_add_qml_module()` or `ecm_add_qml_module()`.

### Settings modules (KCMs)

If you [develop a settings module](kcm.md) that uses KConfig XT, don't use a singleton. Make the configuration part of your `KQuickManagedConfigModule` subclass, created with that module as its parent.

For that, add the `PARENT_IN_CONSTRUCTOR` option, which generates a `Config` class whose constructor takes an optional `QObject *parent`. The module then notices changes made with the controls on the QML side, and offers to apply or reset them.

To change settings you need setters and properties in `Config`, generated by `MUTATORS` and `GENERATE_PROPERTIES`.

Give the module a constant, read-only `Q_PROPERTY` for the configuration, so its QML can use it:

```cpp
// mykcm.h

#pragma once

#include <KQuickManagedConfigModule>

// The class generated from the .kcfg file
#include "my_config.h"

class MyKcm : public KQuickManagedConfigModule {
  Q_OBJECT

  Q_PROPERTY(My::Config *config READ config CONSTANT)

public:
  MyKcm(QObject *parent, const KPluginMetaData &data);

  My::Config *config() const;

private:
  My::Config *m_config;
};
```

Instead of registering a singleton, use [qmlRegisterAnonymousType()](https://doc.qt.io/qt-6/qqml-h.html#qmlRegisterAnonymousType) here:

```cpp
// mykcm.cpp

#include "mykcm.h"
#include "my_config.h"

// ...

K_PLUGIN_CLASS_WITH_JSON(MyKcm, "metadata.json")

MyKcm::MyKcm(QObject *parent, const KPluginMetaData &data)
    : KQuickManagedConfigModule(parent, data),
      m_config(new My::Config(this)) {
  // ...
  qmlRegisterAnonymousType<My::Config>("org.foo.mykcm.private", 1);
  // ...
}

My::Config *MyKcm::config() const { return m_config; }

#include "mykcm.moc"
```

Your QML then reaches all the settings through the `kcm` property of the module's page, which inherits [AbstractKCM](/docs/api/kcmutilsqml/qml-org-kde-kcmutils-abstractkcm):

```qml
import QtQuick.Controls as QQC2
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
  // ...
  QQC2.SpinBox {
    value: kcm.config.width
    onValueModified: kcm.config.width = value
  }
  // ...
}
```

[SettingStateBinding](/docs/api/kcmutilsqml/qml-org-kde-kcmutils-settingstatebinding) shows whether a setting is immutable or no longer has its default value:

```qml
import QtQuick.Controls as QQC2
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
    // ...
    QQC2.SpinBox {
        value: kcm.config.width
        onValueModified: kcm.config.width = value

        KCM.SettingStateBinding {
            configObject: kcm.config
            settingName: "width"
        }
    }
    // ...
}
```
