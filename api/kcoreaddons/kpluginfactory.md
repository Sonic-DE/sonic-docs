---
title: "KPluginFactory Class"
description: "KPluginFactory provides a convenient way to provide factory-style plugins."
---

# KPluginFactory Class

[KPluginFactory](kpluginfactory.md) provides a convenient way to provide factory-style plugins. [More...](#details)

- **Header:** `#include <KPluginFactory>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kpluginfactory-members.md)

## Public Types

- [enum KPluginFactory::ResultErrorReason](#ResultErrorReason-enum)

## Public Functions

- [KPluginFactory()](#KPluginFactory)
- [template \<typename T\> T \*create(QObject \*parent = nullptr, const QVariantList &args = {})](#create)
- [template \<typename T\> T \*create(QWidget \*parentWidget, QObject \*parent, const QVariantList &args = {})](#create-1)
- [KPluginMetaData metaData() const](#metaData)
- [void setMetaData(const KPluginMetaData &metaData)](#setMetaData)

## Static Public Members

- [template \<typename T\> KPluginFactory::Result\<T\> instantiatePlugin(const KPluginMetaData &data, QObject \*parent = nullptr, const QVariantList &args = {})](#instantiatePlugin)
- [KPluginFactory::Result\<KPluginFactory\> loadFactory(const KPluginMetaData &data)](#loadFactory)

## Protected Functions

- [QObject \*create(const char \*iface, QWidget \*parentWidget, QObject \*parent, const QVariantList &args)](#create-2)
- [template \<typename T, std::enable\_if\_t\<InheritanceChecker\<T\>::enabled, int\> = 0\> void registerPlugin()](#registerPlugin)
- [template \<typename T, std::enable\_if\_t\<InheritanceWithMetaDataChecker\<T\>::enabled, int\> = 0\> void registerPlugin()](#registerPlugin-1)
- [template \<typename T\> void registerPlugin(KPluginFactory::CreateInstanceWithMetaDataFunction instanceFunction)](#registerPlugin-2)

## Detailed Description {#details}

Qt plugins provide a singleton object, but a common pattern is for plugins to generate as many objects of a particular type as the application requires. By using [KPluginFactory](kpluginfactory.md), you can avoid implementing the factory pattern yourself.

[KPluginFactory](kpluginfactory.md) also allows plugins to provide multiple different object types, indexed by keywords.

The objects created by [KPluginFactory](kpluginfactory.md) must inherit [QObject](https://doc.qt.io/qt-6/qobject.html), and must have a standard constructor pattern:

- if the object is a KPart::Part, it must be of the form
   
   ```cpp
   T(QWidget *parentWidget, QObject *parent, const QVariantList &args)
   ```
   
   or
   
   ```cpp
   T(QWidget *parentWidget, QObject *parent, const KPluginMetaData &metaData, const QVariantList &args)
   ```
- if it is a QWidget, it must be of the form
   
   ```cpp
   T(QWidget *parent, const QVariantList &args)
   ```
   
   or
   
   ```cpp
   T(QWidget *parent, const KPluginMetaData &metaData, const QVariantList &args)
   ```
- otherwise it must be of the form
   
   ```cpp
   T(QObject *parent, const QVariantList &args)
   ```
   
   or
   
   ```cpp
   T(QObject *parent, const KPluginMetaData &metaData, const QVariantList &args)
   ```

You should typically use either [K\_PLUGIN\_CLASS](kpluginfactory.md#K_PLUGIN_CLASS)() or [K\_PLUGIN\_CLASS\_WITH\_JSON](kpluginfactory.md#K_PLUGIN_CLASS_WITH_JSON)() in your plugin code to generate a factory. The typical pattern is:

```cpp
#include <KPluginFactory>
#include <plugininterface.h>

class MyPlugin : public PluginInterface
{
public:
    MyPlugin(QObject *parent, const QVariantList &args)
        : PluginInterface(parent)
    {}
};

K_PLUGIN_CLASS(MyPlugin)
#include <myplugin.moc>
```

If you want to write a custom [KPluginFactory](kpluginfactory.md) not using the standard macro(s) you can reimplement the create(const char \*iface, QWidget \*parentWidget, [QObject](https://doc.qt.io/qt-6/qobject.html) \*parent, const [QVariantList](https://doc.qt.io/qt-6/qvariant.html#QVariantList-typedef) &args) method.

Example:

```cpp
class SomeScriptLanguageFactory : public KPluginFactory
{
    Q_OBJECT
public:
    SomeScriptLanguageFactory()
    {}

protected:
    virtual QObject *create(const char *iface, QWidget *parentWidget, QObject *parent, const QVariantList &args)
    {
        // Create an identifier based on the iface and given pluginId
        const QString identifier = QLatin1String(iface) + QLatin1Char('_') + metaData().pluginId();
        // load scripting language module from the information in identifier and return it:
        return object;
    }
};
```

To load the [KPluginFactory](kpluginfactory.md) from an installed plugin you can use [loadFactory](kpluginfactory.md#loadFactory)() and for directly creating a plugin instance from it [instantiatePlugin](kpluginfactory.md#instantiatePlugin)()

## Member Type Documentation {#member-type-documentation}

### enum KPluginFactory::ResultErrorReason {#ResultErrorReason-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KPluginFactory::NO_PLUGIN_ERROR` | `0` | No error |
| `KPluginFactory::INVALID_PLUGIN` | `1` | The plugin could not be loaded |
| `KPluginFactory::INVALID_FACTORY` | `2` | The factory object could not be loaded |
| `KPluginFactory::INVALID_KPLUGINFACTORY_INSTANTIATION` | `3` | The target object could not be instantiated |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPluginFactory::KPluginFactory() {#KPluginFactory}

### template \<typename T\> T \*KPluginFactory::create(QObject \**parent* = nullptr, const QVariantList &*args* = {}) {#create}

Use this method to create an object.

It will try to create an object which inherits T.

If it has multiple choices it's not defined which object will be returned, so be careful to request a unique interface or use keywords.

T the interface for which an object should be created. The object will inherit T.

`parent` the parent of the object. If `parent` is a widget type, it will also passed to the parentWidget argument of the CreateInstanceFunction for the object.

`args` additional arguments which will be passed to the object.

Returns a pointer to the created object is returned, or `nullptr` if an error occurred.

### template \<typename T\> T \*KPluginFactory::create(QWidget \**parentWidget*, QObject \**parent*, const QVariantList &*args* = {}) {#create-1}

Use this method to create an object. It will try to create an object which inherits T This overload has an additional `parentWidget` argument, which is used by some plugins (e.g. Parts).

T the interface for which an object should be created. The object will inherit T.

`parentWidget` an additional parent widget.

`parent` the parent of the object. If `parent` is a widget type, it will also passed to the parentWidget argument of the CreateInstanceFunction for the object.

`args` additional arguments which will be passed to the object. Since 5.93 this has a default arg. Returns a pointer to the created object is returned, or `nullptr` if an error occurred.

### \[virtual protected\] QObject \*KPluginFactory::create(const char \**iface*, QWidget \**parentWidget*, QObject \**parent*, const QVariantList &*args*) {#create-2}

This function is called when the factory asked to create an Object.

You may reimplement it to provide a very flexible factory. This is especially useful to provide generic factories for plugins implemented using a scripting language.

`iface` the staticMetaObject::className() string identifying the plugin interface that was requested. E.g. for KCModule plugins this string will be "KCModule".

`parentWidget` only used if the requested plugin is a KPart.

`parent` the parent object for the plugin object.

`args` a plugin specific list of arbitrary arguments.

### \[static\] template \<typename T\> KPluginFactory::Result\<T\> KPluginFactory::instantiatePlugin(const KPluginMetaData &*data*, QObject \**parent* = nullptr, const QVariantList &*args* = {}) {#instantiatePlugin}

Attempts to load the [KPluginFactory](kpluginfactory.md) and create a T instance from the given metadata.

[KCoreAddons](kcoreaddons-module.md) will log error messages automatically, meaning you only need to implement your own logging in case you want to give it more context info or have a custom category.

```cpp
if (auto result = KPluginFactory::instantiatePlugin<MyClass>(metaData, parent, args)) {
    // The plugin is valid and result.plugin contains the object
} else {
    // We can access the error related properties, but result.plugin is a nullptr
    qCWarning(MYCATEGORY) << result.errorString;
}
```

If there is no extra error handling needed the plugin can be directly accessed and checked if it is a nullptr

```cpp
if (auto plugin = KPluginFactory::instantiatePlugin<MyClass>(metaData, parent, args).plugin) {
}
```

`data` [KPluginMetaData](kpluginmetadata.md) from which the plugin should be loaded

`args` arguments which get passed to the plugin's constructor

Returns a Result object which contains the plugin instance and potentially error information

### \[static\] KPluginFactory::Result\<KPluginFactory\> KPluginFactory::loadFactory(const KPluginMetaData &*data*) {#loadFactory}

Attempts to load the [KPluginFactory](kpluginfactory.md) from the given metadata.

The errors will be logged using the kf.coreaddons debug category.

`data` [KPluginMetaData](kpluginmetadata.md) from which the plugin should be loaded

Returns a result object which contains the plugin instance and potentially error information

### KPluginMetaData KPluginFactory::metaData() const {#metaData}

Returns the metadata of the plugin

*See also* [setMetaData](kpluginfactory.md#setMetaData)()

### \[protected\] template \<typename T, std::enable\_if\_t\<InheritanceChecker\<T\>::enabled, int\> = 0\> void KPluginFactory::registerPlugin() {#registerPlugin}

Uses a default instance creation function depending on the type of interface. If the interface inherits from `KParts::Part` the function will call

```cpp
new T(QWidget *parentWidget, QObject *parent, const QVariantList &args)
```

`QWidget` the function will call

```cpp
new T(QWidget *parent, const QVariantList &args)
```

else the function will call

```cpp
new T(QObject *parent, const QVariantList &args)
```

If those constructor methods are not callable this overload is not available.

### \[protected\] template \<typename T, std::enable\_if\_t\<InheritanceWithMetaDataChecker\<T\>::enabled, int\> = 0\> void KPluginFactory::registerPlugin() {#registerPlugin-1}

Uses a default instance creation function depending on the type of interface. If the interface inherits from `KParts::Part` the function will call

```cpp
new T(QWidget *parentWidget, QObject *parent, const KPluginMetaData &metaData, const QVariantList &args)
```

`QWidget` the function will call

```cpp
new T(QWidget *parent, const KPluginMetaData &metaData, const QVariantList &args)
```

else the function will call

```cpp
new T(QObject *parent, const KPluginMetaData &metaData, const QVariantList &args)
```

If those constructor methods are not callable this overload is not available.

### \[protected\] template \<typename T\> void KPluginFactory::registerPlugin(KPluginFactory::CreateInstanceWithMetaDataFunction *instanceFunction*) {#registerPlugin-2}

Registers a plugin with the factory. Call this function from the constructor of the [KPluginFactory](kpluginfactory.md) subclass to make the create function able to instantiate the plugin when asked for an interface the plugin implements.

`T` the name of the plugin class

`instanceFunction` A function pointer to a function that creates an instance of the plugin.

### void KPluginFactory::setMetaData(const KPluginMetaData &*metaData*) {#setMetaData}

Set the metadata about the plugin this factory generates.

`metaData` the metadata about the plugin

*See also* [metaData](kpluginfactory.md#metaData)()

## Macro Documentation {#macro-documentation}

### K\_PLUGIN\_CLASS {#K_PLUGIN_CLASS}

Creates a [KPluginFactory](kpluginfactory.md) subclass and exports it as the root plugin object. Unlike [K\_PLUGIN\_CLASS\_WITH\_JSON](kpluginfactory.md#K_PLUGIN_CLASS_WITH_JSON), this macro does not require json meta data.

This macro does the same as [K\_PLUGIN\_FACTORY](kpluginfactory.md#K_PLUGIN_FACTORY), but you only have to pass the class name. The factory name and [registerPlugin](kpluginfactory.md#registerPlugin) call are deduced from the class name. This is also useful if you want to use static plugins, see the kcoreaddons\_add\_plugin CMake method.

### K\_PLUGIN\_CLASS\_WITH\_JSON {#K_PLUGIN_CLASS_WITH_JSON}

Create a [KPluginFactory](kpluginfactory.md) subclass and export it as the root plugin object with JSON metadata.

This macro does the same as [K\_PLUGIN\_FACTORY\_WITH\_JSON](kpluginfactory.md#K_PLUGIN_FACTORY_WITH_JSON), but you only have to pass the class name and the json file. The factory name and [registerPlugin](kpluginfactory.md#registerPlugin) call are deduced from the class name.

```cpp
#include <myplugin.moc>
```

in the same source file when that one has the name "myplugin.cpp".

Example:

```cpp
#include <KPluginFactory>
#include <plugininterface.h>

class MyPlugin : public PluginInterface
{
public:
    MyPlugin(QObject *parent, const KPluginMetaData &metaData, const QVariantList &args)
        : PluginInterface(parent)
    {}
};

K_PLUGIN_CLASS_WITH_JSON(MyPlugin, "metadata.json")

#include <myplugin.moc>
```

*See also* [K\_PLUGIN\_FACTORY\_WITH\_JSON](kpluginfactory.md#K_PLUGIN_FACTORY_WITH_JSON)

### K\_PLUGIN\_FACTORY {#K_PLUGIN_FACTORY}

Create a [KPluginFactory](kpluginfactory.md) subclass and export it as the root plugin object.

`name` the name of the [KPluginFactory](kpluginfactory.md) derived class.

`pluginRegistrations` code to be inserted into the constructor of the class. Usually a series of [registerPlugin](kpluginfactory.md#registerPlugin)() calls.

> **Note:** K\_PLUGIN\_FACTORY declares the subclass including a [Q\_OBJECT](https://doc.qt.io/qt-6/qobject.html#Q_OBJECT) macro. So you need to make sure to have Qt's moc run also for the source file where you use the macro. E.g. in projects using CMake and it's automoc feature, as usual you need to have a line

```cpp
#include <myplugin.moc>
```

in the same source file when that one has the name "myplugin.cpp".

Example:

```cpp
#include <KPluginFactory>
#include <plugininterface.h>

class MyPlugin : public PluginInterface
{
public:
    MyPlugin(QObject *parent, const QVariantList &args)
        : PluginInterface(parent)
    {}
};

K_PLUGIN_FACTORY(MyPluginFactory, registerPlugin<MyPlugin>();)

#include <myplugin.moc>
```

If you want to compile a .json file into the plugin, use [K\_PLUGIN\_FACTORY\_WITH\_JSON](kpluginfactory.md#K_PLUGIN_FACTORY_WITH_JSON).

*See also* [K\_PLUGIN\_FACTORY\_WITH\_JSON](kpluginfactory.md#K_PLUGIN_FACTORY_WITH_JSON)

### K\_PLUGIN\_FACTORY\_WITH\_JSON {#K_PLUGIN_FACTORY_WITH_JSON}

Create a [KPluginFactory](kpluginfactory.md) subclass and export it as the root plugin object with JSON metadata.

This macro does the same as [K\_PLUGIN\_FACTORY](kpluginfactory.md#K_PLUGIN_FACTORY), but adds a JSON file as plugin metadata. See [Q\_PLUGIN\_METADATA](https://doc.qt.io/qt-6/qtplugin.html#Q_PLUGIN_METADATA)() for more information.

`name` the name of the [KPluginFactory](kpluginfactory.md) derived class.

`pluginRegistrations` code to be inserted into the constructor of the class. Usually a series of [registerPlugin](kpluginfactory.md#registerPlugin)() calls.

`jsonFile` name of the JSON file to be compiled into the plugin as metadata

> **Note:** K\_PLUGIN\_FACTORY\_WITH\_JSON declares the subclass including a [Q\_OBJECT](https://doc.qt.io/qt-6/qobject.html#Q_OBJECT) macro. So you need to make sure to have Qt's moc run also for the source file where you use the macro. E.g. in projects using CMake and its automoc feature, as usual you need to have a line

```cpp
#include <myplugin.moc>
```

in the same source file when that one has the name "myplugin.cpp".

Example:

```cpp
#include <KPluginFactory>
#include <plugininterface.h>

class MyPlugin : public PluginInterface
{
public:
    MyPlugin(QObject *parent, const KPluginMetaData &metaData, const QVariantList &args)
        : PluginInterface(parent)
    {}
};

K_PLUGIN_FACTORY_WITH_JSON(MyPluginFactory,
                 "metadata.json",
                 registerPlugin<MyPlugin>();
                )

#include <myplugin.moc>
```

*See also* [K\_PLUGIN\_FACTORY](kpluginfactory.md#K_PLUGIN_FACTORY)
