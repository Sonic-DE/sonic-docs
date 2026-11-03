---
title: "The KDE Configuration Compiler"
description: "Persistent platform-independent application settings."
---

# The KDE Configuration Compiler

Persistent platform-independent application settings.

kconfig\_compiler generates C++ source code from an XML file containing information about configuration options (.kcfg) and a file that provides the code generation options (.kcfgc) The generated class is based on [KConfigSkeleton](../kconfiggui/kconfigskeleton.md) and provides an API for the application to access its configuration data.

The generated C++ source code is output to a .h and a .cpp file, whose base name is the same as that of the .kcfgc file.

## The .kcfg XML file format: description of the configuration skeleton {#the-kcfg-xml-file-format-description-of-the-configuration-skeleton}

The structure of the .kcfg file is described by its DTD kcfg.xsd.

The \<kcfgfile\> tag may contain either the "name" attribute, which should be the name of the configuration file described, or the "arg" attribute, which, if set to "true", will allow you to pass the [KSharedConfig::Ptr](ksharedconfig.md#Ptr-typedef) object to use.

If neither "name" nor "arg" is set, the default configuration file ("\<appname\>rc") will be used.

The \<include\> tags are optional and may contain C++ header files that are needed to compile the code needed to compute default values. To generate a \#include "..." statement instead of \#include \<...\>, enclose the header file name in double quotes (e.g. \<include\>"header.h"\</include\>).

The remaining entries in the XML file are grouped by the tag \<group\> which describes the corresponding group in the configuration file.

The individual entries must have at least a name or a key. The key is used as the key in the config file, while the name is used to create accessor and modifier functions. If \<key\> is given, but not \<name\>, the name is constructed by removing all spaces from \<key\>. If \<name\> is given, but not \<key\>, the key is the same as \<name\>.

An entry must also have a type. The list of allowable types is specified in the DTD and loosely follows the list of types supported by the [QVariant](https://doc.qt.io/qt-6/qvariant.html) with exception of the clearly binary types (e.g. Pixmap, Image...) which are not supported. Besides those basic types the following special types are supported:

| Type | Description |
| --- | --- |
| Path | This is a string that is specially treated as a file-path. In particular paths in the home directory are prefixed with $HOME in when being stored in the configuration file. |
| Enum | This indicates an enumeration. The possible enum values and optional enum name should be provided via the \<choices\> tag. Enum values are accessed as integers by the application but stored as strings in the configuration file. This makes it possible to add more values at a later date without breaking compatibility. |
| IntList | This indicates a list of integers. This information is provided to the application as [QList](https://doc.qt.io/qt-6/qlist.html)\<int\>. Useful for storing QSplitter geometries. |
| Color | Isn't a special type but has special input. It is generated as QColor. Any valid input to QColor([QString](https://doc.qt.io/qt-6/qstring.html)) can be used (hex or SVG keyword notation) as well as a special format r,g,b,a where the a denotes the alpha channel and may be omitted. |

An entry can optionally have a default value which is used as default when the value isn't specified in any config file. Default values are interpreted as literal constant values. If a default value needs to be computed or if it needs to be obtained from a function call, the \<default\> tag should contain the code="true" attribute. The contents of the \<default\> tag is then considered to be a C++ expression. Note that in this case you might have to add an \<include\> tag as described above, or a SourceIncludeFiles entry in the .kcfgc file as described below, so that the code which computes the default value can be compiled.

Additional code for computing default values can be provided outside any entry definition via the \<code\> tag. The contents of the \<code\> tag is inserted as-is. A typical use for this is to compute a common default value which can then be referenced by multiple entries that follow.

## The .kcfgc file format: code generation options {#the-kcfgc-file-format-code-generation-options}

The options for generating the C++ sources are read from the file with the extension .kcfgc. To generate a class add the corresponding kcfgc file to the SOURCES line in the Makefile.am.

The following options are read from the kcfgc file:

| Option | Description | Default | Since |
| --- | --- | --- | --- |
| File=\<string\> | Name of kcfg file containing the options the class is generated for | \<programname\>.kcfg |   |
| HeaderExtension=\<string\> | Extension to use for the name of the generated C++ header files. | h | 5.57 |
| NameSpace=\<string\> | Optional namespace for generated class |   |   |
| ClassName=\<string\> | Name of generated class (required) |   |   |
| Inherits=\<string\> | Class the generated class inherits from. This class must inherit [KConfigSkeleton](../kconfiggui/kconfigskeleton.md) and must provide a default constructor (kcfgfile not specified), a constructor taking a [QString](https://doc.qt.io/qt-6/qstring.html) argument (kcfgfile with "name" attribute) and a constructor taking a [KSharedConfig::Ptr](ksharedconfig.md#Ptr-typedef) as argument (kcfgfile with "arg" attribute). Please refer to the documentation of [KConfigSkeleton](../kconfiggui/kconfigskeleton.md). | [KConfigSkeleton](../kconfiggui/kconfigskeleton.md) |   |
| Visibility=\<string\> | Inserts visibility directive (for example KDE\_EXPORT) between "class" keyword and class name in header file |   |   |
| Singleton=\<bool\> | Generated class is a singleton. | false |   |
| CustomAdditions=\<bool\> |   |   |   |
| MemberVariables=\<string\> | C++ access modifier used for member variables holding the configuration values Values: public, protected, private, dpointer | private |   |
| IncludeFiles=\<string\>, \<string\> ... | Names of files to be included in the header of the generated class. Enclose a file name in (escaped) double quotes to generate \#include "..." instead of \#include \<...\>. |   |   |
| SourceIncludeFiles=\<string\>, \<string\> ... | Names of files to be included in the source file of the generated class. Enclose a file name in (escaped) double quotes to generate \#include "..." instead of \#include \<...\>. |   |   |
| Mutators=\<value\> | Values: true, false or a comma separated list of options If true, mutator functions for all configuration options are generated. If false, no mutator functions are generated. If a list is provided, mutator functions are generated for the options that are listed. | false |   |
| Notifiers=\<value\> | Values: true, false or a comma separated list of options If true, entries will be written with the Notify flag enabled, so changes can be detected using [KConfigWatcher](kconfigwatcher.md). If a list is provided, the options that are listed are written with said flag. | false |   |
| DefaultValueGetters=\<value\> | Values: true, false or a comma separated list of options If true, functions to return the default value of all configuration options are generated. If false, no default value functions are generated. If a list is provided, default value functions are generated for the options that are listed. | false |   |
| ItemAccessors=\<bool\> | Generate accessor functions for the [KConfigSkeletonItem](kconfigskeletonitem.md) objects corresponding to the configuration options. If SetUserTexts is set, ItemAccessors also has to be set. | false |   |
| SetUserTexts=\<bool\> | Set the label and whatthis texts of the items from the kcfg file. If SetUserTexts is set, ItemAccessors also has to be set. | false |   |
| GlobalEnums=\<bool\> | If set to true all choices of Enum items will be created in the global scope of the generated class. If set to false, each Enum item whose enum is not explicitly named will get its own namespace for its choices. | false |   |
| UseEnumTypes=\<bool\> | If set to true, all Enum items whose enums are named will use enum types for the return value of accessor functions and for the parameter of mutator functions. This eliminates the need to cast accessor return values to the enum type if you want to use the enum type in your own code. If set to false, accessor return values and mutator parameters will be of type int. | false |   |
| ForceStringFilename=\<bool\> | If set to true, forces the first parameter of the generated class to be a [QString](https://doc.qt.io/qt-6/qstring.html) when using an argument for the filename. This is useful to specify at runtime the filename of the configuration class. | false |   |
| GenerateProperties=\<bool\> | If set to true, a [Q\_PROPERTY](https://doc.qt.io/qt-6/qobject.html#Q_PROPERTY) will be generated for each member variable holding a configuration value and the [Q\_OBJECT](https://doc.qt.io/qt-6/qobject.html#Q_OBJECT) macro will be added to the generated class. Note that you will also need to pass the GENERATE\_MOC option to the kconfig\_add\_kcfg\_files macro. | false |   |
| ParentInConstructor=\<bool\> | If set to true, the generated constructor will take an additional [QObject](https://doc.qt.io/qt-6/qobject.html)\* parameter that will be used as the object's parent. This is useful when working with KQuickAddons::ManagedConfigModule to set it as the parent of the generated class to allow automatic settings discovery and handle the deallocation. Note this parameter is incompatible with Singleton set to true. | false |   |
| TranslationSystem=\<string\> | Set the translation system for label, tooltip and whatsthis text in generated [KConfigSkeleton](../kconfiggui/kconfigskeleton.md). Set the value to kde to use the KDE Framework translation system, see KI18n. | qt |   |
| TranslationDomain=\<value\> | When TranslationSystem=kde is set, allow to specify the domain in which to look for translations. |   |   |
| QmlUncreatable=\<bool\> | If set to true the generated code will use the QML\_UNCREATABLE macro to register the type to QML. This shouldn't combined with Singleton, and can only be passed to C++ manually. | false | 6.11 |
| QmlRegistration=\<bool\> | If set to true the generated code will use the QML\_ELEMENT macro to register the type to QML. If Singleton is also true it will be registered as a QML singleton using QML\_SINGLETON | false | 6.4 |
| KConfigConstructor=\<bool\> | If set to true the generated code will have an alternative constructor directly from const std::unique\_ptr\<[KConfig](kconfig.md)\> instead of [KSharedConfigPtr](ksharedconfig.md#KSharedConfigPtr-typedef). | false | 6.23 |

## Advanced entry options {#advanced-entry-options}

There are several possibilities to parameterize entries.

### Parameterized entries {#parameterized-entries}

An entry can be parameterized using a fixed range parameter specified with the \<parameter\> tag. Such parameter can either be an Enum or an int. An Enum parameter should specify the possible enumeration values with the \<choices\> tag. An int parameter should specify its maximum value. Its minimum value is always 0.

A parameterized entry is expanded to a number of entries, one for each value in the parameter range. The name and key should contain a reference to the parameter in the form of $(parameter-name). When expanding the entries the $(parameter-name) part is replaced with the value of the parameter. In the case of an Enum parameter it is replaced with the name of the enumuration value. In the case of an int parameter it is replaced with the numeric value of the parameter.

Parameterized entries all share the same default value unless different default values have been specified for specific parameter values. This can be done with the param= attribute of the \<default\>. When a param attribute is specified the default value only applies to that particular parameter value.

Example 1:

```cpp
<entry name="Color$(ColorIndex)" type="Color" key="color_$(ColorIndex)">
  <parameter name="ColorIndex" type="Int" max="3"/>
  <default param="0">#ff0000</default>
  <default param="1">#00ff00</default>
  <default param="2">#0000ff</default>
  <default param="3">#ffff00</default>
</entry>
```

The above describes 4 color configuration entries with the following defaults:

```cpp
color_0=#ff0000
color_1=#00ff00
color_2=#0000ff
color_3=#ffff00
```

The configuration options will be accessible to the application via a QColor color(int ColorIndex) and a void setColor(int ColorIndex, const QColor &v) function.

Example 2:

```cpp
<entry name="Sound$(SoundEvent)" type="String" key="sound_$(SoundEvent)">
  <parameter name="SoundEvent" type="Enum">
    <values>
      <value>Explosion</value>
      <value>Crash</value>
      <value>Missile</value>
    </values>
  </parameter>
  <default param="Explosion">boom.wav</default>
  <default param="Crash">crash.wav</default>
  <default param="Missile">missile.wav</default>
</entry>
```

The above describes 3 string configuration entries with the following defaults:

```cpp
sound_Explosion=boom.wav
sound_Crash=crash.wav
sound_Missile=missile.wav
```

The configuration options will be accessible to the application via a [QString](https://doc.qt.io/qt-6/qstring.html) sound(int SoundEvent) and a void setSound(int SoundEvent, const [QString](https://doc.qt.io/qt-6/qstring.html) &v) function.

### Parameterized groups {#parameterized-groups}

A group name can be parametrized using a parameter given to the [KConfigSkeleton](../kconfiggui/kconfigskeleton.md) instance (which means this feature cannot be used with singleton classes).

Example 1:

```cpp
<kcfgfile name="testrc">
  <parameter name="groupname"/>
</kcfgfile>
<group name="$(groupname)">
  <entry key="Text" type="string">
  </entry>
</group>
```

In this case passing "Group2" as the 'groupname' parameter to the generated class will make it use group "Group2" for the entry "Text".

By setting the stateConfig attribute of kcfgfile to "true", [KSharedConfig::openStateConfig](ksharedconfig.md#openStateConfig) is used. This should be used when one stores volatile data, like window sizes or autocompletion texts. It is recommended to have at least two separate kcfg files for the different kinds of data.

> **Note:** This option is ignored when ForceStringFilename is set.

### Enums {#enums}

By default, if GlobalEnums is set to false, a separate named enum will be generated for each Enum entry. Since each enum is defined in a little enclosing class of its own, this allows the same Enum value names to be used in different enums. For example, the .kcfg entry

```cpp
<entry name="KeepData" type="Enum">
  <choices>
    <choice name="Do"/>
    <choice name="Dont" value="Don't"/>
  </choices>
</entry>
```

will generate this public class containing the enum definition, inside the generated class:

```cpp
class EnumKeepData
{
  public:
  enum type { Do, Dont, COUNT };
};
```

Since 5.68, if present the value attribute will be used as the choice value written to the backend instead of the name, allowing to write text incompatible with enum naming.

Alternatively, if GlobalEnums is set to true, all Enum items are defined as unnamed enums in the global scope of the generated class. In this case, all Enum values must have different names to avoid clashes. However, you can use a 'prefix' argument in \<choices\> to prevent duplicate enum member names clashing. Using this, the Enum value names are prefixed in code with the string you specify. For example, if GlobalEnums is set to true, the .kcfg entry

```cpp
<entry name="KeepData" type="Enum">
  <choices prefix="Keep_">
    <choice name="Do"/>
    <choice name="Dont" value="Don't"/>
  </choices>
</entry>
```

will generate config file entries of "KeepData=Do" and "KeepData=Dont", but the enum will be declared

```cpp
enum { Keep_Do, Keep_Dont };
```

It is possible to specify your own name for a generated enum, by including a 'name' parameter in \<choices\>. Just like unnamed enums, this enum will be defined in the global scope of the generated class (without any enclosing class of its own). Therefore the names of Enum values must be unique across both unnamed enums (if GlobalEnums is set to true) and all specifically named enums.

An example of a specifically named enum:

```cpp
<entry name="KeepData" type="Enum">
  <choices name="Types">
    <choice name="Do"/>
    <choice name="Dont"/>
  </choices>
</entry>
```

which results in the following enum declaration, inside the generated class:

```cpp
enum Types { Do, Dont };
```

It is also possible to specify the use of enums external to the generated class, by including the string "::" in the enum name - just ensure that it is sufficiently qualified to be unambiguous in use. To specify use of an unnamed enum, append a trailing "::". For example, to use the enum 'myEnum' defined in class ClassA, use either of

```cpp
<choices name="ClassA::myEnum">
<choices name="::ClassA::myEnum">
```

To specify an unnamed enum in namespace ProgSpace, use

```cpp
<choices name="ProgSpace::">
```

To specify a top-level unnamed enum, use

```cpp
<choices name="::">
```

To specify the top-level enum 'anotherEnum', use

```cpp
<choices name="::anotherEnum">
```

### Notify signals {#notify-signals}

An entry can emit a signal when it gets changed. First of all, you must define a list of signals for the configuration class. The signal's name may be any legal identifier you wish. The \<argument\> tag allows you to specify arguments for the emitted signal. It supports all types as defined in the KConfigXT DTD. The argument value must specify the name, without spaces, of one of the entries defined in the .kcfg file. A signal definition can also contain a \<label\> tag which will be the documentation line in the generated file.

```cpp
<signal name="emoticonSettingsChanged" />

<signal name="styleChanged">
  <label>Tell when a complete style change.</label>
  <argument type="String">stylePath</argument>
  <argument type="String">StyleCSSVariant</argument>
</signal>
```

After defining the signals, you must tell which signal to emit for the entry. A signal can be emitted by multiple entries. Also, you don't need to specify the arguments for a signal, the signal name will suffice.

```cpp
<entry key="stylePath" type="String">
  <label>Absolute path to a directory containing a Adium/Kopete chat window style.</label>
  <emit signal="styleChanged" />
</entry>
```

The signal will be emitted when save() is called.

> **Warning:** You must not call save() in direct response to any notify signal. If you need to call save(), use a QueuedConnection to listen to the notify signal.

You can also listen to the generic configChanged() signal from [KConfigSkeleton](../kconfiggui/kconfigskeleton.md) to notify your application about configuration changes. In that case you may also call save() in direct response.

Note that you will also need to pass the GENERATE\_MOC option to the kconfig\_add\_kcfg\_files macro.

### Translation context {#translation-context}

In the kcfg file you can specify the translation's context for \<tooltip\>, \<whatsthis\> and \<label\> element for an entry.

```cpp
<entry type="Bool" key="Auto Save">
  <label>Enable automatic saving of calendar</label>
  <whatsthis context="@info:whatsthis">Enable automatic saving of calendars to have calendars saved automatically.</whatsthis>
  <default>false</default>
</entry>
```

For more information on translation context and how to write good translatable text, please refer to [https://api.kde.org/frameworks/ki18n/html/prg\_guide.html](https://api.kde.org/frameworks/ki18n/html/prg_guide.html)
