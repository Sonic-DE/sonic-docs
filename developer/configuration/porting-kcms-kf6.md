---
title: Porting KCMs to KDE Frameworks 6
description: How settings modules (KCMs) written for KDE Frameworks 5 are ported to the KDE Frameworks 6 API that SonicDE ships.
source_url: https://develop.kde.org/docs/features/configuration/porting_kf6/
source_authors: [Alexander Lohnau, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-settings-utils (KCMUtils, KCMUtilsQuick, KCMUtilsCore, org.kde.kcmutils), sonic-frameworks-settings (KAuthorized, org.kde.config; authorizeControlModules() removed in 178fcc95)
---

# Porting KCMs to KDE Frameworks 6

Settings modules (KCMs) changed considerably between KDE Frameworks 5 and 6. SonicDE ships the KDE Frameworks 6 API only, so a module written for KF5 must be ported as described here.

### Build system and class names

In KF5, the code for QML modules was in KDeclarative and the code for QtWidgets modules in KConfigWidgets. In KF6, all of it is in KCMUtils (in SonicDE, `sonic-frameworks-settings-utils`):

- `KCModule` (QtWidgets modules) is in the `KF6::KCMUtils` library.
- `KQuickConfigModule` and `KQuickManagedConfigModule` (QML modules) are in `KF6::KCMUtilsQuick`.
- `KCModuleData` is in `KF6::KCMUtilsCore`, which both of the other libraries link publicly.

Since the QML classes are no longer in KDeclarative, the `KQuickAddons` namespace no longer fits: `KDeclarative::ConfigModule` is now `KQuickConfigModule`, and `KQuickAddons::ManagedConfigModule` is now `KQuickManagedConfigModule`.

### Class hierarchy

In KF5, the APIs of QML and QtWidgets modules were very different, which was a burden when working with both. In KF6, `KAbstractConfigModule` holds all the API that doesn't depend on the user interface technology. Most of it was taken from the QML classes, which are more widely used and have the cleaner API.

### KQuickConfigModule and KQuickManagedConfigModule

Removed, for lack of use: the `QQmlComponent::Status` getter, `showPassiveNotification()` and `passiveNotificationRequested()`, the attached `quickHelp` property (it isn't used when modules are shown), and setting a `rootOnlyMessage`.

QML files are no longer installed with KPackage, but bundled into the plugin as Qt resources, so the plugin contains everything it needs; this makes testing and installing simpler. Put all QML files in a folder called `ui`. `kcmutils_add_qml_kcm(my_kcm)` creates the plugin target and bundles the files of the `ui` folder.

The function also installs the plugin in the `plasma/kcms/systemsettings` namespace; change it with `INSTALL_NAMESPACE`. List source files with the optional `SOURCES` argument. The arguments work like those of `kcoreaddons_add_plugin()`.

It also generates a desktop file for the module, needed for example to pin the module to the task manager. If you don't need it, turn it off with `DISABLE_DESKTOP_FILE_GENERATION`.

This example uses every argument; usually the target name alone is enough:

```cmake
kcmutils_add_qml_kcm(my_kcm DISABLE_DESKTOP_FILE_GENERATION SOURCES kcm.cpp INSTALL_NAMESPACE plasma/kcms/kinfocenter)
target_link_libraries(my_kcm ...)
```

#### QML modules

KDeclarative's `org.kde.kcm` QML module moved to KCMUtils as `org.kde.kcmutils`. All its types have version 1.0. For consistency, `KPluginSelector` and `KPluginDelegate` were renamed to [PluginSelector](/docs/api/kcmutilsqml/qml-org-kde-kcmutils-pluginselector) and [PluginDelegate](/docs/api/kcmutilsqml/qml-org-kde-kcmutils-plugindelegate). Import it under a name, for example `import org.kde.kcmutils as KCMUtils`.

The `KCMShell` type of `org.kde.kquickcontrolsaddons` moved into the same module as [KCMLauncher](/docs/api/kcmutilsqml/qml-org-kde-kcmutils-kcmlauncher). Its `open()`, `openSystemSettings()` and `openInfoCenter()` methods are unchanged.

To check whether a module may be shown, use `KAuthorized` from the `org.kde.config` QML module:

```qml
import org.kde.config

function launchClockSettings() {
    if (KAuthorized.authorizeControlModule("kcm_clock")) {
        // Launch the KCM or do other logic
    }
}
```

`KAuthorized.authorizeControlModules()`, which filtered a list of modules, has been removed; call `authorizeControlModule()` for each module instead.

### KCModule

Because of the new class hierarchy, `KCModule` is no longer a QWidget. Call `widget()` to get its widget, for example where you need a parent widget. And since it isn't a QWidget, [KPluginFactory](/docs/api/kcoreaddons/kpluginfactory) passes a `QObject *` parent instead of a `QWidget *`; it is cast to a QWidget internally, but the constructor should take a `QObject *`.

The API using [KAboutData](/docs/api/kcoreaddons/kaboutdata) was removed: metadata comes from [KPluginMetaData](/docs/api/kcoreaddons/kpluginmetadata). Take a `const KPluginMetaData &data` argument in the constructor and pass it to `KCModule`. For plugins embedded in, for example, a [KPluginWidget](/docs/api/kcmutils/kpluginwidget), you can leave it out.

`setAuthAction()` and `authAction()` were removed: create the `KAuth::Action` yourself and execute it where needed. To say that saving needs administrator privileges, set the action's name with `setAuthActionName()`; `authActionName()` returns it, and `needsAuthorization()` is then true.

Instead of the signal `changed(bool hasChanged)`, call `setNeedsSave(bool needsSave)`; for connections use the slot `markAsChanged()`. Instead of the signal `defaulted(bool state)`, call `setRepresentsDefaults(bool defaults)`.

#### Compatibility API in KDE Frameworks 5.105

KDE Frameworks 5.105 (KConfigWidgets) added compatibility API to ease the transition: `QWidget *widget()`, `void setNeedsSave(bool needsSave)` and the constructor `KCModule(QObject *parent, const KPluginMetaData &data = {}, const QVariantList &args = QVariantList())`. With them, a module can be ported step by step while still building against KF5.

### Other KCMUtils API

`KCModuleProxy` was removed. Instead, get a `KCModule` from `KCModuleLoader::loadModule()` and embed its `widget()`. If your application already has a `QQmlEngine`, or needs one elsewhere, pass it to `loadModule()` for loading QML-based modules.

To load `KQuickConfigModule` and `KQuickManagedConfigModule` modules directly, use [KQuickConfigModuleLoader](/docs/api/kcmutilsquick/kquickconfigmoduleloader), with the `QQmlEngine` argument as for `KCModuleLoader`.
