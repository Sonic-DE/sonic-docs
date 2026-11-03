---
title: "KAboutData Class"
description: "This class is used to store information about a program or plugin."
---

# KAboutData Class

This class is used to store information about a program or plugin. [More...](#details)

- **Header:** `#include <KAboutData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kaboutdata-members.md)

## Public Types

- [\[since 6.29\] enum KAboutData::UrlType](#UrlType-enum)

## Properties

- [\[read-only\] authors : const QList\<KAboutPerson\>](#authors-prop)
- [\[read-only\] bugAddress : const QString](#bugAddress-prop)
- [\[read-only\] componentName : const QString](#componentName-prop)
- [\[read-only\] components : const QList\<KAboutComponent\>](#components-prop)
- [\[read-only\] copyrightStatement : const QString](#copyrightStatement-prop)
- [\[read-only\] credits : const QList\<KAboutPerson\>](#credits-prop)
- [\[read-only\] desktopFileName : const QString](#desktopFileName-prop)
- [\[read-only\] displayName : const QString](#displayName-prop)
- [\[read-only\] homepage : const QString](#homepage-prop)
- [\[read-only\] licenses : const QList\<KAboutLicense\>](#licenses-prop)
- [\[read-only\] otherText : const QString](#otherText-prop)
- [\[read-only\] productName : const QString](#productName-prop)
- [\[read-only\] programLogo : const QVariant](#programLogo-prop)
- [\[read-only\] releases : QList\<KAboutRelease\>](#releases-prop)
- [\[read-only\] shortDescription : const QString](#shortDescription-prop)
- [\[read-only\] translators : const QList\<KAboutPerson\>](#translators-prop)
- [\[read-only\] version : const QString](#version-prop)

## Public Functions

- [KAboutData(const QString &componentName = {}, const QString &displayName = {}, const QString &version = {})](#KAboutData-1)
- [KAboutData(const QString &componentName, const QString &displayName, const QString &version, const QString &shortDescription, enum KAboutLicense::LicenseKey licenseType, const QString &copyrightStatement = QString(), const QString &otherText = QString(), const QString &homePageAddress = QString(), const QString &bugAddress = QStringLiteral("submit@bugs.kde.org"))](#KAboutData-2)
- [KAboutData(const KAboutData &other)](#KAboutData)
- [KAboutData &addAuthor(const KAboutPerson &author)](#addAuthor) (since 6.9)
- [KAboutData &addAuthor(const QString &name, const QString &task = QString(), const QString &emailAddress = QString(), const QString &webAddress = QString(), const QUrl &avatarUrl = QUrl())](#addAuthor-1)
- [KAboutData &addAuthor(const QString &name, const QString &task, const QString &emailAddress, const QString &webAddress, const QString &kdeStoreUsername)](#addAuthor-2) (since 6.0)
- [KAboutData &addComponent(const KAboutComponent &component)](#addComponent) (since 6.9)
- [KAboutData &addComponent(const QString &name, const QString &description = QString(), const QString &version = QString(), const QString &webAddress = QString(), KAboutLicense::LicenseKey licenseKey = KAboutLicense::Unknown)](#addComponent-1)
- [KAboutData &addComponent(const QString &name, const QString &description, const QString &version, const QString &webAddress, const QString &pathToLicenseFile)](#addComponent-2)
- [KAboutData &addCredit(const KAboutPerson &person)](#addCredit) (since 6.9)
- [KAboutData &addCredit(const QString &name, const QString &task = QString(), const QString &emailAddress = QString(), const QString &webAddress = QString(), const QUrl &avatarUrl = QUrl())](#addCredit-1)
- [KAboutData &addCredit(const QString &name, const QString &task, const QString &emailAddress, const QString &webAddress, const QString &kdeStoreUsername)](#addCredit-2) (since 6.0)
- [KAboutData &addLicense(KAboutLicense &&license)](#addLicense) (since 6.26)
- [KAboutData &addLicense(KAboutLicense::LicenseKey licenseKey)](#addLicense-1)
- [KAboutData &addLicense(KAboutLicense::LicenseKey licenseKey, KAboutLicense::VersionRestriction versionRestriction)](#addLicense-2)
- [KAboutData &addLicenseText(const QString &license)](#addLicenseText)
- [KAboutData &addLicenseTextFile(const QString &file)](#addLicenseTextFile)
- [KAboutData &addRelease(KAboutRelease &&release)](#addRelease) (since 6.26)
- [QList\<KAboutPerson\> authors() const](#authors)
- [QString bugAddress() const](#bugAddress)
- [QString componentName() const](#componentName)
- [QList\<KAboutComponent\> components() const](#components)
- [QString copyrightStatement() const](#copyrightStatement)
- [QList\<KAboutPerson\> credits() const](#credits)
- [QString customAuthorPlainText() const](#customAuthorPlainText)
- [QString customAuthorRichText() const](#customAuthorRichText)
- [bool customAuthorTextEnabled() const](#customAuthorTextEnabled)
- [QString desktopFileName() const](#desktopFileName)
- [QString displayName() const](#displayName)
- [QString homepage() const](#homepage)
- [QList\<KAboutLicense\> licenses() const](#licenses)
- [QString organizationDomain() const](#organizationDomain)
- [QString otherText() const](#otherText)
- [void processCommandLine(QCommandLineParser \*parser)](#processCommandLine)
- [QString productName() const](#productName)
- [QVariant programLogo() const](#programLogo)
- [QList\<KAboutRelease\> releases() const](#releases) (since 6.26)
- [KAboutData &setBugAddress(const QByteArray &bugAddress)](#setBugAddress)
- [KAboutData &setComponentName(const QString &componentName)](#setComponentName)
- [KAboutData &setCopyrightStatement(const QString &copyrightStatement)](#setCopyrightStatement)
- [KAboutData &setCustomAuthorText(const QString &plainText, const QString &richText)](#setCustomAuthorText)
- [KAboutData &setDesktopFileName(const QString &desktopFileName)](#setDesktopFileName)
- [KAboutData &setDisplayName(const QString &displayName)](#setDisplayName)
- [KAboutData &setHomepage(const QString &homepage)](#setHomepage)
- [KAboutData &setLicense(KAboutLicense &&license)](#setLicense) (since 6.26)
- [KAboutData &setLicense(KAboutLicense::LicenseKey licenseKey)](#setLicense-1)
- [KAboutData &setLicense(KAboutLicense::LicenseKey licenseKey, KAboutLicense::VersionRestriction versionRestriction)](#setLicense-2)
- [KAboutData &setLicenseText(const QString &license)](#setLicenseText)
- [KAboutData &setLicenseTextFile(const QString &file)](#setLicenseTextFile)
- [KAboutData &setOrganizationDomain(const QByteArray &domain)](#setOrganizationDomain)
- [KAboutData &setOtherText(const QString &otherText)](#setOtherText)
- [KAboutData &setProductName(const QByteArray &name)](#setProductName)
- [KAboutData &setProgramLogo(const QVariant &image)](#setProgramLogo)
- [KAboutData &setShortDescription(const QString &shortDescription)](#setShortDescription)
- [KAboutData &setTranslator(const QString &name, const QString &emailAddress)](#setTranslator)
- [KAboutData &setUrl(KAboutData::UrlType type, const QString &url)](#setUrl) (since 6.29)
- [KAboutData &setVersion(const QByteArray &version)](#setVersion)
- [bool setupCommandLine(QCommandLineParser \*parser)](#setupCommandLine)
- [QString shortDescription() const](#shortDescription)
- [QList\<KAboutPerson\> translators() const](#translators)
- [KAboutData &unsetCustomAuthorText()](#unsetCustomAuthorText)
- [QString url(KAboutData::UrlType type) const](#url) (since 6.29)
- [QString version() const](#version)

## Static Public Members

- [QString aboutTranslationTeam()](#aboutTranslationTeam)
- [KAboutData applicationData()](#applicationData)
- [KAboutData fromAppStreamFile(const QString &appStreamFileName)](#fromAppStreamFile) (since 6.26)
- [KAboutData fromAppStreamForApplication()](#fromAppStreamForApplication) (since 6.26)
- [KAboutData fromAppStreamId(const QString &applicationId)](#fromAppStreamId) (since 6.26)
- [void setApplicationData(const KAboutData &aboutData)](#setApplicationData)

## Detailed Description {#details}

It can store such values as version number, program name, home page, address for bug reporting, multiple authors and contributors (using [KAboutPerson](kaboutperson.md)), license and copyright information.

Currently, the values set here are shown by the "About" box (see KAboutApplicationDialog), used by the bug report dialog (see KBugReport), and by the help shown on command line (see [KAboutData::setupCommandLine](kaboutdata.md#setupCommandLine)()).

Porting Notes: Since KDE Frameworks 5.0, the translation catalog mechanism must be provided by your translation framework to load the correct catalog instead (eg: KLocalizedString::setApplicationDomain() for KI18n, or [QCoreApplication::installTranslator](https://doc.qt.io/qt-6/qcoreapplication.html#installTranslator)() for Qt's translation system). This applies to the old setCatalogName() and catalogName() members. But see also K4AboutData in kde4support as a compatibility class.

Example: Setting the metadata of an application using [KAboutData](kaboutdata.md) in code also relying on the KDE Framework modules KI18n and KDBusAddons:

```cpp
// create QApplication instance
QApplication app(argc, argv);
// setup translation string domain for the i18n calls
KLocalizedString::setApplicationDomain("foo");
// create a KAboutData object to use for setting the application metadata
KAboutData aboutData("foo", i18n("Foo"), "0.1",
                     i18n("To Foo or not To Foo"),
                     KAboutLicense::LGPL,
                     i18n("Copyright 2017 Bar Foundation"), QString(),
                     "https://www.foo-the-app.net");
// overwrite default-generated values of organizationDomain & desktopFileName
aboutData.setOrganizationDomain("barfoundation.org");
aboutData.setDesktopFileName("org.barfoundation.foo");

// set the application metadata
KAboutData::setApplicationData(aboutData);
// in GUI apps set the window icon manually, not covered by KAboutData
// needed for environments where the icon name is not extracted from
// the information in the application's desktop file
QApplication::setWindowIcon(QIcon::fromTheme(QStringLiteral("foo")));

// integrate with commandline argument handling
QCommandLineParser parser;
aboutData.setupCommandLine(&parser);
// setup of app specific commandline args
[...]
parser.process(app);
aboutData.processCommandLine(&parser);

// with the application metadata set, register to the D-Bus session
KDBusService programDBusService(KDBusService::Multiple | KDBusService::NoExitOnFailure);
```

## Member Type Documentation {#member-type-documentation}

### \[since 6.29\] enum KAboutData::UrlType {#UrlType-enum}

Types of URLs associated with application metadata.

This includes URL types defined in the AppStream specification as well as KDE extensions to that.

| Constant | Value | Description |
| --- | --- | --- |
| `KAboutData::Homepage` | `0` | The application homepage. |
| `KAboutData::Bugtracker` | `1` | The application's bug tracking system, for users to report issues. |
| `KAboutData::Faq` | `2` | A FAQ page for this application. |
| `KAboutData::Help` | `3` | User reference or documentation. |
| `KAboutData::Donation` | `4` | Information on how to donate to this project. |
| `KAboutData::Translate` | `5` | Page about how to contribute to translating the application. |
| `KAboutData::Contact` | `6` | Page with contact information of the vendor/developer. |
| `KAboutData::VCSBrowser` | `7` | Link to the Git forge or similar with the application source code. |
| `KAboutData::Contribute` | `8` | Information on how to contribute to this application. |
| `KAboutData::XKDEMatrixRoom` | `9` | Matrix room for this application (KDE::matrix AppStream extension). |
| `KAboutData::XKDEForum` | `10` | Web forum/forum section for this application (KDE::forum AppStream extension). |
| `KAboutData::XKDEMastodon` | `11` | Mastodon account about this applications (KDE::mastodon AppStream extension). |

This enum was introduced in Qt 6.29.

*See also* [https://www.freedesktop.org/software/appstream/docs/chap-Metadata.html#tag-url](https://www.freedesktop.org/software/appstream/docs/chap-Metadata.html#tag-url)

## Property Documentation {#property-documentation}

### \[read-only\] authors : const QList\<KAboutPerson\> {#authors-prop}

**Access functions:**

- `QList`\<`KAboutPerson`\> **[authors](kaboutdata.md#authors)**() const

### \[read-only\] bugAddress : const QString {#bugAddress-prop}

**Access functions:**

- `QString` **[bugAddress](kaboutdata.md#bugAddress)**() const

### \[read-only\] componentName : const QString {#componentName-prop}

**Access functions:**

- `QString` **[componentName](kaboutdata.md#componentName)**() const

### \[read-only\] components : const QList\<KAboutComponent\> {#components-prop}

**Access functions:**

- `QList`\<`KAboutComponent`\> **[components](kaboutdata.md#components)**() const

### \[read-only\] copyrightStatement : const QString {#copyrightStatement-prop}

**Access functions:**

- `QString` **[copyrightStatement](kaboutdata.md#copyrightStatement)**() const

### \[read-only\] credits : const QList\<KAboutPerson\> {#credits-prop}

**Access functions:**

- `QList`\<`KAboutPerson`\> **[credits](kaboutdata.md#credits)**() const

### \[read-only\] desktopFileName : const QString {#desktopFileName-prop}

**Access functions:**

- `QString` **[desktopFileName](kaboutdata.md#desktopFileName)**() const

### \[read-only\] displayName : const QString {#displayName-prop}

**Access functions:**

- `QString` **[displayName](kaboutdata.md#displayName)**() const

### \[read-only\] homepage : const QString {#homepage-prop}

**Access functions:**

- `QString` **[homepage](kaboutdata.md#homepage)**() const

### \[read-only\] licenses : const QList\<KAboutLicense\> {#licenses-prop}

**Access functions:**

- `QList`\<`KAboutLicense`\> **[licenses](kaboutdata.md#licenses)**() const

### \[read-only\] otherText : const QString {#otherText-prop}

**Access functions:**

- `QString` **[otherText](kaboutdata.md#otherText)**() const

### \[read-only\] productName : const QString {#productName-prop}

**Access functions:**

- `QString` **[productName](kaboutdata.md#productName)**() const

### \[read-only\] programLogo : const QVariant {#programLogo-prop}

**Access functions:**

- `QVariant` **[programLogo](kaboutdata.md#programLogo)**() const

### \[read-only\] releases : QList\<KAboutRelease\> {#releases-prop}

**Access functions:**

- `QList`\<`KAboutRelease`\> **[releases](kaboutdata.md#releases)**() const

### \[read-only\] shortDescription : const QString {#shortDescription-prop}

**Access functions:**

- `QString` **[shortDescription](kaboutdata.md#shortDescription)**() const

### \[read-only\] translators : const QList\<KAboutPerson\> {#translators-prop}

**Access functions:**

- `QList`\<`KAboutPerson`\> **[translators](kaboutdata.md#translators)**() const

### \[read-only\] version : const QString {#version-prop}

**Access functions:**

- `QString` **[version](kaboutdata.md#version)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAboutData::KAboutData(const QString &*componentName* = {}, const QString &*displayName* = {}, const QString &*version* = {}) {#KAboutData-1}

Constructor.

`componentName` The program name or plugin name used internally. Example: "kwrite".

`displayName` A displayable name for the program or plugin. This string should be translated. Example: i18n("KWrite")

`version` The component version string.

Sets the property [desktopFileName](kaboutdata.md#desktopFileName) to "org.kde."+[componentName](kaboutdata.md#componentName) and the property [organizationDomain](kaboutdata.md#organizationDomain) to "kde.org".

Default arguments since 5.53

*See also* [setOrganizationDomain](kaboutdata.md#setOrganizationDomain)(const QByteArray&), [setDesktopFileName](kaboutdata.md#setDesktopFileName)(const QString&)

### KAboutData::KAboutData(const QString &*componentName*, const QString &*displayName*, const QString &*version*, const QString &*shortDescription*, enum KAboutLicense::LicenseKey *licenseType*, const QString &*copyrightStatement* = QString(), const QString &*otherText* = QString(), const QString &*homePageAddress* = QString(), const QString &*bugAddress* = QStringLiteral("submit@bugs.kde.org")) {#KAboutData-2}

Constructor.

Porting Note: The `catalogName` parameter present in KDE4 was deprecated and removed. See also K4AboutData in kde4support if this feature is needed for compatibility purposes, or consider using [componentName](kaboutdata.md#componentName)() instead.

`componentName` The program name or plugin name used internally. Example: [QStringLiteral](https://doc.qt.io/qt-6/qstring.html#QStringLiteral)("kwrite"). This should never be translated.

`displayName` A displayable name for the program or plugin. This string should be translated. Example: i18n("KWrite")

`version` The component version string. Example: [QStringLiteral](https://doc.qt.io/qt-6/qstring.html#QStringLiteral)("1.0").

`shortDescription` A short description of what the component does. This string should be translated. Example: i18n("A simple text editor.")

`licenseType` The license identifier. Use [setLicenseText](kaboutdata.md#setLicenseText) or [setLicenseTextFile](kaboutdata.md#setLicenseTextFile) if you use a license not predefined here.

`copyrightStatement` A copyright statement, that can look like this: i18n("Copyright (C) 1999-2000 Name"). The string specified here is taken verbatim; the author information from [addAuthor](kaboutdata.md#addAuthor) is not used.

`otherText` Some free form text, that can contain any kind of information. The text can contain newlines. This string should be translated.

`homePageAddress` The URL to the component's homepage, including URL scheme. "http://some.domain" is correct, "some.domain" is not. Since KDE Frameworks 5.17, https and other valid URL schemes are also valid. See also the note below.

`bugAddress` The bug report address string, an email address or a URL. This defaults to the kde.org bug system.

> **Note:** The `homePageAddress` argument is used to derive a default organization domain for the application (which is used to register on the session D-Bus, locate the appropriate desktop file, etc.), by taking the host name and dropping the first component, unless there are less than three (e.g. "www.kde.org" -\> "kde.org"). Use both [setOrganizationDomain](kaboutdata.md#setOrganizationDomain)(const [QByteArray](https://doc.qt.io/qt-6/qbytearray.html)&) and [setDesktopFileName](kaboutdata.md#setDesktopFileName)() if their default values do not have proper values.

*See also* [setOrganizationDomain](kaboutdata.md#setOrganizationDomain)(const QByteArray&), [setDesktopFileName](kaboutdata.md#setDesktopFileName)(const QString&)

### KAboutData::KAboutData(const KAboutData &*other*) {#KAboutData}

Copy constructor. Performs a deep copy.

`other` object to copy

### \[static\] QString KAboutData::aboutTranslationTeam() {#aboutTranslationTeam}

Returns a message about the translation team.

### \[since 6.9\] KAboutData &KAboutData::addAuthor(const KAboutPerson &*author*) {#addAuthor}

Add an author.

You can call this function as many times as you need. Each entry is appended to a list.

`author` the author.

This function was introduced in Qt 6.9.

### KAboutData &KAboutData::addAuthor(const QString &*name*, const QString &*task* = QString(), const QString &*emailAddress* = QString(), const QString &*webAddress* = QString(), const QUrl &*avatarUrl* = QUrl()) {#addAuthor-1}

Defines an author.

You can call this function as many times as you need. Each entry is appended to a list. The person in the first entry is assumed to be the leader of the project.

`name` The developer's name. It should be translated.

`task` What the person is responsible for. This text can contain newlines. It should be translated. Can be left empty.

`emailAddress` An Email address where the person can be reached. Can be left empty.

`webAddress` The person's homepage or a relevant link. Start the address with "http://". "http://some.domain" is correct, "some.domain" is not. Can be left empty.

`avatarUrl` URL to the avatar of the person

### \[since 6.0\] KAboutData &KAboutData::addAuthor(const QString &*name*, const QString &*task*, const QString &*emailAddress*, const QString &*webAddress*, const QString &*kdeStoreUsername*) {#addAuthor-2}

This is an overloaded function.

This function was introduced in Qt 6.0.

### \[since 6.9\] KAboutData &KAboutData::addComponent(const KAboutComponent &*component*) {#addComponent}

Add a component that is used by the application.

You can call this function as many times as you need. Each entry is appended to a list.

`component` The component

This function was introduced in Qt 6.9.

### KAboutData &KAboutData::addComponent(const QString &*name*, const QString &*description* = QString(), const QString &*version* = QString(), const QString &*webAddress* = QString(), KAboutLicense::LicenseKey *licenseKey* = KAboutLicense::Unknown) {#addComponent-1}

Defines a component that is used by the application.

You can call this function as many times as you need. Each entry is appended to a list.

`name` The component's name. It should be translated.

`description` Short description of the component and maybe copyright info. This text can contain newlines. It should be translated. Can be left empty.

`version` The version of the component. Can be left empty.

`webAddress` The component's homepage or a relevant link. Start the address with "http://". "http://some.domain" is correct, "some.domain" is not. Can be left empty.

`licenseKey` The component's license identifier. Can be left empty (i.e. [KAboutLicense::Unknown](kaboutlicense.md#LicenseKey-enum))

### KAboutData &KAboutData::addComponent(const QString &*name*, const QString &*description*, const QString &*version*, const QString &*webAddress*, const QString &*pathToLicenseFile*) {#addComponent-2}

Defines a component that is used by the application with a custom license text file.

You can call this function as many times as you need. Each entry is appended to a list.

`name` The component's name. It should be translated.

`description` Short description of the component and maybe copyright info. This text can contain newlines. It should be translated. Can be left empty.

`version` The version of the component. Can be left empty.

`webAddress` The component's homepage or a relevant link. Start the address with "http://". "http://some.domain" is correct, "some.domain" is not. Can be left empty.

`pathToLicenseFile` Path to the file in the local filesystem containing the license text. The file format has to be plain text in an encoding compatible to the local.

### \[since 6.9\] KAboutData &KAboutData::addCredit(const KAboutPerson &*person*) {#addCredit}

Add a person that deserves credit.

You can call this function as many times as you need. Each entry is appended to a list.

`person` The person.

This function was introduced in Qt 6.9.

### KAboutData &KAboutData::addCredit(const QString &*name*, const QString &*task* = QString(), const QString &*emailAddress* = QString(), const QString &*webAddress* = QString(), const QUrl &*avatarUrl* = QUrl()) {#addCredit-1}

Defines a person that deserves credit.

You can call this function as many times as you need. Each entry is appended to a list.

`name` The person's name. It should be translated.

`task` What the person has done to deserve the honor. The text can contain newlines. It should be translated. Can be left empty.

`emailAddress` An email address when the person can be reached. Can be left empty.

`webAddress` The person's homepage or a relevant link. Start the address with "http://". "http://some.domain" is is correct, "some.domain" is not. Can be left empty.

`avatarUrl` URL to the avatar of the person

### \[since 6.0\] KAboutData &KAboutData::addCredit(const QString &*name*, const QString &*task*, const QString &*emailAddress*, const QString &*webAddress*, const QString &*kdeStoreUsername*) {#addCredit-2}

This is an overloaded function.

This function was introduced in Qt 6.0.

### \[since 6.26\] KAboutData &KAboutData::addLicense(KAboutLicense &&*license*) {#addLicense}

Adds a license.

`license` a license object, obtained e.g. via [KAboutLicense::byKeyword](kaboutlicense.md#byKeyword)().

This function was introduced in Qt 6.26.

*See also* [addLicenseText](kaboutdata.md#addLicenseText), [setLicense](kaboutdata.md#setLicense), [setLicenseText](kaboutdata.md#setLicenseText), [setLicenseTextFile](kaboutdata.md#setLicenseTextFile)

### KAboutData &KAboutData::addLicense(KAboutLicense::LicenseKey *licenseKey*) {#addLicense-1}

Adds a license identifier.

If there is only one unknown license set, e.g. by using the default parameter in the constructor, that one is replaced.

`licenseKey` the license identifier.

*See also* [setLicenseText](kaboutdata.md#setLicenseText), [addLicenseText](kaboutdata.md#addLicenseText), [addLicenseTextFile](kaboutdata.md#addLicenseTextFile)

### KAboutData &KAboutData::addLicense(KAboutLicense::LicenseKey *licenseKey*, KAboutLicense::VersionRestriction *versionRestriction*) {#addLicense-2}

Adds a license identifier.

If there is only one unknown license set, e.g. by using the default parameter in the constructor, that one is replaced.

`licenseKey` the license identifier.

`versionRestriction` Whether later versions of the license are also allowed. e.g. licensed under "GPL 2.0 or at your option later versions" would be OrLaterVersions.

*See also* [setLicenseText](kaboutdata.md#setLicenseText), [addLicenseText](kaboutdata.md#addLicenseText), [addLicenseTextFile](kaboutdata.md#addLicenseTextFile)

### KAboutData &KAboutData::addLicenseText(const QString &*license*) {#addLicenseText}

Adds a license text, which is translated.

If there is only one unknown license set, e.g. by using the default parameter in the constructor, that one is replaced.

Example:

```cpp
addLicenseText( i18n("This is my license") );
```

`license` The license text.

*See also* [setLicenseText](kaboutdata.md#setLicenseText), [addLicense](kaboutdata.md#addLicense), [addLicenseTextFile](kaboutdata.md#addLicenseTextFile)

### KAboutData &KAboutData::addLicenseTextFile(const QString &*file*) {#addLicenseTextFile}

Adds a license text by pointing to a file where it resides. The file format has to be plain text in an encoding compatible to the locale.

If there is only one unknown license set, e.g. by using the default parameter in the constructor, that one is replaced.

`file` path to the file in the local filesystem containing the license text.

*See also* [addLicenseText](kaboutdata.md#addLicenseText), [addLicense](kaboutdata.md#addLicense), [setLicenseTextFile](kaboutdata.md#setLicenseTextFile)

### \[since 6.26\] KAboutData &KAboutData::addRelease(KAboutRelease &&*release*) {#addRelease}

Adds a release note for this application.

This function was introduced in Qt 6.26.

*See also* [releases](kaboutdata.md#releases)()

### \[static\] KAboutData KAboutData::applicationData() {#applicationData}

Returns the [KAboutData](kaboutdata.md) for the application.

This contains information such as authors, license, etc., provided that [setApplicationData](kaboutdata.md#setApplicationData) has been called before. If not called before, the returned [KAboutData](kaboutdata.md) will be initialized from the equivalent properties of [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html) (and its subclasses), if an instance of that already exists. For the list of such properties see [setApplicationData](kaboutdata.md#setApplicationData) (before 5.22: limited to [QCoreApplication::applicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop)).

*See also* [setApplicationData](kaboutdata.md#setApplicationData)

### QList\<KAboutPerson\> KAboutData::authors() const {#authors}

Returns a list of authors.

> **Note:** Getter function for property [authors](kaboutdata.md#authors-prop).

### QString KAboutData::bugAddress() const {#bugAddress}

Returns the email address or URL for bugs.

> **Note:** Getter function for property [bugAddress](kaboutdata.md#bugAddress-prop).

*See also* [setBugAddress](kaboutdata.md#setBugAddress)()

### QString KAboutData::componentName() const {#componentName}

Returns the application's internal name.

> **Note:** Getter function for property [componentName](kaboutdata.md#componentName-prop).

*See also* [setComponentName](kaboutdata.md#setComponentName)()

### QList\<KAboutComponent\> KAboutData::components() const {#components}

Returns a list of components.

> **Note:** Getter function for property [components](kaboutdata.md#components-prop).

### QString KAboutData::copyrightStatement() const {#copyrightStatement}

Returns the copyright statement.

> **Note:** Getter function for property [copyrightStatement](kaboutdata.md#copyrightStatement-prop).

*See also* [setCopyrightStatement](kaboutdata.md#setCopyrightStatement)()

### QList\<KAboutPerson\> KAboutData::credits() const {#credits}

Returns a list of persons who contributed.

> **Note:** Getter function for property [credits](kaboutdata.md#credits-prop).

### QString KAboutData::customAuthorPlainText() const {#customAuthorPlainText}

Returns the plain text displayed around the list of authors instead of the default message telling users to send bug reports to [bugAddress](kaboutdata.md#bugAddress)().

### QString KAboutData::customAuthorRichText() const {#customAuthorRichText}

Returns the rich text displayed around the list of authors instead of the default message telling users to send bug reports to [bugAddress](kaboutdata.md#bugAddress)().

### bool KAboutData::customAuthorTextEnabled() const {#customAuthorTextEnabled}

Returns whether custom text should be displayed around the list of authors.

### QString KAboutData::desktopFileName() const {#desktopFileName}

Returns the desktop file name of this application (e.g. "org.kde.foo")

> **Note:** Getter function for property [desktopFileName](kaboutdata.md#desktopFileName-prop).

*See also* [setDesktopFileName](kaboutdata.md#setDesktopFileName)(const QString&)

### QString KAboutData::displayName() const {#displayName}

Returns the translated program name.

> **Note:** Getter function for property [displayName](kaboutdata.md#displayName-prop).

*See also* [setDisplayName](kaboutdata.md#setDisplayName)()

### \[static, since 6.26\] KAboutData KAboutData::fromAppStreamFile(const QString &*appStreamFileName*) {#fromAppStreamFile}

Create about data from an AppStream file.

This fills all fields of the returned [KAboutData](kaboutdata.md) object that can be found in the the given AppStream file, including (translated) name, license, URLs, etc. Note that most importantly the version number is not included in this.

`appStreamFileName` A path to the AppStream file to read.

This function was introduced in Qt 6.26.

*See also* [fromAppStreamId](kaboutdata.md#fromAppStreamId), [fromAppStreamForApplication](kaboutdata.md#fromAppStreamForApplication)

### \[static, since 6.26\] KAboutData KAboutData::fromAppStreamForApplication() {#fromAppStreamForApplication}

Create about data from the AppStream file of the current application.

This fills all fields of the returned [KAboutData](kaboutdata.md) object that can be found in the the given AppStream file, including (translated) name, license, URLs, etc. Note that most importantly the version number is not included in this.

QGuiApplication::desktopFileName has to be set prior to calling this.

Properties not provided by AppStream data but set on QGuiApplication are being set as well, in the same way as [KAboutData::applicationData](kaboutdata.md#applicationData)() does (since 6.28).

This function was introduced in Qt 6.26.

*See also* [fromAppStreamFile](kaboutdata.md#fromAppStreamFile), [fromAppStreamId](kaboutdata.md#fromAppStreamId)

### \[static, since 6.26\] KAboutData KAboutData::fromAppStreamId(const QString &*applicationId*) {#fromAppStreamId}

Create about data from an AppStream file.

This fills all fields of the returned [KAboutData](kaboutdata.md) object that can be found in the the given AppStream file, including (translated) name, license, URLs, etc. Note that most importantly the version number is not included in this.

`applicationId` An application identifier used to find the corresponding AppStream file in the default install location.

This function was introduced in Qt 6.26.

*See also* [fromAppStreamFile](kaboutdata.md#fromAppStreamFile), [fromAppStreamForApplication](kaboutdata.md#fromAppStreamForApplication)

### QString KAboutData::homepage() const {#homepage}

Returns the application homepage.

> **Note:** Getter function for property [homepage](kaboutdata.md#homepage-prop).

*See also* [setHomepage](kaboutdata.md#setHomepage)()

### QList\<KAboutLicense\> KAboutData::licenses() const {#licenses}

Returns a list of licenses.

> **Note:** Getter function for property [licenses](kaboutdata.md#licenses-prop).

### QString KAboutData::organizationDomain() const {#organizationDomain}

Returns the domain name of the organization that wrote this application.

*See also* [setOrganizationDomain](kaboutdata.md#setOrganizationDomain)(const QByteArray&)

### QString KAboutData::otherText() const {#otherText}

Returns a translated, free form text.

> **Note:** Getter function for property [otherText](kaboutdata.md#otherText-prop).

*See also* [setOtherText](kaboutdata.md#setOtherText)()

### void KAboutData::processCommandLine(QCommandLineParser \**parser*) {#processCommandLine}

Reads the processed `parser` and sees if any of the arguments are the ones set up from [setupCommandLine](kaboutdata.md#setupCommandLine)().

*See also* [setupCommandLine](kaboutdata.md#setupCommandLine)()

### QString KAboutData::productName() const {#productName}

Returns the application's product name, which will be used in KBugReport dialog. By default it returns [componentName](kaboutdata.md#componentName)(), otherwise the one which is set with [setProductName](kaboutdata.md#setProductName)()

> **Note:** Getter function for property [productName](kaboutdata.md#productName-prop).

*See also* [setProductName](kaboutdata.md#setProductName)()

### QVariant KAboutData::programLogo() const {#programLogo}

Returns the program logo data, or a null image if there is no custom application logo defined.

Because [KAboutData](kaboutdata.md) is a core class it cannot use QImage/QPixmap/QIcon directly, so this is a [QVariant](https://doc.qt.io/qt-6/qvariant.html) containing a QImage/QPixmap/QIcon.

> **Note:** Getter function for property [programLogo](kaboutdata.md#programLogo-prop).

*See also* [setProgramLogo](kaboutdata.md#setProgramLogo)()

### \[since 6.26\] QList\<KAboutRelease\> KAboutData::releases() const {#releases}

Returns all release notes for this application.

> **Note:** Getter function for property [releases](kaboutdata.md#releases-prop).

This function was introduced in Qt 6.26.

*See also* [addRelease](kaboutdata.md#addRelease)()

### \[static\] void KAboutData::setApplicationData(const KAboutData &*aboutData*) {#setApplicationData}

Sets the application data for this application.

In addition to changing the result of [applicationData](kaboutdata.md#applicationData), this initializes the equivalent properties of [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html) (and its subclasses) with information from `aboutData`, if an instance of that already exists. Those properties are:

- [QCoreApplication::applicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop)
- [QCoreApplication::applicationVersion](https://doc.qt.io/qt-6/qcoreapplication.html#applicationVersion-prop)
- [QCoreApplication::organizationDomain](https://doc.qt.io/qt-6/qcoreapplication.html#organizationDomain-prop)
- QGuiApplication::applicationDisplayName
- QGuiApplication::desktopFileName (since 5.16)

*See also* [applicationData](kaboutdata.md#applicationData)

### KAboutData &KAboutData::setBugAddress(const QByteArray &*bugAddress*) {#setBugAddress}

Defines the address where bug reports should be sent.

`bugAddress` The bug report email address or URL. This defaults to the kde.org bug system.

*See also* [bugAddress](kaboutdata.md#bugAddress)()

### KAboutData &KAboutData::setComponentName(const QString &*componentName*) {#setComponentName}

Defines the component name used internally.

`componentName` the application or plugin name. Example: "kate".

*See also* [componentName](kaboutdata.md#componentName)()

### KAboutData &KAboutData::setCopyrightStatement(const QString &*copyrightStatement*) {#setCopyrightStatement}

Defines the copyright statement to show when displaying the license.

`copyrightStatement` a copyright statement, that can look like this: i18n("Copyright (C) 1999-2000 Name"). The string specified here is taken verbatim; the author information from [addAuthor](kaboutdata.md#addAuthor) is not used.

*See also* [copyrightStatement](kaboutdata.md#copyrightStatement)()

### KAboutData &KAboutData::setCustomAuthorText(const QString &*plainText*, const QString &*richText*) {#setCustomAuthorText}

Sets the custom text displayed around the list of authors instead of the default message telling users to send bug reports to [bugAddress](kaboutdata.md#bugAddress)().

`plainText` the plain text.

`richText` the rich text.

Setting both to parameters to QString() will cause no message to be displayed at all. Call [unsetCustomAuthorText](kaboutdata.md#unsetCustomAuthorText)() to revert to the default message.

### KAboutData &KAboutData::setDesktopFileName(const QString &*desktopFileName*) {#setDesktopFileName}

Sets the base name of the desktop entry for this application.

This is the file name, without the full path and without extension, of the desktop entry that represents this application according to the freedesktop desktop entry specification (e.g. "org.kde.foo").

A default desktop file name is constructed when the [KAboutData](kaboutdata.md) object is created, using the reverse domain name of the [organizationDomain](kaboutdata.md#organizationDomain) and the [componentName](kaboutdata.md#componentName) as they are at the time of the [KAboutData](kaboutdata.md) object creation. Call this method to override that default name. Typically this is done when also [setOrganizationDomain](kaboutdata.md#setOrganizationDomain) or [setComponentName](kaboutdata.md#setComponentName) need to be called to override the initial values.

The desktop file name can also be passed to the application at runtime through the `desktopfile` command line option which is added by [setupCommandLine](kaboutdata.md#setupCommandLine). This is useful if an application supports multiple desktop files with different runtime settings.

`desktopFileName` the desktop file name of this application

*See also* [desktopFileName](kaboutdata.md#desktopFileName)(), [organizationDomain](kaboutdata.md#organizationDomain)(), [componentName](kaboutdata.md#componentName)(), [setupCommandLine](kaboutdata.md#setupCommandLine)()

### KAboutData &KAboutData::setDisplayName(const QString &*displayName*) {#setDisplayName}

Defines the displayable component name string.

`displayName` the display name. This string should be translated. Example: i18n("Advanced Text Editor").

*See also* [displayName](kaboutdata.md#displayName)()

### KAboutData &KAboutData::setHomepage(const QString &*homepage*) {#setHomepage}

Defines the program homepage.

`homepage` the program homepage string. Start the address with "http://". "http://kate.kde.org" is correct but "kate.kde.org" is not.

*See also* [homepage](kaboutdata.md#homepage)()

### \[since 6.26\] KAboutData &KAboutData::setLicense(KAboutLicense &&*license*) {#setLicense}

Sets the license.

`license` a license object, obtained e.g. via [KAboutLicense::byKeyword](kaboutlicense.md#byKeyword)().

This function was introduced in Qt 6.26.

*See also* [addLicense](kaboutdata.md#addLicense), [addLicenseText](kaboutdata.md#addLicenseText), [setLicenseText](kaboutdata.md#setLicenseText), [setLicenseTextFile](kaboutdata.md#setLicenseTextFile)

### KAboutData &KAboutData::setLicense(KAboutLicense::LicenseKey *licenseKey*) {#setLicense-1}

Defines the license identifier.

`licenseKey` the license identifier.

*See also* [addLicenseText](kaboutdata.md#addLicenseText), [setLicenseText](kaboutdata.md#setLicenseText), [setLicenseTextFile](kaboutdata.md#setLicenseTextFile)

### KAboutData &KAboutData::setLicense(KAboutLicense::LicenseKey *licenseKey*, KAboutLicense::VersionRestriction *versionRestriction*) {#setLicense-2}

Defines the license identifier.

`licenseKey` the license identifier.

`versionRestriction` Whether later versions of the license are also allowed. e.g. licensed under "GPL 2.0 or at your option later versions" would be OrLaterVersions.

*See also* [addLicenseText](kaboutdata.md#addLicenseText), [setLicenseText](kaboutdata.md#setLicenseText), [setLicenseTextFile](kaboutdata.md#setLicenseTextFile)

### KAboutData &KAboutData::setLicenseText(const QString &*license*) {#setLicenseText}

Defines a license text, which is translated.

Example:

```cpp
setLicenseText( i18n("This is my license") );
```

`license` The license text.

### KAboutData &KAboutData::setLicenseTextFile(const QString &*file*) {#setLicenseTextFile}

Defines a license text by pointing to a file where it resides. The file format has to be plain text in an encoding compatible to the locale.

`file` Path to the file in the local filesystem containing the license text.

### KAboutData &KAboutData::setOrganizationDomain(const QByteArray &*domain*) {#setOrganizationDomain}

Defines the domain of the organization that wrote this application. The domain is set to kde.org by default, or the domain of the homePageAddress constructor argument, if set.

Make sure to call setOrganizationDomain(const [QByteArray](https://doc.qt.io/qt-6/qbytearray.html)&) if your product is not developed inside the KDE community.

Used e.g. for the registration to D-Bus done by KDBusService from the KDE Frameworks KDBusAddons module.

Calling this method has no effect on the value of the [desktopFileName](kaboutdata.md#desktopFileName) property.

> **Note:** If your program should work as a D-Bus activatable service, the base name of the D-Bus service description file or of the desktop file you install must match the D-Bus "well-known name" for which the program will register. For example, KDBusService will use a name created from the reversed organization domain with the component name attached, so for an organization domain "bar.org" and a component name "foo" the name of an installed D-Bus service file needs to be "org.bar.foo.service" or the name of the installed desktop file "org.bar.foo.desktop" (and the [desktopFileName](kaboutdata.md#desktopFileName) property accordingly set to "org.bar.foo").

`domain` the domain name, for instance kde.org, koffice.org, etc.

*See also* [organizationDomain](kaboutdata.md#organizationDomain)(), [setDesktopFileName](kaboutdata.md#setDesktopFileName)(const QString&)

### KAboutData &KAboutData::setOtherText(const QString &*otherText*) {#setOtherText}

Defines the additional text to show in the about dialog.

`otherText` some free form text, that can contain any kind of information. The text can contain newlines. This string should be translated.

*See also* [otherText](kaboutdata.md#otherText)()

### KAboutData &KAboutData::setProductName(const QByteArray &*name*) {#setProductName}

Defines the product name which will be used in the KBugReport dialog. By default it's the [componentName](kaboutdata.md#componentName), but you can overwrite it here to provide support for special components e.g. in the form 'product/component', such as 'kontact/summary'.

`name` the name of product

*See also* [productName](kaboutdata.md#productName)()

### KAboutData &KAboutData::setProgramLogo(const QVariant &*image*) {#setProgramLogo}

Defines the program logo.

Use this if you need to have an application logo in [AboutData](../kcoreaddonsqml/qml-org-kde-coreaddons-aboutdata.md) other than the application icon.

Because [KAboutData](kaboutdata.md) is a core class it cannot use QImage/QPixmap/QIcon directly, so this is a [QVariant](https://doc.qt.io/qt-6/qvariant.html) that should contain a QImage/QPixmap/QIcon.

QIcon should be preferred, to be able to properly handle HiDPI scaling. If a QIcon is provided, it will be used at a typical size of 48x48.

`image` logo image.

*See also* [programLogo](kaboutdata.md#programLogo)()

### KAboutData &KAboutData::setShortDescription(const QString &*shortDescription*) {#setShortDescription}

Defines a short description of what the program does.

`shortDescription` the program description. This string should be translated. Example: i18n("An advanced text editor with syntax highlighting support.").

*See also* [shortDescription](kaboutdata.md#shortDescription)()

### KAboutData &KAboutData::setTranslator(const QString &*name*, const QString &*emailAddress*) {#setTranslator}

Sets the name(s) of the translator(s) of the GUI.

The canonical use with the ki18n framework is:

```cpp
setTranslator(i18nc("NAME OF TRANSLATORS", "Your names"),
              i18nc("EMAIL OF TRANSLATORS", "Your emails"));
```

If you are using a KMainWindow this is done for you automatically.

The name and emailAddress are treated as lists separated with ",".

If the strings are empty or "Your names"/"Your emails" respectively they will be ignored.

`name` the name(s) of the translator(s)

`emailAddress` the email address(es) of the translator(s)

### \[since 6.29\] KAboutData &KAboutData::setUrl(KAboutData::UrlType *type*, const QString &*url*) {#setUrl}

Sets the URL of the given type.

This function was introduced in Qt 6.29.

*See also* [url](kaboutdata.md#url)()

### KAboutData &KAboutData::setVersion(const QByteArray &*version*) {#setVersion}

Defines the program version string.

`version` the program version.

*See also* [version](kaboutdata.md#version)()

### bool KAboutData::setupCommandLine(QCommandLineParser \**parser*) {#setupCommandLine}

Configures the `parser` command line parser to provide an authors entry with information about the developers of the application and an entry specifying the license.

Additionally, it will set the description to the command line parser, will add the help option and if the QApplication has a version set (e.g. via [KAboutData::setApplicationData](kaboutdata.md#setApplicationData)) it will also add the version option.

Since 5.16 it also adds an option to set the desktop file name.

Returns true if adding the options was successful; otherwise returns false.

*See also* [processCommandLine](kaboutdata.md#processCommandLine)

### QString KAboutData::shortDescription() const {#shortDescription}

Returns a short, translated description.

> **Note:** Getter function for property [shortDescription](kaboutdata.md#shortDescription-prop).

*See also* [setShortDescription](kaboutdata.md#setShortDescription)()

### QList\<KAboutPerson\> KAboutData::translators() const {#translators}

Returns a list of translators.

> **Note:** Getter function for property [translators](kaboutdata.md#translators-prop).

### KAboutData &KAboutData::unsetCustomAuthorText() {#unsetCustomAuthorText}

Clears any custom text displayed around the list of authors and falls back to the default message telling users to send bug reports to [bugAddress](kaboutdata.md#bugAddress)().

### \[invokable, since 6.29\] QString KAboutData::url(KAboutData::UrlType *type*) const {#url}

Returns the URL of the given type, if available. This is typically populated from AppStream application metadata.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

This function was introduced in Qt 6.29.

*See also* [setUrl](kaboutdata.md#setUrl)()

### QString KAboutData::version() const {#version}

Returns the program's version.

> **Note:** Getter function for property [version](kaboutdata.md#version-prop).

*See also* [setVersion](kaboutdata.md#setVersion)()
